<template>

    <div class="row container-fluid" id="CardContainer">
<div class="card border">
    
    <div v-for="lista in listTodo" :key="id" class="card-body border">
        <div>
            <p class="card-text">{{lista.todo}}</p>
            <p class="card-text text-decoration-line-through">{{lista.todo}}</p>

        </div>
        <button>Editar</button>
        <button>Delete</button>
    </div>
</div>
    </div>
</template>

<script setup>
import { ref } from "vue";
import  axios  from "axios";
const listTodo = ref([]);

//ENVIAR COMENTARIOS

// async function getTodoList() {
//     var requestOptions = {
//   method: 'GET',
//   redirect: 'follow'
// };

// fetch("http://localhost:3000/todos", requestOptions)
//   .then(response => response.text())
//   .then(result =>  {return result})
//   .catch(error => console.log('error', error));
// }
// listTodo=getTodoList()
// console.log(listTodo);
var config = {
  method: 'get',
  url: 'http://localhost:3000/todos',
  headers: {}
}

const getName = async () => {
  try {
    const response = await axios.request(config)
    listTodo.value = response.data
    console.log(response.data)
  } catch (error) {
    console.log(error)
  }
}
getName()
</script>

<style lang="scss" scoped>

</style>