<template>
    <div class="column algo">
        <newTodo />
        <listTodo />
    </div>
</template>

<script setup>
import newTodo from './components/newTodo.vue'
import listTodo from './components/listTodo.vue'
</script>

<style  scoped>
.algo {
    background-image: url(./assets/mika-korhonen-5ObeNx0iIKk-unsplash.jpg);
}
</style>
