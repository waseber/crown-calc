<script setup lang="ts">
// Spring Logic
const sideA = ref(0);
const sideB = ref(0);
let springOutput = ref(null);

function springCalculator() {
  const tan = Math.atan(sideA.value / sideB.value);
  const tanDeg = (tan * 180) / Math.PI;
  springOutput.value = tanDeg.toFixed(2);
}
</script>

<template>
  <div class="p-5">
    <h2 class="text-xl text-white">Spring Calculator</h2>
    <h4 class="italic text-white">It's trigonometry, stupid!</h4>
    <form class="flex">
      <label for="sideA" class="mr-4">
        <div class="text-white">Height Along the Wall:</div>
        <input
          type="text"
          name="sideA"
          id="sideA"
          class="my-2 p-2 border-solid border-2 rounded-lg border-gray-800 text-black"
          v-model="sideA"
          @input="springCalculator"
        />
      </label>

      <label for="sideB">
        <div class="text-white">Depth Along the Ceiling:</div>
        <input
          type="text"
          name="sideA"
          id="sideB"
          class="my-2 p-2 border-solid border-2 rounded-lg border-gray-800 text-black"
          v-model="sideB"
          @input="springCalculator"
        />
      </label>
    </form>
    <p class="text-white">Spring: {{ springOutput }}&#176;</p>
  </div>
</template>
