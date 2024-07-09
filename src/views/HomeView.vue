<script setup>
import { ref } from 'vue'

const todos = ref([])
const newTodo = ref('')

function addTodo() {
  if (newTodo.value.trim()) {
    todos.value.push(newTodo.value.trim())
    newTodo.value = ''
  }
}

function deleteTodo(index) {
  todos.value.splice(index, 1)
}

</script>

<template>
  <div>
    <h1 class="headder">To Do List</h1>
  </div>
  <div >
    <input  v-model="newTodo" type="text" class="inputText">
    <button @click="addTodo" class="addButton">Add</button>
  </div>
  <div class="textTable">
    <table>
      <tr v-for="(todo, index) in todos" :key="index">
        <td>
          <p> {{ todo }} </p>
        </td>
        <td> 
          <button class="deleteButton" @click="deleteTodo(index)"> Delete </button> 
        </td>
      </tr>
    </table>
  </div>
  
</template>

<style>
#app {
  text-align: center;
}

.headder {
  margin-top: 50px;
}

.inputText {
  margin-right: 10px;
  width: 300px;
  height: 30px;
}

.addButton {
  width: 50px;
  height: 35px;
  background-color: #00a5ff;
  
  
}

.deleteButton{
  background-color: #ff3022;
  color: white;
}

.addButton:active, .deleteButton:active {
  transform: translateY(4px);
  box-shadow: 0 5px #666;
}

/* เอฟเฟคเมื่อ hover */
/* .addButton:hover, .deleteButton:hover {
  background-color: #ccc;
} */

.textTable table {
  padding: 25px;
  margin: 0px auto;
  width: 420px;
}

.textTable p {
  text-align: left;
}
</style>