<template>
  <div id="app">
    <div class="container">
      <h1>Employee</h1>
      <EmployeeForm @add:employee="addEmployee" />
      <EmployeeTable :employees="employees" />
    </div>
  </div>
</template>

<script>
import EmployeeTable from "./components/EmployeeTable";
import EmployeeForm from "./components/EmployeeForm";
export default {
  name: "App",
  data() {
    return {
      employees: [
        {
          id: 1,
          firstName: "Ndivhuwo",
          lastName: "Khabubu",
          email: "hello@khabubundivhu.co.za"
        },
        {
          id: 2,
          firstName: "John",
          lastName: "Doe",
          email: "john@khabubundivhu.co.za"
        },
        {
          id: 3,
          firstName: "Mary",
          lastName: "Wick",
          email: "mary@khabubundivhu.co.za"
        }
      ]
    };
  },
  components: {
    EmployeeTable,
    EmployeeForm
  },
  methods: {
    addEmployee(employee) {
      const lastId =
        this.employees.length > 0
          ? this.employees[this.employees.length - 1].id
          : 0;
      const id = lastId + 1;
      const newEmployee = { ...employee, id };

      this.employees = [...this.employees, newEmployee];
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
