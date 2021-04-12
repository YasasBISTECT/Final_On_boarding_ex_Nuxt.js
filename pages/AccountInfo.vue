<template>
  <div class="container">
    <div>
      <form @sumbit.stop.prevent="submitForm">
        <br />
        <h1>Account Info</h1>
        <br />
        <b-form-group
          id="personName-input-group-1"
          label="Contact Person*"
          label-for="personName-input-1"
        >
          <b-form-input
            id="personName-input-1"
            name="personName-input-1"
            placeholder="Contact Person Name"
            v-model="$v.form.contactPerson.$model"
            :state="validateState('contactPerson')"
            aria-describedby="personName-input-1-live-feedback"
          ></b-form-input>

          <b-form-invalid-feedback id="personName-input-1-live-feedback"
            >This is a required field and must be at least 3
            characters.</b-form-invalid-feedback
          >
        </b-form-group>

        <!-- business Name -->
        <b-form-group
          id="businessName-input-group-2"
          label="Business Name"
          label-for="businessName-input-2"
        >
          <b-form-input
            id="businessName-input-2"
            name="businessName-input-2"
            placeholder="Business Name"
            v-model="$v.form.businessName.$model"
          ></b-form-input>
        </b-form-group>

        <!-- conatct Number -->
        <b-form-group
          id="contactNumber-input-group-3"
          label="Contact Number"
          label-for="contactNumber-input-3"
        >
          <b-input-group id="input-contactNum" class="mb-2">
            <b-form-input
              id="conNumber_country-input-3"
              name="conNumber_country-input-3"
              v-model="$v.form.contactNum_country.$model"
              class="mr-3"
              label="contactNum_country"
              placeholder="Country Code"
            ></b-form-input>
            <b-form-input
              id="conNumber_telNumber-input-3"
              name="conNumber_telNumber-input-3"
              v-model="$v.form.contactNumber.$model"
              label="Last name"
              placeholder="Phone Number"
            ></b-form-input>
          </b-input-group>
        </b-form-group>

        <!-- address 1 -->

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

        <!-- email -->
        <b-form-group
          id="email-input-group-8"
          label="Email*"
          label-for="email-input-8"
        >
          <b-form-input
            id="email-input-8"
            name="email-input-8"
            type="email"
            v-model="$v.form.email.$model"
            :state="validateState('email')"
            placeholder="Email Address"
            aria-describedby="email-input-8-live-feedback"
          ></b-form-input>

          <b-form-invalid-feedback id="email-input-8-live-feedback"
            >This is a required field.</b-form-invalid-feedback
          >
        </b-form-group>

        <!-- start date -->

        <b-form-group
          id="startDate-input-group-9"
          label="Start Date*"
          label-for="startDate-input-9"
        >
          <b-form-datepicker
            id="startDate-input-9"
            name="startDate-input-9"
            v-model="$v.form.stratDate.$model"
            :state="validateState('stratDate')"
            aria-describedby="startDate-input-9-live-feedback"
          ></b-form-datepicker>

          <b-form-invalid-feedback id="startDate-input-9-live-feedback"
            >This is a required field.</b-form-invalid-feedback
          >
        </b-form-group>

        <div class="form-group">
          <!-- <button class="btn btn-primary" @click="submitForm()">Submit</button> -->
          <b-button
            class="ml-2"
            variant="primary"
            @click="nextClickValidateTab1()"
            >Next</b-button
          >

          <b-button class="ml-2" variant="warning" @click="resetFormTab1()"
            >Cancel</b-button
          >
          <!-- <b-button class="ml-2" @click="hello()">test</b-button> -->
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import { validationMixin } from "vuelidate";
import { required, minLength, email } from "vuelidate/lib/validators";

export default {
  name: "nuxt_Universal01",
  mixins: [validationMixin],
  data() {
    return {
      district: [
        { value: null, text: "District" },
        { value: "gampaha", text: "Gampaha" },
        { value: "colombo", text: "Colombo" },
        { value: "kaluthara", text: "Kaluthara" },
        { value: "galle", text: "Galle" },
      ],
      form: {
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
      },
    };
  },

  validations: {
    form: {
      contactPerson: { required, minLength: minLength(3) },
      businessName: {},
      contactNum_country: {},
      contactNumber: {},
      streetAddress1: { required },
      streetAddress2: {},
      city: { required },
      district: { required },
      email: { required, email },
      stratDate: { required },
    },
  },

  methods: {
    validateState(name) {
      const { $dirty, $error } = this.$v.form[name];
      return $dirty ? !$error : null;
    },

    // hello() {
    //   // this.$router.push("/BillingAddress");
    //   href = "/BillingAddress";
    // },

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

    nextClickValidateTab1() {
      this.$v.form.$touch();
      if (this.$v.form.$anyError) {
        return;
      }
      this.submitForm();
      console.log("next butoon press");
      //   this.$router.push("/BillingAddress");
    },

    submitForm() {
      console.log("*button click");
      axios
        .post("http://localhost:52208/api/AccountInfo", this.form)
        .then((res) => {
          this.$router.push("/BillingAddress");
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
