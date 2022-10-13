<script setup>
import { ref } from "vue";
import Header from "~~/components/Header.vue";
import SpringCalculator from "~~/components/SpringCalculator.vue";
import MiterBevelCalculator from "~~/components/MiterBevelCalculator.vue";
</script>

<template>
  <div>
    <NuxtLayout name="default">
      <Header #header />

      <spring-calculator #hidden />

      <miter-bevel-calculator />
    </NuxtLayout>
  </div>
</template>
