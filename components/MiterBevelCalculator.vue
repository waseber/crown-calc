<script setup lang="ts">
import { defineEmits, watch } from "vue";

// Miter and Bevel
//// vars
enum springOptionsValue {
  DEFAULT = 0,
  FIRST = 38,
  SECOND = 45,
  CUSTOM = 1,
}

enum springOptionsText {
  DEFAULT = "Common Springs",
  FIRST = "38/52",
  SECOND = "45/45",
  CUSTOM = "Custom",
}

const springOptions = reactive([
  {
    text: springOptionsText.DEFAULT,
    value: springOptionsValue.DEFAULT,
  },
  {
    text: springOptionsText.FIRST,
    value: springOptionsValue.FIRST,
  },
  {
    text: springOptionsText.SECOND,
    value: springOptionsValue.SECOND,
  },
  {
    text: springOptionsText.CUSTOM,
    value: springOptionsValue.CUSTOM,
  },
]);

const wall = ref(0);
const spring = ref(0);
const showSpringText = ref(false);
let miterOutput = ref(null);
let bevelOutput = ref(null);

// Computed
const showResults = computed(() => wall.value > 0 && spring.value > 0);

// watch spring options
watch(spring, (currentVal, oldVal) => {
  if (currentVal === 1) {
    showSpringText.value = true;
  }
});

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
  <div class="m-5 p-5 bg-gray-400 bg-opacity-60 rounded-xl text-white">
    <h2 class="text-xl">Miter and Bevel</h2>
    <h4 class="italic">
      This method assumes you are laying the crown molding flat with the top of
      the molding against the fence.
    </h4>

    <div class="mt-5 flex">
      <label for="wall" class="mr-4 flex flex-col">
        <span>Wall Angle:</span>
        <input
          type="text"
          name="wall"
          id="wall"
          class="my-2 p-2 border-solid border-2 rounded-lg border-gray-800 text-black"
          v-model="wall"
          @input="miterAndBevelCalculator"
        />
      </label>

      <label for="spring" class="flex flex-col">
        <span>Spring:</span>
        <select
          v-model="spring"
          class="my-2 p-2 border-solid border-2 rounded-lg border-gray-800 text-black"
        >
          <option
            v-for="(option, idx) in springOptions"
            :value="option.value"
            :key="idx"
          >
            {{ option.text }}
          </option>
        </select>
        <input
          v-show="showSpringText"
          type="text"
          name="spring"
          id="spring"
          class="my-2 p-2 border-solid border-2 rounded-lg border-gray-800 text-black"
          v-model="spring"
          @input="miterAndBevelCalculator"
        />
      </label>
      <button
        class="ml-4 underline"
        @click.prevent="emitToggle('toggle-spring')"
      >
        Need help finding the spring?
      </button>
    </div>

    <p v-if="showResults">
      Miter Angle: {{ miterOutput }}&#176; Bevel Angle: {{ bevelOutput }}&#176;
    </p>
  </div>
</template>
