<template>
  <div>
    <h1>E-Commerce Site</h1>
    <div>
      <b-button-toolbar
        aria-label="Toolbar with button groups and dropdown menu"
      >
        <b-dropdown
          class="m-md-2"
          variant="outline-primary"
          right
          text="Registered user data"
        >
          <b-dropdown-item href="/GetAccountInfo">Account info</b-dropdown-item>
          <b-dropdown-item href="/GetBillingAddress"
            >Billing Address</b-dropdown-item
          >
          <b-dropdown-item href="/GetShippingAddress"
            >Shipping Address</b-dropdown-item
          >
        </b-dropdown>

        <b-link :to="{ path: '/AccountInfo' }" replace>
          <b-button class="m-md-2" variant="outline-success"
            >Register a new user</b-button
          >
        </b-link>
      </b-button-toolbar>
    </div>
  </div>
</template>

<script>
// import Buttons from "../../nuxt_T01/components/Buttons.vue";
export default {
  //   components: { Buttons },
};
</script>

<style>
</style>