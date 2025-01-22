<script setup lang="ts">
import { RouterLink } from "vue-router";
</script>

<template>
  <div class="flex items-center justify-center min-h-screen bg-gray-100">
    <ul class="space-y-4 text-center">
      <li>
        <router-link
          :to="{ name: 'signin' }"
          class="block text-lg font-medium text-gray-700 hover:text-white hover:bg-blue-500 transition-colors duration-300 rounded-md px-4 py-2 shadow-md"
        >
          Login Screen
        </router-link>
      </li>
      <li>
        <router-link
          :to="{ name: 'dashboard' }"
          class="block text-lg font-medium text-gray-700 hover:text-white hover:bg-blue-500 transition-colors duration-300 rounded-md px-4 py-2 shadow-md"
        >
          Dashboard Screen
        </router-link>
      </li>
      <li>
        <router-link
          :to="{ name: 'suppliers' }"
          class="block text-lg font-medium text-gray-700 hover:text-white hover:bg-blue-500 transition-colors duration-300 rounded-md px-4 py-2 shadow-md"
        >
          Suppliers List Screen
        </router-link>
      </li>
    </ul>
  </div>
</template>

<style scoped></style>
