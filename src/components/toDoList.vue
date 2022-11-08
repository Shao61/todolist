<script setup>
import { ref } from 'vue'
let id = 0
const newToDo = ref('')
const toDos = ref([])

function addToDo() {
  toDos.value.push({id: id++, text:newToDo.value})
   newToDo.value = ''
}
function delToDo(toDo) {
  toDos.value = toDos.value.filter((t) => t.id !== toDo.id)
}
</script>



<template>
  <div id="insert">
    <input type="text" v-model="newToDo" placeholder="請輸入">
    <button @click="addToDo" id="newli">add</button>
  </div>
 
 <ul>
  <li v-for="toDo in toDos" :key="toDo.id">
    {{toDo.text}}
    <button @click="delToDo(toDo)">delete</button>
  </li>
 </ul>
</template>


<style scoped>
#insert{
  text-align: center;
}
button{
  border-radius: 5px;
  border: 1px solid transparent;
  padding: 0.6em 1.2em;
  font-size: 0.5em;
  font-weight: 500;
  font-family: inherit;
  background-color: #1a1a1a;
  cursor: pointer;
  transition: border-color 0.25s;
}
#newli:hover {
  border-color: #646cff;
}

</style>
