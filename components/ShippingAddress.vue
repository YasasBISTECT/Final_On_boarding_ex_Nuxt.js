<template>
  <div class="container">
    <div>
      <form v-on:sumbit.prevent="submitForm">
        <div class="form-group">
          <label for="Address 1">Street Address</label>
          <input
            type="text"
            class="form-control"
            id="streetAddress1"
            placeholder="Street Address"
            v-model="form.streetAddress1"
          />
        </div>

        <div class="form-group">
          <label for="Address 2">Street Address 2</label>
          <input
            type="text"
            class="form-control"
            id="streetAddress2"
            placeholder="Street Address 2"
            v-model="form.streetAddress2"
          />
        </div>

        <div class="form-group">
          <label for="city">City</label>
          <input
            type="text"
            class="form-control"
            id="city"
            placeholder="city"
            v-model="form.city"
          />
        </div>

        <div class="form-group">
          <label for="district">District</label>
          <input
            type="text"
            class="form-control"
            id="district"
            placeholder="District"
            v-model="form.district"
          />
        </div>

        <div class="form-group">
          <label for="district">Specific Registration Request</label>
          <input
            type="text"
            class="form-control"
            id="district"
            placeholder="Specific Registration Request"
            v-model="form.specificRegistrationRequest"
          />
        </div>

        <div class="form-group">
          <b-form-group
            label="Would you like to receive our monthly e-mail?"
            v-slot="{ ariaDescribedby }"
          >
            <b-form-radio
              v-model="selected"
              :aria-describedby="ariaDescribedby"
              name="some-radios"
              value="true"
              >Yes</b-form-radio
            >
            <b-form-radio
              v-model="selected"
              :aria-describedby="ariaDescribedby"
              name="some-radios"
              value="false"
              >No</b-form-radio
            >
          </b-form-group>
        </div>

        <div class="form-group">
          <button class="btn btn-primary" @click="submitForm()">Submit</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "nuxt_Universal01",
  data() {
    return {
      selected: "true",
      form: {
        // contactPerson: null,
        // businessName: null,
        // contactNumber: null,
        streetAddress1: null,
        streetAddress2: null,
        city: null,
        district: null,
        specificRegistrationRequest: null,
        email: true,
        // email: null,
        // stratDate: null,
      },
    };
  },

  methods: {
    submitForm() {
      // console.log("*button click");
      axios
        .post("http://localhost:52208/api/ShippingAddress", this.form)
        .then((res) => {
          //Perform Success Action
        })
        .catch((error) => {
          // error.response.status Check status code
        })
        .finally(() => {
          //Perform action in always
        });
      // console.log("*button click");
    },
  },
};
</script>

<style>
</style>
