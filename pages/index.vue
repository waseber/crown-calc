<script setup>
import { ref } from "vue";
import SpringCalculator from "~~/components/SpringCalculator.vue";
import MiterBevelCalculator from "~~/components/MiterBevelCalculator.vue";

definePageMeta({
  layout: "default",
});
</script>

<template>
  <NuxtLayout name="default">
    <header>
      <h1>Crown Molding Angles Calculator</h1>
    </header>

    <spring-calculator #hidden />

    <miter-bevel-calculator #main />
  </NuxtLayout>
</template>
