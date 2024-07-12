<template>
    <div class="event-content">
        <div class="top">
            <div class="title">Events</div>
            <div class="create-button">
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
            <div class="title">All Tickets</div>
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
                        <td v-if="index >= pageNo && index < pageNo + 5">
                            <img
                                :src="`${ticket.image}`"
                                alt=""
                            />
                        </td>
                        <td v-if="index >= pageNo && index < pageNo + 5">
                            {{ ticket.eventName }}
                        </td>
                        <td v-if="index >= pageNo && index < pageNo + 5">
                            {{ ticket.contactName }}
                        </td>
                        <td v-if="index >= pageNo && index < pageNo + 5">
                            {{ ticket.phoneNumber }}
                        </td>
                        <td v-if="index >= pageNo && index < pageNo + 5">
                            {{ ticket.maxTickets }}
                        </td>
                        <td v-if="index >= pageNo && index < pageNo + 5">
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
                        <td v-if="index >= pageNo && index < pageNo + 5">
                            {{ ticket.location }}
                        </td>
                        <td v-if="index >= pageNo && index < pageNo + 5">
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
                            :class="{ notDisplay: index != pageNo || !editOn }"
                        >
                            <div class="edit-container">
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
                            <img
                                src="../../public/assets/newarrowLeft.svg"
                                alt=""
                                class="arrow"
                            />
                        </div>
                        <div
                            class="page"
                            @click="changePageNo(0)"
                            :class="{ selected: pageNo == 0 }"
                        >
                            1
                        </div>
                        <div
                            class="page"
                            @click="changePageNo(1)"
                            :class="{ selected: pageNo == 1 }"
                        >
                            2
                        </div>
                        <div
                            class="page"
                            @click="changePageNo(2)"
                            :class="{ selected: pageNo == 2 }"
                        >
                            3
                        </div>
                        <div
                            class="page"
                            @click="changePageNo(3)"
                            :class="{ selected: pageNo == 3 }"
                        >
                            4
                        </div>
                        <div
                            class="page"
                            :class="{ selected: pageNo == 4 }"
                            @click="changePageNo(4)"
                        >
                            5
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

    <div
        class="modal"
        :class="{ notVisible: !modalOn }"
    >
        <div class="container">
            <div class="top">
                <div class="text">Create New Event</div>
                <img
                    src="../../public/assets/close.svg"
                    alt=""
                />
            </div>
            <div class="middle">
                <div class="left">
                    <div class="event-name normal">
                        <label for="event-name-input">Event Name</label>
                        <input
                            type="text"
                            name=""
                            id="event-name-input"
                            placeholder="EG. Bezar Event"
                        />
                    </div>

                    <div class="contact-name normal">
                        <label for="contact-name-input">Contact Name</label>
                        <input
                            type="text"
                            name=""
                            id="contact-name-input"
                            placeholder="EG. Abebe Bikila"
                        />
                    </div>

                    <div class="phone-number normal">
                        <label for="phone-number-input">Phone Number</label>
                        <input
                            type="text"
                            name=""
                            id="phone-number-input"
                            placeholder="+2519 00000000"
                        />
                    </div>

                    <div class="max-tickets normal">
                        <label for="max-tickets-input">Max Tickets</label>
                        <input
                            type="text"
                            name=""
                            id="max-tickets-input"
                            placeholder="EG 1000"
                        />
                    </div>

                    <div class="description">
                        <label for="description-input">Description</label>
                        <textarea
                            name=""
                            id="description-input"
                            placeholder="Write description"
                        ></textarea>
                    </div>
                </div>
                <div class="right">
                    <div class="location normal">
                        <label for="location-input">Event Name</label>
                        <input
                            type="text"
                            name=""
                            id="location-input"
                            placeholder="Eg Millennium Hall"
                        />
                    </div>

                    <div class="expire-data normal">
                        <label for="expire-date-input">Expiry Date</label>
                        <input
                            type="text"
                            name=""
                            id="expire-date-input"
                            placeholder="Select Date"
                        />
                    </div>

                    <div class="event-image normal">
                        <label for="event-image-input">Event Image</label>
                        <div class="file-container">
                            <div class="inner">
                                <div class="text">Upload File</div>
                                <div class="select">
                                    Select a file or drag and drop here
                                </div>
                            </div>
                        </div>
                        <input
                            type="file"
                            name=""
                            id="event-image-input"
                            placeholder=""
                            hidden
                        />
                    </div>
                </div>
            </div>
            <div class="bottom">
                <div class="buttons">
                    <div class="cancel">Cancel</div>
                    <div class="create">Create</div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import { useAttrs } from "vue";

export default {
    props: ["user", "editUser"],
    data() {
        return {
            clickedOptions: NaN,
            modalOn: false,
            pageNo: 0,
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
            return Math.floor(this.user.allTickets.length / 5);
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
        turnEditOn() {
            this.editOn = true;
        },
    },
};
</script>
