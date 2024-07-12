<script setup>
import { ref } from 'vue'

const todos = ref([]);
const newTodo = ref('');

function addTodo() {
  if (newTodo.value) {
    todos.value.push(newTodo.value)
    newTodo.value = ''
  }
}

function deleteTodo(index) {
  todos.value.splice(index, 1)
}
</script>

<template>
  <div>
    <h1 class="header">To Do List</h1>
  </div>
  <div class="inputContainer">
    <input v-model="newTodo" type="text" class="inputText">
    <button @click="addTodo" class="addButton">Add</button>
  </div>
  <div class="textTable">
    <table>
      <thead>
        <tr>
          <th class="todoColumn">Todo</th>
          <th class="actionColumn">Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(todo, index) in todos" :key="index">
          <td>{{ todo }}</td>
          <td>
            <button @click="deleteTodo(index)" class="deleteButton">Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style>
#app {
  text-align: center;
  padding-top: 20px;
}

.header {
  margin-top: 50px;
}

.inputContainer {
  margin-bottom: 20px;
}

.inputText {
  margin-right: 10px;
  width: 300px;
  height: 30px;
  padding: 5px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 14px;
}

.addButton {
  height: 35px;
  padding: 0 15px;
  background-color: #00a5ff;
  border: none;
  border-radius: 4px;
  color: white;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.addButton:active {
  background-color: #007bbf;
  transform: translateY(2px); 
}

.addButton:hover {
  background-color: #007bbf;
}

.deleteButton {
  height: 30px;
  background-color: #ff3022;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  display: block; 
  margin: 0 auto; 
}

.deleteButton:active {
  background-color: #e6493e;
  transform: translateY(2px);
}

.deleteButton:hover {
  background-color: #e6493e;
}

.textTable {
  margin: 20px auto;
  width: 80%;
  max-width: 600px;
  border-collapse: collapse;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.textTable table {
  width: 100%;
}

.textTable th, .textTable td {
  padding: 12px;
  border-bottom: 1px solid #ccc;
}

.textTable th {
  background-color: #f0f0f0;
  font-weight: bold;
  justify-content: space-around;
}

.textTable td {
  text-align: left;
}

.textTable tbody tr:nth-child(even) {
  background-color: #f9f9f9;
}

.textTable tbody tr:last-child td {
  border-bottom: none;
}

.textTable p {
  margin: 0;
  font-size: 14px;
  color: #666;
}

.todoColumn {
  width: 80%;
  
}

.actionColumn {
  width: 20%;
}
</style>
