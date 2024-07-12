<template>
    <div
        class="modal"
        :class="{ notVisible: !modalOn }"
    >
        <div class="container">
            <div class="top">
                <div class="text">Create New Event</div>
                <img
                    @click="closeModal"
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
                            v-model="eventDetails.eventName"
                        />
                    </div>

                    <div class="contact-name normal">
                        <label for="contact-name-input">Contact Name</label>
                        <input
                            type="text"
                            name=""
                            id="contact-name-input"
                            placeholder="EG. Abebe Bikila"
                            v-model="eventDetails.contactName"
                        />
                    </div>

                    <div class="phone-number normal">
                        <label for="phone-number-input">Phone Number</label>
                        <input
                            type="text"
                            name=""
                            id="phone-number-input"
                            placeholder="+2519 00000000"
                            v-model="eventDetails.phoneNumber"
                        />
                    </div>

                    <div class="max-tickets normal">
                        <label for="max-tickets-input">Max Tickets</label>
                        <input
                            type="text"
                            name=""
                            id="max-tickets-input"
                            placeholder="EG 1000"
                            v-model="eventDetails.maxTickets"
                        />
                    </div>

                    <div class="description">
                        <label for="description-input">Description</label>
                        <textarea
                            name=""
                            id="description-input"
                            placeholder="Write description"
                            v-model="eventDetails.description"
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
                            v-model="eventDetails.location"
                        />
                    </div>

                    <div class="expire-data normal">
                        <label for="expire-date-input">Expiry Date</label>
                        <input
                            type="text"
                            name=""
                            id="expire-date-input"
                            placeholder="Select Date in the format: 8 Jul 2024 "
                            v-model="eventDetails.expireDate"
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
                    <div class="cancel" @click="closeModal">Cancel</div>
                    <div
                        class="create"
                        :class="{ notActive: canNOtSubmit }"
                        @click="submitEvent"
                    >
                        Create
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ["modalOn", "hideModal", "addEvent"],
    data() {
        return {
            eventDetails: {
                eventName: "",
                contactName: "",
                phoneNumber: "",
                maxTickets: "",
                location: "",
                expireDate: "",
                description: "",
            },
        };
    },
    computed: {
        canNOtSubmit() {
            return (
                !this.eventDetails.eventName ||
                !this.eventDetails.contactName ||
                !this.eventDetails.phoneNumber ||
                !this.eventDetails.maxTickets ||
                !this.eventDetails.location ||
                !this.eventDetails.expireDate ||
                !this.eventDetails.description
            );
        },
    },
    methods: {
      submitEvent() {
        if (!this.canNOtSubmit) {
          let expire = "expired"

          if(!isNaN(this.daysUntil(this.eventDetails.expireDate)) && this.eventDetails.expireDate > 0) {
            expire = "active";
          }

          this.addEvent({
            image: "./assets/image.svg",
            eventName: this.eventDetails.eventName,
            contactName: this.eventDetails.contactName,
            phoneNumber: this.eventDetails.phoneNumber,
            maxTickets: this.eventDetails.maxTickets,
            location: this.eventDetails.location,
            status: expire,
            description: this.eventDetails.description,
          })

          this.hideModal();

          this.eventDetails = {
                eventName: "",
                contactName: "",
                phoneNumber: "",
                maxTickets: "",
                location: "",
                expireDate: "",
                description: "",
            }

        }
      },

      daysUntil(targetDate) {
				const currentDate = new Date();

				const target = new Date(targetDate);

				let [day, month, year] = targetDate.split(' ');

				const months = {
					Jan: '01',
					Feb: '02',
					Mar: '03',
					Apr: '04',
					May: '05',
					Jun: '06',
					Jul: '07',
					Aug: '08',
					Sep: '09',
					Oct: '10',
					Nov: '11',
					Dec: '12',
				};

				month = months[month];

				const diffTime = target - currentDate;

				// from milliseconds to days

				const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));

				return diffDays;
			},
      closeModal() {
        this.hideModal();

        this.eventDetails ={
                eventName: "",
                contactName: "",
                phoneNumber: "",
                maxTickets: "",
                location: "",
                expireDate: "",
                description: "",
            }
      }
    },
};
</script>
