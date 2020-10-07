<template>
  <b-container >
    <p>Hello, Bootstrap-Vue</p>

    <employee-table :employees="employees" />

<b-form>
    <b-row>
      <b-col>
        <label>Employee Id-number</label>
      </b-col>
      <b-col>
        <input v-model="newEmp.id"/>
        </b-col>
    </b-row>
    <b-row>
      <b-col>
        <label>Employee Name</label>
        </b-col>
        <b-col>
        <input type="text" placeholder="snoopy"
        v-model="newEmp.name"/>
        </b-col>
    </b-row>
    <div class="float-md-right">
      <b-btn variant="primary" @click="saveEmployee">
        Add Employee
      </b-btn>

    </div>
    
    
</b-form>

  </b-container>



</template>
<script>
import EmployeeTable from '@/components/EmployeeTable.vue'

export default {
  components : {
    EmployeeTable
  },
  methods:{
    saveEmployee:function(){
    this.employees.push({ id: this.newEmp.id, name: this.newEmp.name })
    }
  },
  data() {
    return{
      showAlert: false,
      newEmp:{
        id:'',
        name:''
      },
      employees:[
        {
          id:1,
          name:'big boo'
        },
        {
          id:2,
          name:'small boo'
        },
        {
          id:3,
          name:'peanutes'
        }
      ]
    }
  }
};
</script>


