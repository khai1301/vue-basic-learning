<script setup>
import { computed, onMounted, ref } from 'vue';
import { useRouter } from 'vue-router';

const router = useRouter();
const todos = ref([]);
const currentPage = ref(1);
const perPage = ref(10);
const keywordSearch = ref('');
const isLoading = ref(true);
const fetchTodos = async() => {
    const res = await fetch('https://jsonplaceholder.typicode.com/todos');
    const data = await res.json();
    todos.value = data;
    isLoading.value = false;
}
const filterTodos = computed(() => {
  if (!keywordSearch.value) return todos.value;
  return todos.value.filter(item => item.title.toUpperCase().indexOf(keywordSearch.value.toUpperCase()) !== -1);
})
const paginatedTodo = computed(() => {
  const start = (currentPage.value - 1) * perPage.value;
  const end = start + perPage.value;
  return filterTodos.value.slice(start, end);
})

const totalPages = computed(() => {
  return Math.ceil(filterTodos.value.length / perPage.value);
})

const changePage = (page) => {
  if (page >= 1 && page <= totalPages.value) {
    currentPage.value = page;
  }
}
onMounted(fetchTodos);
</script>

<template>
  <main>
    <input type="text" name="" id="" placeholder="Search Here" v-model="keywordSearch">
    <div class="" v-if="isLoading">Loading ...
    </div>
    <div class="" v-else>
      <div class="group-card" v-for="todo in paginatedTodo" :key="todo.id">
      <div class="card-item" @click="router.push({ path: `/todo/${todo?.id}`})">
        <div class="title">
          <h2 class="title-todo">Title: {{ todo?.title }}</h2>
        </div>
        <div class="description">
          <p class="description-todo">Completed: {{ todo?.completed }}</p>
        </div>
      </div>
    </div>
    </div>
    <div class="paginate">
      <button @click="changePage(currentPage-1)" :disabled="currentPage === 1">Trước</button>
      <button
        v-for="page in totalPages"
        :key="page"
        @click="changePage(page)"
        :class="{ active: page === currentPage }"
      >
        {{ page }}
      </button>
      <button @click="changePage(currentPage+1)" :disabled="currentPage === totalPages">Sau</button>
    </div>
  </main>
</template>

<style scoped>
.active {
  background: #80be2f;
  color: #fff;
}
</style>
