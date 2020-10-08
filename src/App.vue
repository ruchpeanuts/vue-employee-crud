<template>
  <b-container>
    <div>
      <b-btn
        class="float-md-right"
        variant="primary"
        @click="state = 'editEmployee'"
        v-show="state === 'default'"
      >
        Add Employee
      </b-btn>

      <div v-show="state === 'editEmployee'">
        <b-form>
          <b-row>
            <b-col>
              <label>Employee Id-number</label>
            </b-col>
            <b-col>
              <input type="Number" v-model="newEmp.id" />
            </b-col>
          </b-row>
          <b-row>
            <b-col>
              <label>Employee Name</label>
            </b-col>
            <b-col>
              <input type="text" placeholder="snoopy" v-model="newEmp.name" />
            </b-col>
          </b-row>
          <div class="float-md-right">
            <b-btn variant="primary" @click="saveEmployee">
              Save Employee
            </b-btn>
          </div>
        </b-form>
      </div>
    </div>
    <employee-table :employees="employees" />
    <!-- 
     style="background-image: url('https://picsum.photos/1140/1140');"
     -->
  </b-container>
</template>
<script>
import EmployeeTable from "@/components/EmployeeTable.vue";

export default {
  components: {
    EmployeeTable,
  },
  methods: {
    saveEmployee: function() {
      this.employees.push({ id: this.newEmp.id, name: this.newEmp.name });
    },
  },
  data() {
    return {
      state: "default",
      showAlert: false,
      newEmp: {
        id: "",
        name: "",
      },
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
