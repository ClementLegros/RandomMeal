<script setup lang="ts">
import { RouterView } from "vue-router";
import MyNavbar from "./components/MyNavbar.vue";
</script>

<template>
  <!-- import the navbar -->
  <MyNavbar></MyNavbar>
  <RouterView />
</template>
