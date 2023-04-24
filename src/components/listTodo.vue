<template>
  <div class="row container-fluid" id="CardContainer">
    <div class=" m-3">


    
    <div v-for="todo in listTodo" :key="id" class="card-body border w-50 p-3">
        <div>
          <input class="toggle m-3" type="checkbox" v-model="todo.completed" @change="editTodo(todo)" />
          <input type="text" @blur="editTodo(todo)" autofocus v-if="todo.completed" class="card-text shadow p-3 mb-5 bg-body-tertiary rounded text-decoration-line-through" v-model="todo.todo" />
          <input type="text" @blur="editTodo(todo)" autofocus v-else class="card-text shadow p-3 mb-5 bg-body-tertiary rounded" v-model="todo.todo" />
          <button class="btn btn-danger mx-3 p-3" @click="deleteTodo(todo.id)">Delete</button>

        </div>
      
    </div>
  </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import axios from "axios";
import { computeStyles } from "@popperjs/core";
const listTodo = ref([]);



const getName = async () => {
  try {
    const response = await axios.get('http://localhost:3000/todos')
    listTodo.value = response.data
    console.log(response.data)
  } catch (error) {
    console.log(error)
  }
}
getName()
async function deleteTodo(id) {
  try {
    const response = await axios.delete(`http://localhost:3000/todos/${id}`)
    listTodo.value = listTodo.value.filter((todo) => todo.id !== id)
    //Aprovecho la reactividad de listTodo para actualizar la vista
  } catch (error) {
    console.log(error)
  }
}

async function editTodo(todo) {
  console.log(todo);
 

  try {
    const response = await axios.patch(`http://localhost:3000/todos/${todo.id}`, {
    "todo": todo.todo,
    "completed": todo.completed
  })

    //Aprovecho la reactividad de listTodo para actualizar la vista
  } catch (error) {
    console.log(error)
  }
}
</script>

<style lang="scss" scoped></style>