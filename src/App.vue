<script setup>
import { RouterLink, RouterView } from 'vue-router'
// import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
<nav>
  <ul class="nav nav-pills nav-fill">
    <li class="nav-item">
      <a class="navbar-brand">Quran</a>
    </li>
    <li class="nav-item">
      <a class="nav-link" aria-current="page" href="#"><router-link to = "/">Home</router-link></a>
    </li>
    <li class="nav-item">
      <a class="nav-link" href="#"><router-link to = "/Surah">Surah</router-link></a>
    </li>
  </ul>
  </nav>
  <hr>

  <p class= "fixed-bottom"> copyright by faaysha </p>


  <RouterView />
</template>

<style scoped>

nav{
  margin-top: 10px;
  margin-bottom: 10px;
  margin-left: 10px;
  margin-right: 10px;
  font-size: 20px;
  font-family: "sans-serif";
  font-weight: bold;
}
.navbar-brand{
  font-size: 25px;
  font-family: "monospace";
  font-weight: bolder;
}

.fixed-bottom{
  text-align: center;
  font-size: 10px;
  font-weight: bold;
}
</style>
