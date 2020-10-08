<template>
  <b-container>
    <h1>Employees</h1>

    <employee-form @save:employee="saveEmployee" />

    <employee-table
      :employees="employees"
      @delete:employee="deleteEmployee"
      @edit:employee="editEmployee"
    />
  </b-container>
</template>
<script>
import EmployeeTable from "@/components/EmployeeTable.vue";
import EmployeeForm from "@/components/EmployeeForm.vue";
export default {
  components: {
    EmployeeTable,
    EmployeeForm,
  },
  methods: {
    saveEmployee: function(newEmp) {
      console.log("testing handleSubmit in parent", newEmp);

      this.employees = [...this.employees, newEmp];
    },
    deleteEmployee(id) {
      this.employees = this.employees.filter((employee) => employee.id != id);
    },
    editEmployee(id, updatedEmployee) {
      this.employees = this.employees.map((employee) =>
        employee.id === id ? updatedEmployee : employee
      );
    },
  },
  data() {
    return {
      employees: [
        {
          id: 1,
          name: "big boo",
        },
        {
          id: 2,
          name: "small boo",
        },
        {
          id: 3,
          name: "peanutes",
        },
      ],
    };
  },
};
</script>

<style scoped>
.btn {
  margin: 10px;
  margin-right: 140px;
}
.btn.btn-outline-primary {
  margin-right: 10px;
  margin-top: 75px;
}
.editblock {
  height: 130px;
}
.material-icons {
  font-size: 15px;
}
</style>
