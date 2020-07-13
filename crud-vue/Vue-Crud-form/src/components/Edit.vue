<template>
  <form>
    <div class="form-group">
      <label for="NameInput">Name</label>
      <input type="text" class="form-control" id="NameInput"  v-model="employee.name"/>
    </div>
    <div class="form-group">
      <label for="DateInput">Date</label>
      <input type="text" class="form-control" id="NameInput" v-model="employee.date"/>
    </div>
    <div class="form-group">
      <label for="AddressInput">Address</label>
      <input type="text" class="form-control" id="NameInput" v-model="employee.address" />
    </div>

    <button type="submit" class="btn btn-primary" @click="save()">Submit</button>
  </form>
</template>
<script>
export default {
    name:'Edit',
    props:{
        employee: Object
    },
    methods:{
        save(){
            this.$emit('saveit',this.employee)

        }
    }
}
</script>


<style>
</style>