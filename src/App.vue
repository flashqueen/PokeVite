<script setup>
import { ref } from 'vue'

let num = ref(0)
</script>

<template>
  <!-- NAVBAR -->
  <nav class="navbar navbar-expand-lg navbar-dark bg-success bg-gradient">
    <div class="container-fluid">
      <router-link class="navbar-brand" to="/">
        <img src="./assets/eeveeLogo.png" alt="Logo" width="44" height="40" class="d-inline-block align-text-top">
      </router-link>
      <router-link class="navbar-brand" to="/">PokeVite</router-link>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav"
        aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item">
            <router-link class="nav-link" aria-current="page" to="/">Home</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/sobre">Sobre</router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>

  <!-- CONTENT -->
  <div class="main">
    <router-view>

    </router-view>
  </div>

  <footer class="bg-secondary text-light py-2 text-center">
    <div>Danilo Oliveira &copy; | {{ new Date().getFullYear() }}</div>
  </footer>
</template>

<style>
footer {
  position: fixed;
  bottom: 0;
  width: 100%;
}
</style>