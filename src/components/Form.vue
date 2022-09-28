<script setup>
import {ref,reactive} from "vue"
const form = ref("form")
let prevData = []

if(localStorage.getItem("data")) {
  prevData = JSON.parse(localStorage.getItem("data"))
}else{
   prevData = []
}
const data = reactive([
  ...prevData,
])
console.log( prevData)
const emit = defineEmits(['response'])

const handleSubmit = () => {

const information = {
    firstName:form._rawValue[0].value,
    lastName:form._rawValue[1].value,
    address:form._rawValue[2].value,
    dateOfBirth:form._rawValue[3].value,
    gender:form._rawValue[4].value,
    note:form._rawValue[5].value,
}
data.push(information)
emit('response', data)
localStorage.setItem("data",JSON.stringify(data))
window.location.reload();
}

</script>

<template>
  <div class=" container-fluid  d-flex flex-column col-md-5 col-md-offset-5  w-50  min-vh-100 justify-content-center align-items-center"  >
  <div class="row my-auto ">
  <h1>VuiForm</h1>
  
  <form class="form-horizontal col-12  col-offset-12"  @submit.prevent="handleSubmit" ref="form">
  <div class="form-row">
    <div class="form-group col-md-12">
        <label for="firstName" class="form-label">First name</label>
      <input type="text" class="form-control" id="firstName" placeholder="First Name" required >
      <div class="valid-feedback">
      Looks good!
    </div>
    <div id="validationServer01" class="invalid-feedback">
        Please write first name.
      </div>
    </div>
    <div class="form-group col-md-12">
      <label for="lastName">Last Name</label>
      <input type="text" class="form-control" id="lastName" placeholder="Last Name" required>
    </div>
    <div class="form-group col-md-8">
    <label for="address">Address</label>
    <input type="text" class="form-control" id="address" placeholder="1234 Main St" required>
  </div>
    <div class="form-group col-md-12">
      <label for="dateOfBirth">Date Of Birth</label>
      <input type="date" class="form-control" id="dateOfBirth" placeholder="Last Name">
    </div>
  </div>
  
  
  <div class="form-row">
    
    <div class="form-group col-md-5 mt-2">
      <select id="gender" class="form-control">
        <option value="" disabled selected>Choose Gender</option>
        <option value="Male">Male</option>
        <option value="Female">Female</option>
      </select>
    </div>
    <div class="form-group col-md-10 mt-2">
      <textarea id="note" class = "form-control" rows = "3" placeholder = "Notes" ></textarea>
    </div>
  </div>
  <button type="submit" class="btn btn-primary mt-2" @submit="handleSubmit">Submit</button>
</form>

</div>

</div>

</template>

<style scoped>
  h1{
    margin-bottom: 0.5in !important;
  }
  textarea {
  resize: none;
}
</style>
