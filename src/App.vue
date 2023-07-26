<script setup>
import { ref } from 'vue'

const msg = ref('Shopping List App!')
const newItem = ref('')
const newItemHighPriority = ref(false)
const iceCreamFlavours = ref([]);
const listItems= ref ([
  { id : 1 ,label :"10 milk shakes "},
 { id:2, label:"2 milk cakes"},
 { id : 3 , label :"20 glasses"}
])
const saveItem=()=>{
  listItems.value.push({id: listItems.value.length + 1 ,label:newItem.value})
  newItem.value = ""
}
</script>
  
<template>
  <h1>{{ msg }}</h1>
  <form 
   @submit.prevent="saveItem" 
   class ="add-item-form">

    <input type="text" placeholder="add Item" v-model.trim="newItem"/>
    <label>
      <input type="checkbox"
      v-model="newItemHighPriority"/>
      High Priority
    </label>
    <button 
    class="btn btn-primary"
    >
    Add to list</button> 
</form>
  <ul>
    <li v-for="{id,label}, in listItems" :key="id">{{label }}</li>
  </ul>
</template>