<template>
  <div id="app">
    <div class="row">
      <div class="col-2">
        <h2>CRUD form</h2>
        
      </div>
      <div class="col-2 offset-6">
        <button type="button" class="btn btn-primary" @click="addem()">Thêm</button>
      </div>
     <div class="container"> <edit-employee :employee="employee" @saveit="save" v-if="isEdit"></edit-employee>

     </div>
    </div>
        
    <table class="table table-striped" style="width:960px;margin:0 auto">
      <thead>
        <tr>
          <th>#</th>
          <th>Name</th>
          <th>Date</th>
          <th>Address</th>
          <th>Action</th>
        </tr>
      </thead>
      <tbody>
     
        <tr v-for="item in employeeList" :key="item.id">
          <td>{{item.id}}</td>
          <th>{{item.name}}</th>
          <td>{{item.date}}</td>
          <td>{{item.address}}</td>

          <td>
            <button type="button" class="btn btn-warning" @click="editrecord(item)">Edit</button>
            <button type="button" class="btn btn-info" @click="deleterecord(item)">Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import Edit from "./components/Edit";
export default {
  name: "App",
  data() {
    return {
      employeeList: [
        {
          id: 1,
          name: "nguyen van A",
          date: "1/1/1999",
          address: "Hanoi"
        },
        {
          id: 2,
          name: "nguyen van B",
          date: "05/05/1995",
          address: "Haiwai"
        },
        // {
        //   id: 3,
        //   name: "nguyen van C",
        //   date: "1/1/1996",
        //   address: "Bangkok"
        // }
      ],
       indexcont:3,
       employee:null,
       isEdit:false
    };
  },
  components: {
    "edit-employee": Edit
  },

  methods: {
    
    addem(){
      let employee ={
        // id:Math.floor(Math.random()*10000),
        id: this.indexcont++,
        name: '',
          date: '',
          address: ''
      }
      this.employee = employee
      this.isEdit=true
    },
    save(employee){
      let index = this.employeeList.findIndex(item => item.id == employee.id)
      if(index>=0){
        this.employeeList.splice(index,1,employee)
      }else{
        this.employeeList.push(employee)
      }
     
      this.isEdit=false
     
    },
    editrecord(employee){
      this.employee=JSON.parse(JSON.stringify(employee))
      this.isEdit=true
      
    },
    deleterecord(employee){
      let index = this.employeeList.findIndex(item => item.id == employee.id)
      this.employeeList.splice(index,1)
    }
    
  }
};
</script>

<style>
.table-striped tbody tr:nth-of-type(odd) {
  background-color: rgba(208, 10, 10, 0.05);
}
.btn-primary {
  margin-top: 12px;
  background-color: rgb(223, 118, 183);
}
.container {
  margin-bottom: 20px;
}
</style>
