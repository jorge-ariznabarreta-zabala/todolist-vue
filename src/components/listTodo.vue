<template>

    <div class="row container-fluid" id="CardContainer">
<div class="card border">
    
    <div v-for="todo in listTodo" :key="id" class="card-body border">
        <div>
          <p v-if="todo.completed" class="card-text text-decoration-line-through">{{todo.todo}}</p>
            <p v-else class="card-text">{{todo.todo}}</p>

        </div>
        <button>Editar</button>
        <button @click="deleteTodo(todo.id)">Delete</button>
    </div>
</div>
    </div>
</template>

<script setup>
import { ref } from "vue";
import  axios  from "axios";
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
async function deleteTodo(id){
  try {
    const response = await axios.delete(`http://localhost:3000/todos/${id}`)
    listTodo.value = listTodo.value.filter((todo) => todo.id !==id)
  } catch (error) {
    console.log(error)
  }
}
</script>

<style lang="scss" scoped>

</style>