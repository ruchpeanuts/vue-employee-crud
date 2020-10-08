<template>
  <div id="employee-table">
    <b-table
      striped
      hover
      bordered
      fixed
      responsive
      :items="employees"
    ></b-table>
  </div>
</template>

<script>
export default {
  name: "employee-table",
  props: {
    employees: Array,
  },
};
</script>

<style scoped></style>
