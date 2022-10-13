<script setup>
import { ref } from "vue";
import Header from "~~/components/Header.vue";
import SpringCalculator from "~~/components/SpringCalculator.vue";
import MiterBevelCalculator from "~~/components/MiterBevelCalculator.vue";

const toggleSpring = ref(false);
</script>

<template>
  <div>
    <NuxtLayout name="default">
      <Header #header />

      <spring-calculator v-if="toggleSpring" #aside />

      <miter-bevel-calculator @toggle-spring="toggleSpring = true" />
    </NuxtLayout>
  </div>
</template>
