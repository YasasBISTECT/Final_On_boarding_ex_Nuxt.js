<template>
  <div class="container">
    <div>
      <form @sumbit.stop.prevent="submitForm">
        <br />
        <h1>Shipping Address</h1>
        <br />
        <b-form-group
          id="address_1-input-group-4"
          label="Street Address*"
          label-for="address_1-input-4"
        >
          <b-form-input
            id="address_1-input-4"
            name="address_1-input-4"
            placeholder="Street Address"
            v-model="$v.form.streetAddress1.$model"
            :state="validateState('streetAddress1')"
            aria-describedby="address_1-input-5-live-feedback"
          ></b-form-input>

          <b-form-invalid-feedback id="address_1-input-5-live-feedback"
            >This is a required field.</b-form-invalid-feedback
          >
        </b-form-group>

        <!-- address 2 -->

        <b-form-group
          id="address_2-input-group-5"
          label="Street Address 2"
          label-for="address_2-input-5"
        >
          <b-form-input
            id="address_2-input-5"
            name="address_2-input-5"
            placeholder="Street Address 2"
            v-model="$v.form.streetAddress2.$model"
            aria-describedby="address_2-input-5-live-feedback"
          ></b-form-input>
        </b-form-group>

        <!-- city -->
        <b-form-group
          id="city-input-group-6"
          label="City*"
          label-for="city-input-6"
        >
          <b-form-input
            id="city-input-6"
            name="city-input-6"
            v-model="$v.form.city.$model"
            :state="validateState('city')"
            placeholder="City"
            aria-describedby="city-input-6-live-feedback"
          ></b-form-input>

          <b-form-invalid-feedback id="city-input-6-live-feedback"
            >This is a required field.</b-form-invalid-feedback
          >
        </b-form-group>

        <!-- district -->
        <b-form-group
          id="district-input-group-7"
          label="District*"
          label-for="district-input-7"
        >
          <b-form-select
            id="district-input-7"
            name="district-input-7"
            v-model="$v.form.district.$model"
            :options="district"
            :state="validateState('district')"
            aria-describedby="district-input-7-live-feedback"
          ></b-form-select>

          <b-form-invalid-feedback id="district-input-7-live-feedback"
            >This is a required field.</b-form-invalid-feedback
          >
        </b-form-group>

        <b-form-group
          id="address_2-input-group-5"
          label="Specific Registration Request"
          label-for="address_2-input-5"
        >
          <b-form-textarea
            id="address_2-input-5"
            name="address_2-input-5"
            max-rows="10"
            v-model="$v.form.specificRegistrationRequest.$model"
          ></b-form-textarea>
        </b-form-group>

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
          <!-- <button class="btn btn-primary" @click="submitForm()">Submit</button> -->
          <b-button class="ml-2" @click="previous()">Previous</b-button>
          <b-button class="ml-2" variant="warning" @click="resetFormTab1()"
            >Cancel</b-button
          >
          <b-button
            class="ml-2"
            variant="primary"
            @click="nextClickValidateTab1()"
            >Submit</b-button
          >

          <!-- <b-button class="ml-2" @click="hello()">test</b-button> -->
        </div>

        <!-- <div class="form-group">
          <button class="btn btn-primary" @click="submitForm()">Submit</button>
        </div> -->
      </form>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import { validationMixin } from "vuelidate";
import { required, minLength } from "vuelidate/lib/validators";
export default {
  name: "nuxt_Universal01",
  mixins: [validationMixin],
  data() {
    return {
      selected: "true",
      district: [
        { value: null, text: "District" },
        { value: "gampaha", text: "Gampaha" },
        { value: "colombo", text: "Colombo" },
        { value: "kaluthara", text: "Kaluthara" },
        { value: "galle", text: "Galle" },
      ],
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

  validations: {
    form: {
      streetAddress1: { required },
      streetAddress2: {},
      city: { required },
      district: { required },
      specificRegistrationRequest: {},
    },
  },

  methods: {
    validateState(name) {
      const { $dirty, $error } = this.$v.form[name];
      return $dirty ? !$error : null;
    },

    resetFormTab1() {
      this.form = {
        contactPerson: null,
        businessName: null,
        contactNum_country: null,
        contactNumber: null,
        streetAddress1: null,
        streetAddress2: null,
        city: null,
        district: null,
        email: null,
        stratDate: null,
      };
      this.$nextTick(() => {
        this.$v.$reset();
      });
    },

    previous() {
      this.$router.push("/BillingAddress");
    },

    nextClickValidateTab1() {
      this.$v.form.$touch();
      if (this.$v.form.$anyError) {
        return;
      }
      this.submitForm();
      console.log("next butoon press");
      //   this.$router.push("/ShippingAddress");
      //   this.$router.push("/HomePage");
    },

    submitForm() {
      console.log("*submit form");
      axios
        .post("http://localhost:52208/api/ShippingAddress", this.form)
        .then((res) => {
          //Perform Success Action
          alert("Done");
          this.$router.push("/HomePage");
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
