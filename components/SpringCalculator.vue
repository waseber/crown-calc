<script setup lang="ts">
import { defineEmits } from "vue";
// Spring Logic
const sideA = ref(0);
const sideB = ref(0);
let springOutput = ref(null);

function springCalculator() {
  const tan = Math.atan(sideA.value / sideB.value);
  const tanDeg = (tan * 180) / Math.PI;
  springOutput.value = tanDeg.toFixed(2);
}

// emit toggle
const emitToggle = defineEmits(["toggleSpring"]);
</script>

<template>
  <div class="m-10 p-5 bg-gray-400 bg-opacity-60 rounded-xl">
    <div class="flex justify-between">
      <h2 class="text-xl text-white">Spring Calculator</h2>
      <button
        class="-mt-10 -mr-3 text-4xl text-white"
        @click.prevent="emitToggle('toggle-spring')"
      >
        &times;
      </button>
    </div>
    <h4 class="italic text-white">It's trigonometry, stupid!</h4>
    <form class="mt-5 flex">
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
    <p v-if="sideA > 0 && sideB > 0" class="text-white">
      Spring: {{ springOutput }}&#176;
    </p>
  </div>
</template>
