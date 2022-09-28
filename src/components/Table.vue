<script setup>
    import {ref,watch,reactive} from "vue"
  const props = defineProps({
  msg: Object
})
let data = []
if(localStorage.getItem("data")) {
    data = reactive(JSON.parse(localStorage.getItem("data")))
}

const note = ref("")
const userIdentifier = ref("")
const syncData=(text,firstName)=>{
    note.value = text;
    userIdentifier.value = firstName;
}
const deleteRow=(event)=>{
  let identifier = Number(event.target.parentElement.id)
  console.log(identifier)
  
 data.splice(data.findIndex(indexFinder),1)
 function indexFinder(obj) {
  return obj.id==identifier;
}
 const updatedData = reactive([])
 Object.assign(updatedData,data)
 //console.log(updatedData)
 localStorage.setItem("data", JSON.stringify(updatedData))
 event.target.parentNode.remove()
 window.location.reload();
}


</script>
    
    <template>
     
     <div class="container mb-5">
<table class="table table-hover table-dark ">
  <thead>
    <tr>
      <th scope="col">#</th>
      <th scope="col">First Name</th>
      <th scope="col">Last Name</th>
      <th scope="col">Address</th>
      <th scope="col">Date Of Birth</th>
      <th scope="col">Gender</th>
    </tr>
  </thead>
  <tbody>
    <tr  v-for="dataObj,index in data" data-bs-toggle="modal" :id="index" data-bs-target="#exampleModal" :key="dataObj.id" @click="syncData(dataObj.note,dataObj.firstName)">
      <th scope="row">{{index}}</th>
      <td>{{dataObj.firstName}}</td>
      <td>{{dataObj.lastName}}</td>
      <td>{{dataObj.address}}</td>
      <td>{{dataObj.dateOfBirth}}</td>
      <td>{{dataObj.gender}}</td>
      
    <button data-bs-toggle="asd"  data-bs-target="#nothing" class="btn border-none" @click="deleteRow">
        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="white" class="bi bi-trash3" viewBox="0 0 16 16">
  <path d="M6.5 1h3a.5.5 0 0 1 .5.5v1H6v-1a.5.5 0 0 1 .5-.5ZM11 2.5v-1A1.5 1.5 0 0 0 9.5 0h-3A1.5 1.5 0 0 0 5 1.5v1H2.506a.58.58 0 0 0-.01 0H1.5a.5.5 0 0 0 0 1h.538l.853 10.66A2 2 0 0 0 4.885 16h6.23a2 2 0 0 0 1.994-1.84l.853-10.66h.538a.5.5 0 0 0 0-1h-.995a.59.59 0 0 0-.01 0H11Zm1.958 1-.846 10.58a1 1 0 0 1-.997.92h-6.23a1 1 0 0 1-.997-.92L3.042 3.5h9.916Zm-7.487 1a.5.5 0 0 1 .528.47l.5 8.5a.5.5 0 0 1-.998.06L5 5.03a.5.5 0 0 1 .47-.53Zm5.058 0a.5.5 0 0 1 .47.53l-.5 8.5a.5.5 0 1 1-.998-.06l.5-8.5a.5.5 0 0 1 .528-.47ZM8 4.5a.5.5 0 0 1 .5.5v8.5a.5.5 0 0 1-1 0V5a.5.5 0 0 1 .5-.5Z"/>
</svg></button>
    </tr>

  </tbody>
</table>
<div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">{{userIdentifier}}</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
        <p>{{note}}</p>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
      </div>
    </div>
  </div>
</div>
</div>
</template>
    
<style scoped>
.btn{
border-radius:0 !important;

}
.btn > * {
  pointer-events: none;
}

</style>
    