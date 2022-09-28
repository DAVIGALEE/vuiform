<script setup>
import Form from "./components/Form.vue"
import Table from "./components/Table.vue"
import {reactive,ref,toRefs,watch} from 'vue'

const data = reactive({})
watch(data,()=>{
    //console.log(data)
})
</script>

<template>
 
<Form @response="(message)=>Object.assign(data, message)"></Form>
<Table :msg="data"></Table>

</template>

<style scoped>
 
</style>
