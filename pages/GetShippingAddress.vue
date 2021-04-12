<template>
  <div>
    <br />
    <h1>Shipping Address of User's Data Table</h1>
    <br /><br />

    <div>
      <table class="table">
        <thead>
          <tr scope="col">
            <th>No</th>
            <th>Shipping Id</th>
            <th>CustRegistration Id</th>
            <!-- <th>Country Code</th> -->
            <!-- <th>Phone Number</th> -->
            <th>Address 1</th>
            <th>Address 2</th>
            <th>City</th>
            <th>District</th>
            <th>Specific Request</th>
            <th>Email Subscription</th>
          </tr>
        </thead>
        <tbody>
          <tr scope="row" v-for="(post, index) in posts" :key="post">
            <td>{{ index + 1 }}</td>
            <td>{{ post.shippingId }}</td>
            <td>{{ post.custRegistrationId }}</td>
            <!-- <td>{{ post.contactPerson }}</td> -->
            <!-- <td>{{ post.businessName }}</td> -->
            <!-- <td>{{ post.contactNumber }}</td> -->
            <td>{{ post.streetAddress1 }}</td>
            <td>{{ post.streetAddress2 }}</td>
            <td>{{ post.city }}</td>
            <td>{{ post.district }}</td>
            <td>{{ post.specificRegistrationRequest }}</td>
            <td>{{ post.email }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "consume-rest-api",
  data() {
    return {
      posts: null,
    };
  },

  created() {
    axios
      .get(`http://localhost:52208/api/ShippingAddress`)
      .then((response) => {
        // JSON responses are automatically parsed.
        this.posts = response.data;
        console.warn(this.posts);
      })
      .catch((e) => {
        this.errors.push(e);
      });
    // ------------
    // const axios = require("axios");
    // axios.get("http://localhost:52208/api/AccountInfo").then((resp) => {
    //   console.warn(resp.data);
    // });
  },
};
</script>

<style scoped>
.post {
  margin: 20px;
}
</style>