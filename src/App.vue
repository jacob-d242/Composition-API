<script setup>
import { ref,computed } from 'vue'
import MainAppR from './MainAppR.vue'

const listItems = ref([
   {
     id: 1, 
     label: "10 party hats", 
     purchased: true, 
     highPriority: false
   },
   {
		id: 2, 
    label:"2 board games", 
    purchased: true, 
    highPriority: false
   },
   {
     id: 3, 
     label: "20 cups", 
     purchased: false, 
     highPriority: true
   }
])
const msg = ref('Shopping List App!')
const characterCount = computed(()=> newItem.value.length) 
const newItem = ref('')
const newItemHighPriority = ref(false)
const editing = ref(false);
const reverseItems = computed(() => [...listItems.value].reverse())
const saveItem = () => {
  listItems.value.push(
    {
    id: listItems.value.length + 1,
    label: newItem.value,
    highPriority: newItemHighPriority.value,
    purchased: false
}
  )
  newItem.value = ""
  // newItemHighPriority.value = ""
}

const editItem = (e) => {
  editing.value = e
  newItem.value = ""
 // newItemHighPriority.value =""
}

const togglePurchase = (item) => {
  item.purchased = !item.purchased
}
</script>

<template>
  <div>
    <div class="header">
    <h1>{{ msg }}</h1>
    <button v-if="editing" class="btn btn-primary" @click="editItem(false)">Cancel</button>
    <button v-else class="btn btn-primary" @click="editItem(true)">Add New</button>
  </div>
  <form
    :v-if="editing"
    @submit.prevent="saveItem"
    class="add-item-form"
  >

    <input type="text" placeholder="add Item" v-model.trim="newItem" />
    <label>
      <input type="checkbox" v-model="newItemHighPriority" value="newItemHighPriority"/>
      High Priority
    </label>
    <button :disabled="newItem.length === 0" class="btn btn-primary">
      Add to list
    </button>
  </form>
  <p>{{ characterCount }}/100</p>
  <ul>
    <li
      v-for="( item, index ) in reverseItems"
      @click="togglePurchase(item)"
      class="static-class"
      :key="item.id"
      :class="{
        strikeout: item.purchased,
        priority: item.highPriority
      }"
    >
      {{ item.label }}
    </li>
  </ul>
  <p v-if="!listItems.length">
    No Items available please add in the above
  </p>
  </div>
 <div>
  <MainAppR/>
 </div>
</template>
