<script setup lang="ts">
import { computed } from "vue";

// Top Suppliers
const suppliers = [
  { name: "Emzor Pharmaceuticals", value: 235000 },
  { name: "Fidson Healthcare", value: 122040 },
  { name: "Emzor Pharmaceuticals", value: 76320 },
  { name: "Emzor Pharmaceuticals", value: 63470 },
  { name: "Fidson Healthcare", value: 4609 },
];

const totalSupplierValue = computed(() =>
  suppliers.reduce((total, supplier) => total + supplier.value, 0)
);

const suppliersWithProgress = computed(() =>
  suppliers.map((supplier) => ({
    ...supplier,
    progress: Math.round((supplier.value / totalSupplierValue.value) * 100),
  }))
);

// Top Products
const products = [
  { name: "Paracetamol", value: 2000 },
  { name: "Ibuprofen", value: 500 },
  { name: "Amoxicillin", value: 403 },
  { name: "Vitamin C Tablets", value: 321 },
  { name: "Artemether-Lumefantrine", value: 81 },
];

const totalProductValue = computed(() =>
  products.reduce((total, product) => total + product.value, 0)
);

const productsWithProgress = computed(() =>
  products.map((product) => ({
    ...product,
    progress: Math.round((product.value / totalProductValue.value) * 100),
  }))
);
</script>

<template>
  <div class="md:px-5">
    <div class="rounded-lg border p-5">
      <!-- Top Suppliers -->
      <p class="text-[#172B4D] font-medium text-lg mb-8">Top Suppliers</p>
      <template v-for="(supplier, index) in suppliersWithProgress" :key="index">
        <p class="text-sm text-[#172B4D]">{{ supplier.name }}</p>
        <div class="flex justify-between items-center gap-2 mb-2">
          <v-progress-linear
            color="#0C66E4"
            bg-color="#033"
            :model-value="supplier.progress"
            height="8"
            rounded
          />
          <div>&#8358;{{ supplier.value.toLocaleString() }}</div>
        </div>
      </template>
      <v-divider :thickness="1" class="border-opacity-100 my-8" />

      <!-- Top Products -->
      <p class="text-[#172B4D] font-medium text-lg">Top Products</p>
      <template v-for="(product, index) in productsWithProgress" :key="index">
        <p class="text-sm text-[#172B4D]">{{ product.name }}</p>
        <div class="flex justify-between items-center gap-2 mb-2">
          <v-progress-linear
            color="#A3F94E"
            bg-color="#033"
            :model-value="product.progress"
            height="8"
            rounded
          />
          <div>{{ product.value.toLocaleString() }}</div>
        </div>
      </template>
    </div>
  </div>
</template>

<style scoped></style>
