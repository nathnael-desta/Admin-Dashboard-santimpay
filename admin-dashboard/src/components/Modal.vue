<template>
    <div
        class="modal"
        :class="{ notVisible: !modalOn }"
    >
        <div class="container">
            <div class="top">
                <div class="text">Create New Event</div>
                <img
                    @click="hideModal"
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
export default {
    props: ["modalOn", "hideModal"],
    data() {
        return {
          eventDetails: {
            eventName: '',
            contactName: '',
            phoneNumeer: '',
            maxTickets: '',
            location: '',
            expireDate: '',
            description: '',
            
          }
        };
    },
    methods: {},
};
</script>
