<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Menu from './components/layout/Menu.vue'
</script>

<template>
  <div>
    <Menu />
    <RouterView />
  </div>
</template>

<style>
  * {
    margin: 0px;
    padding: 0px;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  }
</style>
