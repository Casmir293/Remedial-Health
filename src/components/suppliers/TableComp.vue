<script setup lang="ts">
import { ref } from "vue";

const search = ref("");
const items = ref([
  {
    order_id: "RHPO-1651244214",
    supplier_name: "Fidson Healthcare",
    type: "Trade",
    date: "5/21/2024",
    total: "₦2,055,043.00",
    quantity: "93",
    quantity_returned: "1",
    status: "Approved",
  },
  {
    order_id: "RHPO-1651244211",
    supplier_name: "Fidson Healthcare",
    type: "Swap",
    date: "3/25/2024",
    total: "₦423,369.55",
    quantity: "120",
    quantity_returned: "2",
    status: "Approved",
  },
  {
    order_id: "RHPO-1651244891",
    supplier_name: "Fidson Healthcare",
    type: "Trade",
    date: "5/21/2024",
    total: "₦386,937.91",
    quantity: "67",
    quantity_returned: "5",
    status: "Pending",
  },
  {
    order_id: "RHPO-1651214524",
    supplier_name: "Fidson Healthcare",
    type: "Trade",
    date: "5/20/2024",
    total: "₦952,639.63",
    quantity: "84",
    quantity_returned: "3",
    status: "Approved",
  },
  {
    order_id: "RHPO-1051244110",
    supplier_name: "Fidson Healthcare",
    type: "Trade",
    date: "6/20/2024",
    total: "₦629,792.38",
    quantity: "36",
    quantity_returned: "0",
    status: "Approved",
  },
  {
    order_id: "RHPO-1651241013",
    supplier_name: "Fidson Healthcare",
    type: "Trade",
    date: "6/28/2024",
    total: "₦1,638,653.94",
    quantity: "47",
    quantity_returned: "5",
    status: "Failed",
  },
  {
    order_id: "RHPO-1651241014",
    supplier_name: "Fidson Healthcare",
    type: "Swap",
    date: "7/2/2024",
    total: "₦51,333.32",
    quantity: "48",
    quantity_returned: "4",
    status: "Approved",
  },
  {
    order_id: "RHPO-1651241015",
    supplier_name: "Fidson Healthcare",
    type: "Trade",
    date: "12/6/2024",
    total: "₦1,168,142.80",
    quantity: "11",
    quantity_returned: "0",
    status: "Pending",
  },
  {
    order_id: "RHPO-1651241016",
    supplier_name: "Fidson Healthcare",
    type: "Trade",
    date: "6/11/2024",
    total: "₦1,462,624.27",
    quantity: "29",
    quantity_returned: "2",
    status: "Approved",
  },
  {
    order_id: "RHPO-1651241017",
    supplier_name: "Fidson Healthcare",
    type: "Trade",
    date: "1/4/2024",
    total: "₦249,268.61",
    quantity: "50",
    quantity_returned: "0",
    status: "Approved",
  },
]);

const headers = [
  {
    key: "order_id",
    title: "Order No",
  },
  {
    key: "supplier_name",
    title: "Supplier's Name",
  },
  {
    key: "type",
    title: "Type",
  },
  {
    key: "date",
    title: "Date",
  },
  {
    key: "total",
    title: "Total",
  },
  {
    key: "quantity",
    title: "Quantity Returned",
  },
  {
    key: "status",
    title: "Status",
  },
  { title: "Action", key: "action" },
];
</script>

<template>
  <!-- Table Accesories -->
  <div class="px-5 flex justify-between items-center overflow-x-auto">
    <div class="lg:block hidden">PURCHASE ORDER</div>

    <div class="py-4 flex justify-center items-center gap-3">
      <v-btn append-icon="mdi-chevron-down" variant="tonal" class="text-none">
        Page 1/6
      </v-btn>
      <v-text-field
        width="250"
        v-model="search"
        prepend-inner-icon="mdi-magnify"
        density="compact"
        label="Search"
        hide-details
        variant="outlined"
      ></v-text-field>
      <v-btn
        prepend-icon="mdi-filter-variant"
        color="#172B4D"
        variant="outlined"
        class="text-none"
      >
        Filter
      </v-btn>
      <v-btn
        prepend-icon="mdi-swap-vertical"
        color="#172B4D"
        variant="outlined"
        class="text-none"
      >
        Sort by
      </v-btn>
      <v-icon
        icon="mdi-menu"
        size="30"
        color="#0C66E4"
        class="cursor-pointer hover:opacity-70 transition-all bg-[#E9F2FF] p-2 rounded-md"
      />
      <v-icon
        icon="mdi-apps"
        size="30"
        color="#44546F"
        class="cursor-pointer hover:opacity-70 transition-all d-md-none"
      />
    </div>
  </div>
  <!-- ./ Table Accesories -->

  <!-- Table -->
  <div class="px-5 pb-10">
    <VCard>
      <VDataTable
        v-model:search="search"
        :headers="headers"
        :items="items"
        :ç-per-page="10"
        hover
        hide-default-footer
      >
        <!-- table head -->
        <template
          v-slot:headers="{ columns, isSorted, getSortIcon, toggleSort }"
        >
          <tr class="bg-[#F7F8F9]" style="border-radius: 10px">
            <template v-for="column in columns" :key="column.key">
              <th>
                <span
                  class="mr-2 cursor-pointer font-semibold"
                  @click="() => toggleSort(column)"
                  >{{ column.title }}</span
                >
                <template v-if="isSorted(column)">
                  <v-icon :icon="getSortIcon(column)"></v-icon>
                </template>
              </th>
            </template>
          </tr>
        </template>
        <!-- status -->
        <template v-slot:item.status="{ item }">
          <div
            class="w-[85px] px-2 py-1 rounded-md border-[1px] font-semibold text-center"
            :class="{
              'bg-[#DCFFF1] text-[#216E4E] border-[#BAF3DB]':
                item.status === 'Approved',
              'bg-[#FFF7DC] text-[#946F00] border-[#FFE3A3]':
                item.status === 'Pending',
              'bg-[#FFEDED] text-[#C92D2D] border-[#FFB2B2]':
                item.status === 'Failed',
            }"
          >
            {{ item.status }}
          </div>
        </template>

        <!-- Action -->
        <template v-slot:item.action="{ item }">
          <v-menu transition="slide-y-transition">
            <template v-slot:activator="{ props }">
              <v-icon icon="mdi-dots-vertical" v-bind="props"></v-icon>
            </template>
            <v-list>
              <v-list-item class="cursor-pointer hover:opacity-60">
                <v-list-item-title class="flex items-center gap-2">
                  <v-icon
                    icon="mdi-pencil"
                    size="small"
                  />Edit</v-list-item-title
                >
              </v-list-item>
              <v-list-item class="cursor-pointer hover:opacity-60">
                <v-list-item-title class="flex items-center gap-2">
                  <v-icon
                    icon="mdi-delete"
                    size="small"
                  />Delete</v-list-item-title
                >
              </v-list-item>
            </v-list>
          </v-menu>
        </template>
      </VDataTable>
    </VCard>
  </div>
  <!-- ./ Table -->
</template>

<style scoped></style>
