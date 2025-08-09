<script setup>
import { RouterLink } from 'vue-router';
</script>

<template>
  <header>
    <img src="@/assets/logo.svg" alt="" class="logo" width="60" height="60">
    <nav>
      <router-link to="/">
        <div class="btn-main">
          Home todo
        </div>
      </router-link>
      <router-link to="/create" >
        <div class="btn-action">
          Create todo
        </div>
      </router-link>
    </nav>
  </header>
  <router-view></router-view>
</template>

<style scoped>
header {
  display: flex;
  justify-content: space-around;
  padding: 0.4rem 2rem;
  box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.2);
}
nav {
  display: flex;
  align-items: center;
  column-gap: 1rem;
}
</style>
