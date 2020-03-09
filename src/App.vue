<template>
  <div id="app" class="small-container">
   <h1>Employees</h1>
    <employee-form @add:employee="addEmployee"></employee-form>
    <employee-table
      v-bind:employees= "employees"
    />
  </div>
</template>

<script>
import EmployeeTable from './components/EmployeeTable.vue'
import EmployeeForm from './components/EmployeeForm.vue'

export default {
  name: 'app',
  components: {
    EmployeeTable,
    EmployeeForm
  },
  data () {
    return {
      employees: [
        {
          id: 1,
          name: 'Richard ',
          email: 'rmcn@lol.com'
        },
        {
          id: 2,
          name: 'D ',
          email: 'djdjd@lol.com'
        },
        {
          id: 3,
          name: 'Riley ',
          email: 'rjrjfn@lol.com'
        }
      ]
    }
  },
  methods: {
    addEmployee (employee) {
      const lastId =
        this.employees.length > 0
          ? this.employees[this.employees.length - 1].id
          : 0
      const id = lastId + 1
      const newEmployee = {...employee, id}

      this.employees = [...this.employees, newEmployee]
    }
  }
} /** end export default**/

</script>

<style>
  button {
    background: #009435;
    border: 1px solid #009435;
  }

  .small-container {
    max-width: 680px;
  }

  body{
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }
</style>
