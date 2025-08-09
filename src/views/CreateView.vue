<script setup>
import { reactive, ref } from 'vue';

const todo = reactive({
  title: '',
  completed: '',
})
</script>
<template>
  <main>
    <div class="form-create">
      <div class="title">
        <h2>Create todo</h2>
      </div>
      <div class="input-todo">
        <div class="title">
          <label for="">Title</label>
          <input type="text" name="" id="" placeholder="Enter title todo" v-model="todo.title">
        </div>
        <div class="completed">
          <label for="">Completed</label>
          <input type="radio" value="true" name="completed" id="" v-model="todo.completed">
          <input type="radio" value="false" name="completed" id="" v-model="todo.completed">
        </div>
      </div>
      <div class="btn-main">
        Create new todo 
      </div>
    </div>
  </main>
</template>

<style scoped>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
.input-todo {
  display: flex;
  flex-direction: column;
}
</style>
