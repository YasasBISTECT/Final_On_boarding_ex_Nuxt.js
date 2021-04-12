<template>
  <div class="center">
    <div class="hText">E-Commerce Site</div>
    <div class="child">
      <b-button-toolbar
        aria-label="Toolbar with button groups and dropdown menu"
      >
        <div class="button">
          <b-dropdown
            class="m-md-2"
            variant="outline-primary"
            right
            text="Registered user data"
          >
            <b-dropdown-item href="/GetAccountInfo"
              >Account info</b-dropdown-item
            >
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
        </div>
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
.center {
  position: absolute;
  top: 50%;
  left: 50%;
  margin: -100px 0 0 -300px;
}
.child {
  position: relative;
  top: 50%;
  left: 50%;
  margin: 5px 0 0 -200px;
}
.hText {
  font-size: 500%;
}
</style>