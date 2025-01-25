<script setup lang="ts">
import { useRouter } from "vue-router";
const router = useRouter();

const backNav = () => {
  router.back();
};
</script>

<template>
  <div class="pr-5 pl-1 h-[65px] flex justify-between items-center">
    <div>
      <v-btn @click="backNav" prepend-icon="mdi-chevron-left" elevation="0">
        Back
      </v-btn>
    </div>
    <div class="font-medium hidden sm:block">SUPPLIER'S DASHBOARD</div>
    <div>
      <v-btn prepend-icon="mdi-pencil" color="#0C66E4" class="text-none mr-4">
        Edit
      </v-btn>
      <v-btn icon="mdi-dots-horizontal" color="#091e420f" />
    </div>
  </div>
</template>

<style scoped></style>
