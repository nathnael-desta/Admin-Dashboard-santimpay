<template v-if="users">
    <login-page
      :current-input="currentInput" 
      :check-user= "checkUser"
      v-if="pageNo == 0"
    ></login-page>
    <dashboard
      v-if="user"
      :user="user"
      :edit-user="editUser"
    ></dashboard>
</template>

<script>
import LoginPage from "./components/LoginPage.vue";
import Dashboard from "./components/Dashboard.vue";

export default {
    name: "App",
    components: {
        LoginPage,
        Dashboard
    },
    data() {
        return {
            users: [],
            currentInput: {
              accountName: "",
              accountPassword: ""
            },
            userIndex: 0,
            pageNo: 1
        };
    },
    created() {
      this.getPages();
    },
    computed: {
      user() {
        console.log(this.users[this.userIndex])
        return this.users[this.userIndex];
      }
    },
    methods: {
        async getPages() {
            let res = await fetch("users.json");
            let data = await res.json();

            this.users = data;
        },
        checkUser(name, pass) {
          this.users.forEach((user, index) => {
            let correctInput = false;
            if ((user.email == name || user.phoneNumber == name) && user.password == pass) {
              this.userIndex = index;
              correctInput = true;
            }

            if(!correctInput) {
              alert("incorrect input")
            } else {
              this.pageNo = 1;
            }
          })
        },
        editUser(index, option) {
          if (option === "delete") {
            this.users.splice(index,1);
          }
        }
    },
};
</script>
