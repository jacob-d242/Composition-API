<script setup>
import { ref } from 'vue'

const msg = ref('Shopping List App!')
const newItem = ref('')
const newItemHighPriority = ref(false)
const editing = ref(false);
const listItems= ref ([
//   { id : 1 ,label :"10 milk shakes "},
//  { id:2, label:"2 milk cakes"},
//  { id : 3 , label :"20 glasses"}
])
const saveItem=()=>{
  listItems.value.push({id: listItems.value.length + 1 ,label:newItem.value})
  newItem.value = ""
}
const editItem = (e) =>{
  editing.value = e
  newItem.value = ""
}
</script>
  
<template>
  <div class="header"> 
    <h1>{{ msg }}</h1>
    <button v-if="editing" class="btn btn-primary" @click="editItem(false)" >Cancel</button>
    <button v-else class="btn btn-primary" @click="editItem(true)" >Add New</button>
  </div>
  <a v-bind:href="newItem">Dynamic Link</a>
  <form 
  v-if="editing "
   @submit.prevent="saveItem" 
   class ="add-item-form">

    <input type="text" placeholder="add Item" v-model.trim="newItem"/>
    <label>
      <input type="checkbox"
      v-model="newItemHighPriority"/>
      High Priority
    </label>
    <button 
    :disabled="newItem.length === 0"
    class="btn btn-primary"
    >
    Add to list</button> 
</form>
  <ul>
    <li v-for="{id,label}, in listItems" :key="id">{{label }}</li>
  </ul>
  <p v-if="!listItems.length ">
    No Items available please add in the above
  </p>
</template>