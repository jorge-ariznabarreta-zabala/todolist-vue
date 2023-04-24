<template>
  <div class="row container-fluid" id="CardContainer">
    <div class="card border">

      <div v-for="todo in listTodo" :key="id" class="card-body border">
        <div>
          <input class="toggle" type="checkbox" v-model="todo.completed" @change="editTodo(todo)"/>
          <input type="text" @blur="editTodo(todo)" autofocus v-if="todo.completed"
            class="card-text text-decoration-line-through" v-model="todo.todo" />
          <input type="text" @blur="editTodo(todo)" autofocus v-else class="card-text" v-model="todo.todo" />

        </div>
      
        <button @click="deleteTodo(todo.id)">Delete</button>
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