<template>
    <div class="event-content">
        <div class="top">
            <div class="title">Tickets</div>
        </div>
        <div class="middle">
            <div class="total">
                <div class="top-ticket">
                    <svg
                        width="24"
                        height="24"
                        viewBox="0 0 24 24"
                        fill="none"
                        xmlns="http://www.w3.org/2000/svg"
                    >
                        <path
                            d="M19.5 12.5C19.5 11.12 20.62 10 22 10V9C22 5 21 4 17 4H7C3 4 2 5 2 9V9.5C3.38 9.5 4.5 10.62 4.5 12C4.5 13.38 3.38 14.5 2 14.5V15C2 19 3 20 7 20H17C21 20 22 19 22 15C20.62 15 19.5 13.88 19.5 12.5Z"
                            stroke="#171625"
                            stroke-width="1.5"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                        />
                        <path
                            d="M10 4L10 20"
                            stroke="#171625"
                            stroke-width="1.5"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            stroke-dasharray="5 5"
                        />
                    </svg>
                    <div class="title">Total Tickets</div>
                </div>
                <div class="bottom">{{ user.totalEvents }}</div>
            </div>
            <div class="active">
                <div class="top-ticket">
                    <svg
                        width="24"
                        height="24"
                        viewBox="0 0 24 24"
                        fill="none"
                        xmlns="http://www.w3.org/2000/svg"
                    >
                        <path
                            d="M19.5 12.5C19.5 11.12 20.62 10 22 10V9C22 5 21 4 17 4H7C3 4 2 5 2 9V9.5C3.38 9.5 4.5 10.62 4.5 12C4.5 13.38 3.38 14.5 2 14.5V15C2 19 3 20 7 20H17C21 20 22 19 22 15C20.62 15 19.5 13.88 19.5 12.5Z"
                            stroke="#171625"
                            stroke-width="1.5"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                        />
                        <path
                            d="M10 4L10 20"
                            stroke="#171625"
                            stroke-width="1.5"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            stroke-dasharray="5 5"
                        />
                    </svg>
                    <div class="title">Active Tickets</div>
                </div>
                <div class="bottom">{{ user.eventsActive }}</div>
            </div>
            <div class="expired">
                <div class="top-ticket">
                    <svg
                        width="24"
                        height="24"
                        viewBox="0 0 24 24"
                        fill="none"
                        xmlns="http://www.w3.org/2000/svg"
                    >
                        <path
                            d="M19.5 12.5C19.5 11.12 20.62 10 22 10V9C22 5 21 4 17 4H7C3 4 2 5 2 9V9.5C3.38 9.5 4.5 10.62 4.5 12C4.5 13.38 3.38 14.5 2 14.5V15C2 19 3 20 7 20H17C21 20 22 19 22 15C20.62 15 19.5 13.88 19.5 12.5Z"
                            stroke="#171625"
                            stroke-width="1.5"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                        />
                        <path
                            d="M10 4L10 20"
                            stroke="#171625"
                            stroke-width="1.5"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            stroke-dasharray="5 5"
                        />
                    </svg>
                    <div class="title">Expired Tickets</div>
                </div>
                <div class="bottom">{{ user.eventsInactive }}</div>
            </div>
        </div>
        <div class="bottom">
            <div class="title">All Tickets</div>
            <div class="table">
                <table class="table-container">
                    <tr class="columns">
                        <th>Ticket ID</th>
                        <th>Ticket Name</th>
                        <th>Phone Number</th>
                        <th>Number Of Tickets</th>
                        <th class="ticketStatus">Status</th>
                    </tr>
                    <tr v-for="(ticket, index) in user.allTickets2">
                        <td
                            v-if="index >= pageNo * 5 && index < pageNo * 5 + 5"
                        >
                            {{ ticket.ticketID }}
                        </td>
                        <td
                            v-if="index >= pageNo * 5 && index < pageNo * 5 + 5"
                        >
                            {{ ticket.ticketName }}
                        </td>
                        <td
                            v-if="index >= pageNo * 5 && index < pageNo * 5 + 5"
                        >
                            {{ ticket.phoneNumber }}
                        </td>
                        <td
                            v-if="index >= pageNo * 5 && index < pageNo * 5 + 5"
                        >
                            {{ ticket.noOfTickets }}
                        </td>
                        <td
                            v-if="index >= pageNo * 5 && index < pageNo * 5 + 5" 
                        >
                            <span
                                class="statusactive"
                                :class="{
                                    statusactive: ticket.status == 'active',
                                    statusexpired: ticket.status == 'expired',
                                }"
                                >{{ ticket.status }}</span
                            >
                        </td>
                    </tr>
                </table>
                <div class="pages">
                    <div class="left">
                        <div class="showing">Showing Page</div>
                        <div class="page-number">{{ pageNo + 1 }}</div>
                        <div class="out-of">
                            Out of {{ totalNumberOfPages + 1 }}
                        </div>
                    </div>
                    <div class="right">
                        <div
                            @click="decrease"
                            class="arrow-container"
                        >
                            <img
                                src="../../public/assets/newarrowLeft.svg"
                                alt=""
                                class="arrow"
                            />
                        </div>
                        <div
                            class="pageNos"
                            v-for="(page, index) in navArray"
                        >
                            <div
                                class="page"
                                @click="changePageNo(index)"
                                :class="{ selected: pageNo == index }"
                            >
                                {{ `${index + 1}` }}
                            </div>
                        </div>

                        <div
                            class="arrow-container"
                            @click="increase"
                        >
                            <img
                                src="../../public/assets/newarrowRight.svg"
                                alt=""
                            />
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <modal
        :modal-on="modalOn"
        :hide-modal="hideModal"
        :add-event="addEvent"
    ></modal>
