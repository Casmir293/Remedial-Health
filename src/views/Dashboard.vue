<script setup lang="ts">
import HeaderComp from "@/components/HeaderComp.vue";
import NavComp from "@/components/dashboard/NavComp.vue";
import TitleComp from "@/components/dashboard/TitleComp.vue";
import InfoCard from "@/components/dashboard/InfoCard.vue";
import ChartCard from "@/components/dashboard/ChartCard.vue";
import SummaryCard from "@/components/dashboard/SummaryCard.vue";
</script>

<template>
  <header-comp />

  <section class="hidden lg:block">
    <nav-comp />
  </section>

  <title-comp />

  <main>
    <section>
      <info-card />
      <br />
      <chart-card />
    </section>
    <summary-card />
  </main>
</template>

<style scoped>
main {
  padding: 0 20px 20px 40px;
  gap: 1.25rem;
  display: grid;
}

@media (min-width: 768px) {
  main {
    grid-template-columns: 50% 50%;
    align-items: start;
  }
}

@media (min-width: 1024px) {
  main {
    grid-template-columns: 70% 30%;
  }
}
</style>
