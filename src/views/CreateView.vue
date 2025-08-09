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
      <div class="label-title">
        <h2>Create todo</h2>
      </div>
      <div class="input-todo">
        <div class="title">
          <label for="">Title</label>
          <input type="text" name="" id="" placeholder="Enter title todo" v-model="todo.title">
        </div>
        <div class="completed">
          <label for="">Completed: </label>
          True <input type="radio" value="true" name="completed" id="" v-model="todo.completed">
          False <input type="radio" value="false" name="completed" id="" v-model="todo.completed">
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
.label-title, .btn-main {
  margin: 1rem 0;
}
.input-todo {
  display: flex;
  flex-direction: column;
  row-gap: 1rem;
}
.title {
  display: flex;
  flex-direction: column;
}
.completed {
  display: flex;
}
</style>
