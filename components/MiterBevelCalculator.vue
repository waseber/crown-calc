<script setup lang="ts">
import { defineEmits } from "vue";

// Miter and Bevel
//// vars
const wall = ref(0);
const spring = ref(0);
let miterOutput = ref(null);
let bevelOutput = ref(null);

// Computed
const showResults = computed(() => wall.value > 0 && spring.value > 0);

// methods
function miterAndBevelCalculator() {
  const angle_rad1 = wall.value * ((2 * Math.PI) / 360);
  const angle_rad2 = spring.value * ((2 * Math.PI) / 360);
  const miter =
    Math.atan(Math.sin(angle_rad2) / Math.tan(angle_rad1 / 2)) /
    ((2 * Math.PI) / 360);
  const bevel =
    Math.asin(Math.cos(angle_rad2) * Math.cos(angle_rad1 / 2)) /
    ((2 * Math.PI) / 360);
  const angle_rev = 90 - bevel;
  miterOutput.value = miter.toFixed(2);
  bevelOutput.value = bevel.toFixed(2);
}

// emit toggle
const emitToggle = defineEmits(["toggleSpring"]);
</script>

<template>
  <div>
    <h2>Miter and Bevel</h2>
    <h4>
      This method assumes you are laying the crown molding flat with the top of
      the molding against the fence.
    </h4>

    <label for="wall">
      Wall Angle:
      <input
        type="text"
        name="wall"
        id="wall"
        v-model="wall"
        @input="miterAndBevelCalculator"
      />
    </label>

    <label for="spring">
      Spring:
      <input
        type="text"
        name="spring"
        id="spring"
        v-model="spring"
        @input="miterAndBevelCalculator"
      />
    </label>
    <button @click.prevent="emitToggle('toggle-spring')">
      Need help finding the spring?
    </button>
    <p v-if="showResults">
      Miter Angle: {{ miterOutput }}&#176; Bevel Angle: {{ bevelOutput }}&#176;
    </p>
  </div>
</template>
