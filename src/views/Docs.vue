<script setup lang="ts">
const techStackFrontend = [
  { name: "Vue.js", description: "The Progressive JavaScript Framework." },
  {
    name: "Vuetify",
    description:
      "A Material Design component framework used for building a clean and accessible UI.",
  },
  {
    name: "TypeScript",
    description:
      "Ensures type safety and enhanced code quality throughout the project.",
  },
  {
    name: "Tailwind CSS",
    description:
      "A utility-first CSS framework used for responsive and customizable designs.",
  },
  {
    name: "Apex Chart",
    description:
      "A free and open-source modern charting library that helps developers create beautiful and interactive visualizations.",
  },
];

const techStackBackend = [
  {
    name: "PHP",
    description:
      "A popular general-purpose scripting language that is especially suited to web development.",
  },
];

const resultLinks = [
  { label: "Live URL", url: "https://remedial-health.vercel.app" },
  { label: "Source Code", url: "https://github.com/Casmir293/Remedial-Health" },
  {
    label: "HackerRank DSA Challenge",
    url: "https://www.hackerrank.com/contests/full-stack-laravel-remedial-health/leaderboard",
    note: "casmir293",
  },
];
</script>

<template>
  <div class="bg-gray-100 min-h-screen p-8">
    <div class="max-w-4xl mx-auto bg-white rounded-lg shadow-lg p-6">
      <h1 class="text-2xl font-bold mb-4 text-center">
        Remedial Health Test Documentation
      </h1>

      <section class="mb-6">
        <h2 class="text-xl font-semibold mb-2">Overview</h2>
        <p>
          This is a test task for the Fullstack Developer role (Vue.js/Laravel)
          at
          <a
            href="https://remedial.health"
            target="_blank"
            class="text-blue-600 underline"
            >Remedial Health</a
          >. Candidates were required to build a static user interface of the
          provided
          <a
            href="https://www.figma.com/design/bL4ZubJevMu2sLIsgBcMm0/Test-Work?node-id=0-1&p=f&t=H38Aa825Qq3Mt3Je-0"
            target="_blank"
            class="text-blue-600 underline"
            >Figma Design</a
          >
          and also participate in a
          <a
            href="https://www.hackerrank.com/full-stack-laravel-remedial-health"
            target="_blank"
            class="text-blue-600 underline"
            >HackerRank Data Structures and Algorithms challenge</a
          >.
        </p>
      </section>

      <section class="mb-6">
        <h2 class="text-xl font-semibold mb-2">
          Duration <small>- [4 days]</small>
        </h2>
        <p>Wednesday, Jan 22nd, 2025 - Sunday, Jan 26th, 2025.</p>
      </section>

      <section class="mb-6">
        <h2 class="text-xl font-semibold mb-2">Result</h2>
        <ul class="list-disc list-inside space-y-2">
          <li v-for="link in resultLinks" :key="link.label">
            <strong>{{ link.label }}: </strong>
            <span v-if="link.note">
              - Username is <b>{{ link.note }}</b> &nbsp;</span
            >
            <a
              :href="link.url"
              target="_blank"
              class="text-blue-600 underline"
              >{{ link.url }}</a
            >
          </li>
        </ul>
      </section>

      <section class="mb-6">
        <h2 class="text-xl font-semibold mb-2">Tech Stack</h2>

        <div class="mb-4">
          <h3 class="font-semibold mb-2">Frontend Task</h3>
          <ul class="list-disc list-inside space-y-1">
            <li v-for="tech in techStackFrontend" :key="tech.name">
              <strong>{{ tech.name }}:</strong> {{ tech.description }}
            </li>
          </ul>
        </div>

        <div>
          <h3 class="font-semibold mb-2">HackerRank DSA Challenge</h3>
          <ul class="list-disc list-inside">
            <li v-for="tech in techStackBackend" :key="tech.name">
              <strong>{{ tech.name }}:</strong> {{ tech.description }}
            </li>
          </ul>
        </div>
      </section>
    </div>
  </div>
</template>

<style scoped>
a {
  transition: color 1.5s ease;
}

a:hover {
  color: #1e40af96;
}
</style>
