<template>
  <v-app>
    <v-main>
      <v-content>
        <div class="staticHero">
          <v-img :src="img" style="max-height: 350px">
            <v-row align="end" class="lightbox white--text pa-2 fill-height">
              <v-col>
                <v-container>
                  <div class="headline">CONTACT US</div>
                </v-container>
              </v-col>
            </v-row>
          </v-img>
        </div>
        <div class="staticHero">
          <v-img src="../assets/images/contactusimg.jpg">
            <v-row align="end" class="lightbox white--text pa-2 fill-height">
            </v-row>
          </v-img>
        </div>
        <div class="bothfields" display="flex">
          <div class="block">
            <v-container>
              <v-form ref="form" v-model="valid" lazy-validation>
                <v-text-field
                  v-model="name"
                  :counter="10"
                  :rules="nameRules"
                  label="Name"
                  required
                ></v-text-field>
                <v-text-field
                  v-model="email"
                  :rules="emailRules"
                  label="E-mail"
                  required
                ></v-text-field>
                <v-textarea
                  v-model="message"
                  :rules="messageRules"
                  label="Message"
                  required
                ></v-textarea>
                <v-btn
                  :disabled="!valid"
                  color="success"
                  class="mr-4"
                  @click="validate"
                  >Submit</v-btn
                >
                <v-btn color="error" class="mr-4" @click="reset">Reset</v-btn>
              </v-form>
            </v-container>
          </div>
          <div class="googlemap">
            <iframe
              class="map-frame"
              src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d16705.802661855836!2d-0.14290489950731525!3d51.50711704027593!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x47d8a00baf21de75%3A0x52963a5addd52a99!2sLondon!5e0!3m2!1sen!2suk!4v1577041400110!5m2!1sen!2suk"
            ></iframe>
          </div>
        </div>
      </v-content>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "Contact",
  data: () => ({
    valid: true,
    name: "",
    nameRules: [
      (v) => !!v || "Name is required",
      (v) => (v && v.length <= 10) || "Name must be less than 10 characters",
    ],
    email: "",
    emailRules: [
      (v) => !!v || "E-mail is required",
      (v) => /.+@.+\..+/.test(v) || "E-mail must be valid",
    ],
    message: "",
    messageRules: [
      (v) => !!v || "Message is required",
      (v) => (v && v.length >= 10) || "Message must be more than 10 characters",
    ],
  }),
  methods: {
    validate() {
      if (this.$refs.form.validate()) {
        this.snackbar = true;
      }
    },
    reset() {
      this.$refs.form.reset();
    },
  },
};
</script>

<script>
import Image from "../assets/images/contactusimg.jpg";
export default {
  name: "AboutUs",

  data() {
    return {
      img: Image,
      items: [],
    };
  },
};

</script>


<style>

.bothfields {
  display: flex;
  justify-content: center;
  margin: 0;
  height: 100vh;
}

/* Change the background property in .block to prevent it from using background:transparent and inheriting the dark color from parent style */

.bothfields > div {
  min-width: 50%;
}

.map-frame {
  min-width: 100%;
  min-height: 100%;
}

</style>
