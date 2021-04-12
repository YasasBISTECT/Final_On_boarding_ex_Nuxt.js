<template>
  <div>
    <h1>Register New User</h1>
    <b-card no-body>
      <b-tabs content-class="mt-3" card>
        <!-- tab 1 -->
        <b-tab title="Account Info" active> <AccountInfo /> </b-tab>

        <!-- tab 2 -->
        <b-tab title="Billing Address"><BillingAddress /> </b-tab>

        <!-- tab 3 -->
        <b-tab title="Shipping Address"><ShippingAddress /> </b-tab>
      </b-tabs>
    </b-card>
  </div>
</template>

<script>
export default {};
</script>

<style >
body {
  padding: 5rem;
}
</style>