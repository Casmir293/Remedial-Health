<script setup lang="ts">
import { ref } from "vue";

const selectedTab = ref<number>(1);

const updateSelectedTab = (tab: number) => {
  selectedTab.value = tab;
};

const tabs = [
  { id: 1, label: "Dashboard" },
  { id: 2, label: "All Suppliers" },
  { id: 3, label: "Purchase order" },
  { id: 4, label: "Payments" },
  { id: 5, label: "Supplier's return" },
  { id: 6, label: "Product request" },
];
</script>

<template>
  <nav class="px-5">
    <ol class="flex gap-4 text-[#44546F]">
      <li
        v-for="tab in tabs"
        :key="tab.id"
        @click="updateSelectedTab(tab.id)"
        class="nav-item"
        :class="{ 'selected-tab': selectedTab == tab.id }"
      >
        {{ tab.label }}
      </li>
    </ol>
  </nav>
  <v-divider :thickness="1" class="border-opacity-100" />
</template>

<style scoped>
.selected-tab {
  border-bottom: 2px solid #0c66e4;
  color: #0c66e4;
  transition: all 1.5s ease;
}

.nav-item {
  padding: 16px 8px;
  cursor: pointer;
  opacity: 1;
  transition: all 0.3s ease;
}

.nav-item:hover {
  opacity: 0.8;
  color: #0c66e4;
}
</style>
