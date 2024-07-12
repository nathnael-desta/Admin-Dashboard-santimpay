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
        editUser(index, option, edit) {
          if (option === "delete") {
            this.user.allTickets.splice(index,1);
            return;
          }

          if (option === "edit") {
            this.user.allTickets.splice(index,1,{
        "image": "./assets/image.svg",
        "eventName": edit.eventName,
        "contactName": edit.contactName,
        "phoneNumber": edit.phoneNumber,
        "maxTickets": edit.maxTickets,
        "description": edit.description,
        "location": edit.location,
        "status": edit.status
      });
          }

        }
    },
};
</script>
