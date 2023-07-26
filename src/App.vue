<script setup>
import { ref } from 'vue'

const msg = ref('Hello World!')
const newItem = ref('')
const newItemHighPriority = ref(false)
const iceCreamFlavours = ref([]);
const listItems= ref ([
  { id : 1 ,label :"10 milk shakes "},
 { id:2, label:"2 milk cakes"},
 { id : 3 , label :"20 glasses"}
])
</script>
  
<template>
  <h1>{{ msg }}</h1>
  <div class ="add-item-form">

    <input type="text" placeholder="add Item" v-model="newItem"/>
    <button class="btn btn-primary">Add to list</button>
    <span>Priority</span>
    <label>
      <input type="checkbox" v-model="newItemHighPriority" value="low"/>
      High Priority
    </label>
    <br/>
    <label>
      <input type="checkbox" value="vanilla" v-model="iceCreamFlavours"/>
      Vanilla
    </label>
    <label>
      <input type="checkbox" value="strawabery" v-model="iceCreamFlavours"/>
      Strawabery
    </label>
    <label>
      <input type="checkbox" value="chocolate" v-model="iceCreamFlavours"/>
      Chocolate
    </label>
</div>
  {{ iceCreamFlavours }}
  <ul>
    <li v-for="{id,label}, in listItems" :key="id">{{label }}</li>
  </ul>
</template>