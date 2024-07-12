<template>
    <div class="event-content">
        <div class="top">
            <div class="title">Events</div>
            <div
                class="create-button"
                @click="showModal"
            >
                <img
                    src="../../public/assets/add.svg"
                    alt=""
                />
                <div class="text">Create Event</div>
            </div>
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
            <div class="title">All Events</div>
            <div class="table">
                <table class="table-container">
                    <tr class="columns">
                        <th>Image</th>
                        <th>Event Name</th>
                        <th>Contact Name</th>
                        <th>Phone Number</th>
                        <th>Max Tickets</th>
                        <th>Description</th>
                        <th>Location</th>
                        <th>Status</th>
                    </tr>
                    <tr v-for="(ticket, index) in user.allTickets">
                        <td v-if="index >= (pageNo * 5) && index < ((pageNo * 5) + 5)">
                            <img
                                :src="`${ticket.image}`"
                                alt=""
                            />
                        </td>
                        <td v-if="index >= (pageNo * 5) && index < ((pageNo * 5) + 5)">
                            {{ ticket.eventName }}
                        </td>
                        <td v-if="index >= (pageNo * 5) && index < ((pageNo * 5) + 5)">
                            {{ ticket.contactName }}
                        </td>
                        <td v-if="index >= (pageNo * 5) && index < ((pageNo * 5) + 5)">
                            {{ ticket.phoneNumber }}
                        </td>
                        <td v-if="index >= (pageNo * 5) && index < ((pageNo * 5) + 5)">
                            {{ ticket.maxTickets }}
                        </td>
                        <td v-if="index >= (pageNo * 5) && index < ((pageNo * 5) + 5)">
                            {{ ticket.description.substring(0, 26) }}
                            <span
                                class="more"
                                :class="{
                                    notVisible: !(
                                        ticket.description.length > 26
                                    ),
                                }"
                            >
                                ...<span class="colored">More</span>
                                <span class="popout">
                                    {{ ticket.description }}</span
                                >
                            </span>
                        </td>
                        <td v-if="index >= (pageNo * 5) && index < ((pageNo * 5) + 5)">
                            {{ ticket.location }}
                        </td>
                        <td v-if="index >= (pageNo * 5) && index < ((pageNo * 5) + 5)">
                            <span
                                class="statusactive"
                                :class="{
                                    statusactive: ticket.status == 'active',
                                    statusexpired: ticket.status == 'expired',
                                }"
                                >{{ ticket.status }}</span
                            >
                            <div
                                class="img-container"
                                @click="clickOptions(index)"
                                :class="{ clicked: clickedOptions === index }"
                            >
                                <img
                                    src="../../public/assets/threeDots.svg"
                                    alt=""
                                />
                            </div>
                            <div
                                class="options"
                                :class="{
                                    notVisible: !(clickedOptions === index),
                                }"
                            >
                                <div
                                    class="edit"
                                    @click="turnEditOn"
                                >
                                    <img
                                        src="../../public/assets/edit.svg"
                                        alt=""
                                    />
                                    <div class="text">Edit</div>
                                </div>
                                <div
                                    class="delete"
                                    @click="editUser(index, 'delete')"
                                >
                                    <img
                                        src="../../public/assets/trash.svg"
                                        alt=""
                                    />
                                    <div class="text">Delete</div>
                                </div>
                            </div>
                            <div
                                class="edit-modal"
                                :class="{
                                    notDisplay: index != pageNo || !editOn,
                                }"
                            >
                                <div class="edit-container">
                                    <div class="title">
                                        <div class="text">Edit</div>
                                        <img
                                            @click="hideEditModal"
                                            src="../../public/assets/close.svg"
                                            alt=""
                                        />
                                    </div>

                                    <div class="event-name">
                                        <label for="">Event Name</label>
                                        <input
                                            type="text"
                                            v-model="edit.eventName"
                                        />
                                    </div>
                                    <div class="contact-name">
                                        <label for="">Contact Name</label>
                                        <input
                                            type="text"
                                            v-model="edit.contactName"
                                        />
                                    </div>
                                    <div class="phone-number">
                                        <label for="">Phone Number</label>
                                        <input
                                            type="text"
                                            v-model="edit.phoneNumber"
                                        />
                                    </div>
                                    <div class="max-tickets">
                                        <label for="">Max Tickets</label>
                                        <input
                                            type="text"
                                            v-model="edit.maxTickets"
                                        />
                                    </div>
                                    <div class="description">
                                        <label for="">Description</label>
                                        <input
                                            type="text"
                                            v-model="edit.description"
                                        />
                                    </div>
                                    <div class="location">
                                        <label for="">Location</label>
                                        <input
                                            type="text"
                                            v-model="edit.location"
                                        />
                                    </div>
                                    <div class="status">
                                        <label for="">Status</label>
                                        <input
                                            type="text"
                                            v-model="edit.status"
                                        />
                                    </div>
                                    <div
                                        class="submit"
                                        :class="{ notFully: notFilled }"
                                        @click="makeEdit(index)"
                                    >
                                        Submit
                                    </div>
                                </div>
                            </div>
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
                        <svg class="arrow" width="7" height="12" viewBox="0 0 7 12" fill="none" xmlns="http://www.w3.org/2000/svg">
<path fill-rule="evenodd" clip-rule="evenodd" d="M6.56603 0.558058C6.83216 0.802136 6.83216 1.19786 6.56603 1.44194L2.07812 5.55806C1.812 5.80214 1.812 6.19786 2.07813 6.44194L6.56603 10.5581C6.83216 10.8021 6.83216 11.1979 6.56603 11.4419C6.29991 11.686 5.86844 11.686 5.60231 11.4419L1.1144 7.32583C0.316033 6.59359 0.316031 5.40641 1.1144 4.67418L5.60231 0.558058C5.86844 0.313981 6.29991 0.313981 6.56603 0.558058Z" fill="#171625"/>
</svg>

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
                        <svg width="8" height="12" viewBox="0 0 8 12" fill="none" xmlns="http://www.w3.org/2000/svg">
<path fill-rule="evenodd" clip-rule="evenodd" d="M1.07459 11.4419C0.808469 11.1979 0.808469 10.8021 1.07459 10.5581L5.5625 6.44194C5.82863 6.19786 5.82863 5.80214 5.5625 5.55806L1.07459 1.44194C0.80847 1.19786 0.80847 0.802137 1.07459 0.558058C1.34072 0.313981 1.77219 0.313981 2.03831 0.558058L6.52622 4.67418C7.32459 5.40641 7.32459 6.59359 6.52622 7.32582L2.03831 11.4419C1.77219 11.686 1.34072 11.686 1.07459 11.4419Z" fill="#171625"/>
</svg>

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