</template>

<script>
import { useAttrs } from "vue";
import Modal from "./Modal.vue";

export default {
    components: {
        Modal,
    },
    props: ["user", "editUser", "addEvent"],
    data() {
        return {
            clickedOptions: NaN,
            pageNo: 0,
            modalOn: false,
            editOn: false,
            edit: {
                eventName: "",
                contactName: "",
                phoneNumber: "",
                maxTickets: "",
                description: "",
                location: "",
                status: "",
            },
        };
    },
    computed: {
        totalNumberOfPages() {
            return Math.floor((this.user.allTickets.length - 1) / 5);
        },
        notFilled() {
            return (
                !this.edit.eventName ||
                !this.edit.contactName ||
                !this.edit.phoneNumber ||
                !this.edit.maxTickets ||
                !this.edit.description ||
                !this.edit.location ||
                !this.edit.status
            );
        },
        navArray() {
            let arr = [];
            for (let i = 0; i < this.totalNumberOfPages + 1; i++) {
                arr.push(i);
            }
            return arr;
        },
    },
    methods: {
        clickOptions(no) {
            if (this.clickedOptions == no) {
                this.clickedOptions = 6;
            } else {
                this.clickedOptions = no;
            }
        },
        changePageNo(no) {
            this.pageNo = no;
        },
        decrease() {
            if (this.pageNo > 0) {
                this.pageNo -= 1;
            }
        },
        increase() {
            if (this.pageNo < this.totalNumberOfPages) {
                this.pageNo += 1;
            }
        },
        makeEdit(index) {
            if (!this.notFilled) {
                this.editUser(index, "edit", {
                    eventName: this.edit.eventName,
                    contactName: this.edit.contactName,
                    phoneNumber: this.edit.phoneNumber,
                    maxTickets: this.edit.maxTickets,
                    description: this.edit.description,
                    location: this.edit.location,
                    status: this.edit.status,
                });

                this.editOn = false;
            }
        },
        showModal() {
            this.modalOn = true;
        },
        hideModal() {
            this.modalOn = false;
        },
        turnEditOn() {
            this.editOn = true;
        },
        hideEditModal() {
            this.editOn = false;
        },
    },
};
</script>
