<script setup lang="ts">
import { RouterLink } from "vue-router";
</script>

<template>
  <div class="flex items-center justify-center min-h-screen">
    <ul class="space-y-4 text-center">
      <p class="mb-5 text-3xl font-semibold text-blue-500">
        Remedial Health Task
      </p>

      <li>
        <router-link
          :to="{ name: 'signin' }"
          class="block text-lg font-medium text-gray-700 hover:text-white hover:bg-blue-500 transition-colors duration-500 rounded-md px-4 py-2 shadow-md border"
        >
          < Signin Screen />
        </router-link>
      </li>
      <li>
        <router-link
          :to="{ name: 'dashboard' }"
          class="block text-lg font-medium text-gray-700 hover:text-white hover:bg-blue-500 transition-colors duration-500 rounded-md px-4 py-2 shadow-md border"
        >
          < Dashboard Screen />
        </router-link>
      </li>
      <li>
        <router-link
          :to="{ name: 'suppliers' }"
          class="block text-lg font-medium text-gray-700 hover:text-white hover:bg-blue-500 transition-colors duration-500 rounded-md px-4 py-2 shadow-md border"
        >
          < Suppliers List Screen />
        </router-link>
      </li>
      <li>
        <router-link
          :to="{ name: 'docs' }"
          class="block text-lg font-medium text-gray-700 hover:text-white hover:bg-blue-500 transition-colors duration-500 rounded-md px-4 py-2 shadow-md border"
        >
          < Documentation />
        </router-link>
      </li>
    </ul>
  </div>
</template>

<style scoped></style>
