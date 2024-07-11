<template v-if="users">
    <login-page
      :current-input="currentInput" 
      :check-user= "checkUser"
      v-if="pageNo == 0"
    ></login-page>
    <dashboard
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
            userIndex: NaN,
            pageNo: 0
        };
    },
    created() {
      this.getPages();
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
        }
    },
};
</script>
