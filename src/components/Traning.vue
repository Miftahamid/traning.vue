<template>
  <div class="add container">
    <Alert v-if="alert" v-bind:message="alert"/>
    <h1 class="page-header">Add Customer</h1>
    <form v-on:submit="addCustomer">
      <div class="well">
        <h4>Customer Info</h4>
        <div class="form-group">
          <label>First Name</label>
          <input
            type="text"
            class="form-control"
            placeholder="First Name"
            v-model="customer.first_name"
          >
        </div>
         <div class="well">
        <h4>Customer Location</h4>
        <div class="form-group">
          <label>Address</label>
          <input type="text" class="form-control" placeholder="Address" v-model="customer.address">
        </div>
        <div class="form-group">
          <label>City</label>
          <input type="text" class="form-control" placeholder="City" v-model="customer.city">
        </div>
        <div class="form-group">
          <label>State</label>
          <input type="text" class="form-control" placeholder="State" v-model="customer.state">
        </div>
      </div>
      <button type="submit" class="btn btn-primary">Submit</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "Traning",
  data() {
    return {
      customer: {},
      alert: ""
    };
  },
  methods: {
    addCustomer(e) {
      if (
        !this.customer.first_name ||
        !this.customer.last_name ||
        !this.customer.email
      ) {
        this.alert = "Please fill in all required fields";
      } else {
        let newCustomer = {
          first_name: this.customer.first_name,
          last_name: this.customer.last_name,
          phone: this.customer.phone,
          email: this.customer.email,
          address: this.customer.address,
          city: this.customer.city,
          state: this.customer.state
        };
        this.$http
          .post("http://slimapp/api/customer/add", newCustomer)
          .then(function(response) {
            this.$router.push({
              path: "/",
              query: { alert: "Customer Added" }
            });
          });
        e.preventDefault();
      }
      e.preventDefault();
    }
  },
  components: {
    Alert
  }
};
</script>


<style scoped>
h1 {
  background: blue;
}
</style>

