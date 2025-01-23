<script setup lang="ts">
const cards = [
  {
    title: "Received Supplies",
    value: "60",
    change: "12.95%",
    changeIcon: "mdi-arrow-up",
    changeBg: "#BAF3DB",
    changeText: "#216E4E",
    description: "Compared to last month",
  },
  {
    title: "Received Products Qty",
    value: "20,200",
    change: "12.95%",
    changeIcon: "mdi-arrow-down",
    changeBg: "#FFD5D2",
    changeText: "#AE2E24",
    description: "Compared to last month",
  },
  {
    title: "Received Supplies",
    value: "60",
    change: "12.95%",
    changeIcon: "mdi-minus",
    changeBg: "#091E420F",
    changeText: "#172B4D",
    description: "Compared to last month",
  },
  {
    title: "Orders Pending Arrival",
    value: "15",
  },
  {
    title: "Orders Passed Delivery Date",
    value: "10",
  },
  {
    title: "Average Processing Time",
    value: "06 Days | 14 Hours | 53 Minutes",
  },
];
</script>

<template>
  <div class="info-card gap-5">
    <div
      v-for="(card, index) in cards"
      :key="index"
      class="min-h-[151px] rounded-lg border p-5"
    >
      <p class="text-[#626F86] text-sm font-medium">{{ card.title }}</p>
      <p class="text-lg font-medium mt-6 mb-2">{{ card.value }}</p>
      <div v-if="card.change" class="flex items-center gap-3">
        <p
          class="flex items-center text-sm font-semibold py-1 px-2 rounded-md"
          :style="{ backgroundColor: card.changeBg, color: card.changeText }"
        >
          <v-icon :icon="card.changeIcon" /> {{ card.change }}
        </p>
        <p class="text-xs text-[#626F86]">{{ card.description }}</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.info-card {
  display: grid;
  gap: 1.25rem;
}

.info-card > div {
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.info-card > div:hover {
  transform: scale(1.05);
  box-shadow: 0px 10px 15px rgba(0, 0, 0, 0.1);
  cursor: pointer;
}

@media (min-width: 768px) {
  .info-card {
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  }
}
</style>
