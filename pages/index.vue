<script setup>
import { ref } from "vue";
import Header from "~~/components/Header.vue";
import SpringCalculator from "~~/components/SpringCalculator.vue";
import MiterBevelCalculator from "~~/components/MiterBevelCalculator.vue";

const toggleSpring = ref(false);
</script>

<template>
  <NuxtLayout background="url(../assets/img/saw.jpg)">
    <template #header>
      <Header />
    </template>

    <template #aside>
      <spring-calculator v-if="toggleSpring" />
    </template>

    <miter-bevel-calculator @toggle-spring="toggleSpring = true" />
  </NuxtLayout>
</template>
