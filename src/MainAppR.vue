<script setup>
import {ref,reactive} from 'vue'
let state = reactive({count : 0})
const increment =() =>{
   
    count : state.count++
   
}
</script>
<template>
    <di>
        <h1>{{ state.count }}</h1>
        <button @click="increment">increment</button>
    </di>
</template>

<!-- reactive is used fo primitives -->