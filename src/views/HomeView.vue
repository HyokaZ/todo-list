<script setup>
import { ref } from 'vue'

// สร้างตัวแปรแบบ reactive สำหรับเก็บรายการ To-Do
const todos = ref([])
// สร้างตัวแปรแบบ reactive สำหรับเก็บค่าข้อความที่พิมพ์ใน input
const newTodo = ref('')

// ฟังก์ชันสำหรับเพิ่มรายการใหม่ใน To-Do List
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
      <!-- <th>ToDo</th>
      <th>ToDo</th> -->
      <tr v-for="(todo, index) in todos" :key="index">
        <td>
          <p>
            {{ todo }}
          </p>
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
  background-color: #1cff3b;
  
  
}
.deleteButton{
  background-color: #ff3022;
  color: white;
}

.textTable table {
  padding: 25px;
  margin: 0px auto;
  width: 420px;
}
.textTable p {
  text-align: left;
}
</style>