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
              :add-event="addEvent"
            ></events-content>

            <tickets-content
              :user="user"
              v-if="tabNo == 2"
              :edit-user="editUser"
              :add-event="addEvent"
            ></tickets-content>

            <location-content
                v-if="tabNo == 3"
            ></location-content>

            <users-content
                v-if="tabNo == 4"
            ></users-content>
        </div>
    </div>
</template>
<script>
import Sidebar from "./Sidebar.vue";
import Navbar from "./Navbar.vue";
import DashboardContent from "./DashboardContent.vue";
import EventsContent from "./EventContent.vue";
import TicketsContent from "./TicketsContent.vue";
import LocationContent from "./LocationContent.vue";
import UsersContent from "./UsersContent.vue"

export default {
    components: { Sidebar, Navbar, DashboardContent, EventsContent, TicketsContent, LocationContent, UsersContent },
    props: ["user", "editUser", "addEvent"],
    data() {
      return {
        tabNo: 2
      }
    },
    methods: {
      changeTab(number) {
        this.tabNo = number
      }
    }
};
</script>
