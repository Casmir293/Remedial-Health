<script setup lang="ts"></script>

<template>
  <header class="flex items-center justify-between px-5">
    <div class="flex items-center justify-between">
      <v-icon
        icon="mdi-apps"
        class="cursor-pointer hover:opacity-70 transition-all"
      />
      <img
        class="mx-3 cursor-pointer hover:opacity-70 transition-all"
        width="65"
        src="https://media.licdn.com/dms/image/v2/C4D0BAQHWFN4vkNFGWQ/company-logo_200_200/company-logo_200_200/0/1630579436099?e=1745452800&v=beta&t=JpcGZMFWwTh7mYJZEVnsiqIfxOPJv3yid8gQdsaG8WM"
        alt="logo"
      />
      <v-select
        label="Branch"
        :items="['Lagos', 'Asaba']"
        variant="outlined"
        density="comfortable"
        width="120px"
      />
    </div>

    <div class="flex items-center justify-between">
      <v-icon
        icon="mdi-bell-badge"
        color="grey-darken-2"
        class="cursor-pointer hover:opacity-70 transition-all"
      />
      <v-icon
        icon="mdi-message-text-outline"
        class="mx-3 cursor-pointer hover:opacity-70 transition-all"
        color="grey-darken-2"
      />
      <v-icon
        icon="mdi-face-man"
        color="grey-darken-2"
        class="cursor-pointer hover:opacity-70 transition-all"
      />
    </div>
  </header>
  <v-divider :thickness="1" class="border-opacity-100" />
</template>

<style scoped>
::v-deep(.v-input__details) {
  display: none;
}
</style>
