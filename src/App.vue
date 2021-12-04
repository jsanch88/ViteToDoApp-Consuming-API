<script setup>
import Title from "./components/Title.vue";
import List from "./components/List.vue";
</script>

<template>
  <div class="min-h-screen bg-gradient-to-r from-purple-400 via-blue-500 to-pink-500">
    <div class="container flex flex-col pt-8 mx-auto space-y-8">
      <Title />
      <div class="flex justify-around">
        <List />
        <List isCompleted />
      </div>
    </div>
  </div>
</template>