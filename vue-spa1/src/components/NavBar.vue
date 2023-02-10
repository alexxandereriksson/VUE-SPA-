<script setup>
import { RouterLink, RouterView } from "vue-router";
</script>
<template>
  <nav class="navbar bg-body-tertiary">
    <div class="container-fluid">
      <RouterLink class="navbar-brand" to="/">Home</RouterLink>
    </div>
  </nav>
  <RouterView />
</template>

<style scoped></style>
