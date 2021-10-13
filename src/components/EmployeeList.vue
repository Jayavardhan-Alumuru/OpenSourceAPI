<template>
  <div id="EmployeeList">
    <h1>
      Employee list
    </h1>
    <table border="1px">
      <tr>
       <td>Id</td>
       <td>Name</td>
       <td>Salary</td>
       <td>Age</td>
      </tr>

      <tr v-for="item in list" v-bind:key="item.id">
       <td>{{item.id  }} </td> 
       <td>{{item.employee_name }} </td>
       <td>{{item.employee_salary}} </td>
       <td>{{item.employee_age}} </td>
      </tr>
      
    </table>
  </div>
</template>

<script>

import axios from 'axios'


export default {
  name : "EmployeeList",
  data(){
    return {list: undefined}
  },
  mounted(){
    axios.get('http://dummy.restapiexample.com/api/v1/employees').then((response)=>{
      this.list=response.data.data
      console.warn(response.data.data)
    })
  }
}
</script>
