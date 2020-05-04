<template>
  <div id="employee-form" class="mt-5">
    <form @submit.prevent="handleSubmit">
      <div class="form-group">
        <label>First Name</label>
        <input
          v-model="employee.firstName"
          type="text"
          class="form-control"
          placeholder="Employee's First Name"
        />
      </div>
      <div class="form-group">
        <label>Last Name</label>
        <input
          v-model="employee.lastName"
          type="text"
          class="form-control"
          placeholder="Employee's Last Name"
        />
      </div>
      <div class="form-group">
        <label>Email</label>
        <input
          v-model="employee.email"
          type="email"
          class="form-control"
          placeholder="Employee's Email Address"
        />
      </div>
      <button class="btn btn-primary">Submit</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "EmployeeForm",
  data() {
    return {
      employee: {
        firstName: "",
        lastName: "",
        email: ""
      }
    };
  },
  methods: {
    handleSubmit() {
      this.$emit("add:employee", this.employee);
    }
  }
};
</script>