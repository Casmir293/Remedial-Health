<script setup lang="ts"></script>

<template>
  <section class="flex h-dvh flex-col items-center justify-center">
    <h1 class="font-sans text-3xl font-bold">Remedial Health</h1>
    <p class="mb-10 border-b-2 font-thin">
      Make all of your pharmaceutical purchases in one place
    </p>
    <main class="w-[90%]">
      <section class="flex flex-col items-center justify-center">
        <div class="mb-3 text-2xl font-semibold">404: Page not found</div>
        <router-link
          :to="{ name: 'home' }"
          class="block text-xl text-blue-500 underline"
          >Go Home</router-link
        >
      </section>
    </main>
  </section>
</template>
