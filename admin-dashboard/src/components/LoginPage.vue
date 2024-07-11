<template>
    <div class="login-page">
        <div class="left">
            <div class="logo">
                Santim<span class="highlighted">Events</span>
            </div>
            <div class="img-container">
                <img
                    src="../../public/assets/9233781_4111605 1.svg"
                    alt="image of an event"
                />
            </div>
            <div class="call">Mangage Santim Events Professionally!</div>
        </div>
        <div class="right">
            <form class="login-cutout">
                <div class="top-text">
                    <div class="login">Login</div>
                    <div class="authorized">For Authorized Personel Only</div>
                </div>

                <div class="inputs">
                    <div class="email input">
                        <label for="email-input">Email or Phone Number</label>
                        <input
                            type="text"
                            id="email-input"
                            placeholder="example@example.com"
                            v-model="accountName"
                        />
                    </div>

                    <div class="password input">
                        <label for="password-input">Password</label>
                        <input
                            :type="type"
                            id="password-input"
                            placeholder="......."
                            class="password-input"
                            v-model="accountPassword"
                        />
                        <div 
                            class="eye-container"
                             @click="changeEye"
                            >
                            <img
                                :src="chooseEye"
                                alt="hide password"
                            />
                        </div>
                    </div>
                </div>

                <button class="login-button"
                    @click.prevent="checkUser(accountName, accountPassword)"
                >
                    <div>Login</div>
                    <div 
                        class="arrow-container"
                    >
                        <img
                            src="../../public/assets/arrowRight.svg"

                            alt="right arrow"
                        />
                    </div>
                </button>
            </form>
        </div>
    </div>
</template>

<script>
export default {
  props: ["currentInput", "checkUser"],
  data() {
    return {
      accountName: '',
      accountPassword: '',
      eye: 0,
      type:"password"
    }
  },
  computed: {
    chooseEye() {
        if (this.eye == 0) {
            return "./assets/eyeClosed.svg";
        } else {
                    return "./assets/eye.svg"
        }
    }
  },
  methods: {
    changeEye() {
        if (this.eye == 0) {
            this.eye = 1;
            this.type = "text"
        } else {
            this.eye = 0;
            this.type = "password"
        }
    }
  }
};
</script>
