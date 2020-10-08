<template>
  <div id="employee-table">
    <p v-if="employees.length < 1" class="empty-table">No employees!!</p>
    <table v-else striped hover bordered fixed responsive sticky-header>
      <!-- :items="employees" -->

      <b-tr>
        <b-th>Employee id</b-th>
        <b-th>Employee name</b-th>
        <b-th>Actions</b-th>
      </b-tr>

      <b-tr v-for="employee in employees" :key="employee.id">
        <td v-if="editing === employee.id">
          <input type="text" v-model="employee.id" />
        </td>
        <b-td v-else>{{ employee.id }}</b-td>
        <td v-if="editing === employee.id">
          <input type="text" v-model="employee.name" />
        </td>
        <b-td v-else>{{ employee.name }}</b-td>

        <td v-if="editing === employee.id">
          <button @click="editEmployee(employee)">Save</button>
          <button class="muted-button" @click="editing = null">Cancel</button>
        </td>
        <td v-else>
          <button @click="editMode(employee.id)">Edit</button>
          <button @click="$emit('delete:employee', employee.id)">Delete</button>
        </td>
      </b-tr>
    </table>
  </div>
</template>

<script>
export default {
  name: "employee-table",
  props: {
    employees: Array,
  },
  data() {
    return {
      editing: null,
    };
  },
  methods: {
    editMode(id) {
      this.editing = id;
    },

    editEmployee(employee) {
      if (employee.id === "" || employee.name === "") return;
      this.$emit("edit:employee", employee.id, employee);
      this.editing = null;
    },
  },
};
</script>

<style scoped>
table {
  height: 250px;
}
</style>
