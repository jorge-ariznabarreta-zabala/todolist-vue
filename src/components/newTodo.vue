<template>
  <fieldset>
    <legend>NewTodo:</legend>
    
        
          <input type="text" name="newTodo" id="newTodo" autofocus aria-describedby="helpId" placeholder="Insert a new Todo"
          v-model="newTodo" @keyup.enter="postTodo()">
      
        
      </fieldset>
</template>

<script setup>
let newTodo = '';

//ENVIAR COMENTARIOS

async function postTodo() {
  const url = 'http://localhost:3000/todos';
  const response = await fetch(url, {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: `{"todo":"${this.newTodo}","completed":false}`
  });
  //recarga
  location.reload();
}

</script>

<style lang="scss" scoped></style>