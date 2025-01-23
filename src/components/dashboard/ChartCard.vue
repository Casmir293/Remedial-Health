<script setup lang="ts">
import { reactive } from "vue";

// Shelf Life
const shelfLifeData = reactive({
  series: [85, 45],
  chartOptions: {
    chart: {
      height: 350,
      type: "radialBar",
    },
    plotOptions: {
      radialBar: {
        dataLabels: {
          name: {
            fontSize: "22px",
          },
          value: {
            fontSize: "16px",
          },
        },
      },
    },
    legend: {
      show: true,
      position: "bottom",
    },
    fill: {
      colors: ["#0C66E4", "#A3F94E"],
    },
    labels: ["Less than 16 months", "More than 18 months"],
  },
});

// Storage Space
const storageSpaceData = reactive({
  series: [70],
  chartOptions: {
    chart: {
      height: 350,
      type: "radialBar",
    },
    plotOptions: {
      radialBar: {
        hollow: {
          size: "70%",
        },
      },
    },
    fill: {
      colors: ["#0C66E4"],
    },
    labels: ["Used Space"],
  },
});
</script>

<template>
  <div class="chart-card">
    <!-- Shelf Life -->
    <div class="rounded-lg border p-5">
      <p class="text-[#172B4D] font-medium text-lg">Shelf Life Analysis</p>
      <p class="text-xs text-[#626F86]">
        Ratio of received products with expiry less than 18 months
      </p>

      <div class="flex items-center justify-center">
        <div id="chart">
          <apexchart
            type="radialBar"
            height="auto"
            :options="shelfLifeData.chartOptions"
            :series="shelfLifeData.series"
          ></apexchart>
        </div>
      </div>
    </div>

    <!-- Storage Space -->
    <div class="rounded-lg border p-5">
      <p class="text-[#172B4D] font-medium text-lg">Storage Space</p>
      <p class="text-xs text-[#626F86]">Ratio of used vs free storage space</p>

      <div class="flex items-center justify-center">
        <div id="chart">
          <apexchart
            type="radialBar"
            height="auto"
            :options="storageSpaceData.chartOptions"
            :series="storageSpaceData.series"
          ></apexchart>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.chart-card {
  display: grid;
  gap: 1.25rem;
}

@media (min-width: 768px) {
  .chart-card {
    grid-template-columns: repeat(auto-fill, minmax(100%, 1fr));
  }
}

@media (min-width: 1024px) {
  .chart-card {
    grid-template-columns: repeat(auto-fill, minmax(450px, 1fr));
  }
}
</style>
