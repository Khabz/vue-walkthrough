<template>
  <div id="employee-form" class="mt-5">
    <form @submit.prevent="handleSubmit">
      <div class="form-group">
        <label>First Name</label>
        <input
          v-model="employee.firstName"
          :class="{ 'has-error': submitting && invalidFirstName }"
          @focus="clearStatus"
          @keypress="clearStatus"
          type="text"
          class="form-control"
          placeholder="Employee's First Name"
        />
      </div>
      <div class="form-group">
        <label>Last Name</label>
        <input
          v-model="employee.lastName"
          :class="{ 'has-error': submitting && invalidLastName }"
          @focus="clearStatus"
          @keypress="clearStatus"
          type="text"
          class="form-control"
          placeholder="Employee's Last Name"
        />
      </div>
      <div class="form-group">
        <label>Email</label>
        <input
          v-model="employee.email"
          :class="{ 'has-error': submitting && invalidEmail }"
          @focus="clearStatus"
          type="email"
          class="form-control"
          placeholder="Employee's Email Address"
        />
        <p v-if="error && submitting" class="error-message">❗ Please fill out all required fields</p>
        <p v-if="success" class="success-message">✅ Employee successfully added</p>
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
      submitting: false,
      error: false,
      success: false,
      employee: {
        firstName: "",
        lastName: "",
        email: ""
      }
    };
  },
  methods: {
    handleSubmit() {
      this.submitting = true;
      this.clearStatus();

      if (this.invalidFirstName || this.invalidLastName || this.invalidEmail) {
        this.error = true;
        return;
      }

      this.$emit("add:employee", this.employee);
      this.employee = {
        firstName: "",
        lastName: "",
        email: ""
      };
      this.error = false;
      this.success = true;
      this.submitting = false;
    },

    clearStatus() {
      this.success = false;
      this.error = false;
    }
  },
  computed: {
    invalidFirstName() {
      return this.employee.firstName == '';
    },
    invalidLastName() {
      return this.employee.lastName == '';
    },
    invalidEmail() {
      return this.employee.email == '';
    }
  }
};
</script>

<style scoped>
form {
  margin-bottom: 2rem;
}

.form-control {
  font-weight: 500;
}

.error-message {
  color: #d33c40;
}

.success-message {
  color: #32a95d;
}
</style>