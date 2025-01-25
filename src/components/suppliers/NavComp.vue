<script setup lang="ts">
import { ref } from "vue";

/** Supplier Details */
const sections = [
  {
    title: "Supplier info",
    details: [
      { icon: "mdi-shopping", text: "Fidson Healthcare" },
      { icon: "mdi-map-marker", text: "4, Road 56, Lagos, Nigeria" },
    ],
  },
  {
    title: "Contact info",
    details: [
      { icon: "mdi-email-outline", text: "musa@example.com" },
      { icon: "mdi-cellphone-text", text: "+234 801 234 5678" },
    ],
  },
  {
    title: "Bank info",
    details: [
      { icon: "mdi-bank", text: "First Bank Plc" },
      { icon: "mdi-cellphone-text", text: "-----" },
    ],
  },
];

/** Tab */
const selectedTab = ref<number>(1);

const updateSelectedTab = (tab: number) => {
  selectedTab.value = tab;
};

const tabs = [
  { id: 1, label: "Purchase order" },
  { id: 2, label: "Invoices" },
  { id: 3, label: "Payment" },
];
</script>

<template>
  <div class="px-5 bg-[#F7F8F9] border-b">
    <!-- Supplier Details -->
    <div
      class="sm:flex-row lg:w-[50%] md:w-full flex flex-col gap-5 sm:gap-0 justify-between items-start py-4"
    >
      <img
        src="https://media.licdn.com/dms/image/v2/C4D0BAQHWFN4vkNFGWQ/company-logo_200_200/company-logo_200_200/0/1630579436099?e=1745452800&v=beta&t=JpcGZMFWwTh7mYJZEVnsiqIfxOPJv3yid8gQdsaG8WM"
        alt="logo"
        class="w-[40px]"
      />
      <div v-for="(section, index) in sections" :key="index">
        <p class="text-[#172B4D] font-semibold mb-2">{{ section.title }}</p>
        <div
          v-for="(detail, idx) in section.details"
          :key="idx"
          class="text-[#44546F] flex lg:items-center items-start gap-2 text-sm mb-1"
        >
          <v-icon :icon="detail.icon" color="#091E424F" /> {{ detail.text }}
        </div>
      </div>
    </div>

    <!-- Transaction Details -->
    <div
      class="bg-white p-4 py-6 my-4 border rounded-lg sm:flex-row lg:w-[50%] md:w-full flex flex-wrap gap-5 justify-between items-start text-sm"
    >
      <div class="border-r pr-4 min-w-[165px] sm:w-auto flex-1">
        <div class="flex justify-between items-center mb-3">
          <p class="text-[#626F86]">Purchase Order</p>
          <p class="p-1 px-2 font-semibold rounded-md bg-[#091E420F]">40</p>
        </div>
        <p class="font-semibold">₦5,250,000</p>
      </div>
      <div class="sm:border-r pr-4 w-full sm:w-auto flex-1">
        <div class="flex justify-between items-center mb-3">
          <p class="text-[#626F86]">Invoices</p>
          <p class="p-1 px-2 font-semibold rounded-md bg-[#091E420F]">20</p>
        </div>
        <p class="font-semibold">₦5,250,000</p>
      </div>

      <v-divider :thickness="1" class="border-opacity-100 d-sm-none" />

      <div class="border-r pr-4 w-full sm:w-auto flex-1">
        <div class="flex justify-between items-center mb-3">
          <p class="text-[#626F86]">Payments</p>
          <p class="p-1 px-2 font-semibold rounded-md bg-[#091E420F]">25</p>
        </div>
        <p class="font-semibold">₦5,250,000</p>
      </div>
      <div class="border-r pr-4 w-full sm:w-auto flex-1">
        <div class="mb-4">
          <p class="text-[#626F86]">Purchase Qty</p>
        </div>
        <p class="font-semibold">12</p>
      </div>
      <div class="w-full sm:w-auto flex-1">
        <div class="mb-4">
          <p class="text-[#626F86]">Returns</p>
        </div>
        <p class="font-semibold">0</p>
      </div>
    </div>

    <!-- Tab -->
    <div class="pt-6">
      <ol class="flex text-[#44546F]">
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
    </div>
  </div>
</template>

<style scoped>
.selected-tab {
  color: #172b4d;
  background: white;
  border-top-left-radius: 8px;
  border-top-right-radius: 8px;
  border: 1px solid #091e4224;
  border-bottom: none;
  font-weight: 600;
  transition: background 1.5s ease, color 1.5s ease;
}

.nav-item {
  margin-bottom: -1px;
  padding: 10px 20px;
  cursor: pointer;
  transition: opacity 1.5s ease, background 1.5s ease;
}

.nav-item:hover {
  opacity: 0.8;
  color: #172b4d;
}

.nav-item.selected-tab:hover {
  opacity: 1;
}
</style>
