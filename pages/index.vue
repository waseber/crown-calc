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

    <template v-if="toggleSpring" #aside>
      <spring-calculator @toggle-spring="toggleSpring = false" />
    </template>

    <miter-bevel-calculator @toggle-spring="toggleSpring = !toggleSpring" />
  </NuxtLayout>
</template>
