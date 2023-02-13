<script setup>
import { RouterLink, RouterView } from "vue-router";
</script>
<template>
  <nav
    class="navbar navbar-expand-lg bg-body-tertiary"
    style="background-color: #22343c"
  >
    <div class="container-fluid">
      <RouterLink class="navbar-brand" style="color: white" to="/"
        >Home</RouterLink
      >

      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarNav"
        aria-controls="navbarNav"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item">
            <RouterLink
              class="nav-link active"
              aria-current="page"
              style="color: white"
              to="/about"
              >About</RouterLink
            >
          </li>
        </ul>
      </div>
    </div>
  </nav>
  <RouterView />
</template>
