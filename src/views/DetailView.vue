<script setup>
import { onMounted, ref } from 'vue';
import { useRoute } from 'vue-router';

const router = useRoute();
const todo = ref(null);
const isLoading = ref(true);
const fetchDetailTodo = async() => {
  const res = await fetch(`https://jsonplaceholder.typicode.com/todos/${router.params.id}`);
  const data = await res.json();
  todo.value = data;
  isLoading.value = false;
}
onMounted(fetchDetailTodo);
</script>

<template>
  <main>
    <div class="" v-if="isLoading">Loading ...</div>
    <div class="card-item" v-else>
      <div class="title">
        <h2 class="title-todo">Title: {{ todo?.title }}</h2>
      </div>
      <div class="description">
        <p class="description-todo">Completed: {{ todo?.completed }}</p>
      </div>
    </div>
  </main>
</template>
