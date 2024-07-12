<template>
    <div class="dashboard">
        <sidebar
          :tab-no="tabNo"
          :change-tab="changeTab"
        > </sidebar>

        <div class="main">
            <navbar :user="user"></navbar>

            <dashboard-content 
              :user="user"
              v-if="tabNo == 0"
              ></dashboard-content>

            <events-content
              :user="user"
              v-if="tabNo == 1"
              :edit-user="editUser"
            ></events-content>
        </div>
    </div>
</template>
<script>
import Sidebar from "./Sidebar.vue";
import Navbar from "./Navbar.vue";
import DashboardContent from "./DashboardContent.vue";
import EventsContent from "./EventContent.vue"

export default {
    components: { Sidebar, Navbar, DashboardContent, EventsContent },
    props: ["user", "editUser"],
    data() {
      return {
        tabNo: 1
      }
    },
    methods: {
      changeTab(number) {
        this.tabNo = number
      }
    }
};
</script>
