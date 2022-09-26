<script setup>

</script>

<template>
  <div class=" container-fluid  d-flex flex-column col-md-5 col-md-offset-5  w-50  min-vh-100 justify-content-center align-items-center"  >
  <div class="row my-auto ">
  <h1>VuiForm</h1>
  
  <form class="form-horizontal col-12  col-offset-12">
  <div class="form-row">
    <div class="form-group col-md-12">
      <label for="inputEmail4">Email</label>
      <input type="email" class="form-control" id="inputEmail4" placeholder="Email">
    </div>
    <div class="form-group col-md-12">
      <label for="inputPassword4">Password</label>
      <input type="password" class="form-control" id="inputPassword4" placeholder="Password">
    </div>
  </div>
  <div class="form-group col-md-8">
    <label for="inputAddress">Address</label>
    <input type="text" class="form-control" id="inputAddress" placeholder="1234 Main St">
  </div>
  
  <div class="form-row">
    
    <div class="form-group col-md-5 mt-2">
      <select id="inputState" class="form-control">
        <option value="" disabled selected>Choose Gender</option>
        <option value="Male">Male</option>
        <option value="Female">Female</option>
      </select>
    </div>
    <div class="form-group col-md-10 mt-2">
      <textarea class = "form-control" rows = "3" placeholder = "Notes" ></textarea>
    </div>
  </div>
  <button type="submit" class="btn btn-primary mt-2">Submit</button>
</form>
</div>

</div>
</template>

<style scoped>
  h1{
    margin-bottom: 1in !important;
  }
  textarea {
  resize: none;
}
</style>
