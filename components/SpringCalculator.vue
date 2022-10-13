<script setup>
// Spring Logic
const sideA = ref(0);
const sideB = ref(0);
let springOutput = ref(null);

function springCalculator() {
  const tan = Math.atan(parseFloat(sideA.value) / parseFloat(sideB.value));
  const tanDeg = (tan * 180) / Math.PI;
  springOutput.value = tanDeg.toFixed(2);
}
</script>

<template>
  <div>
    <h2>Spring Calculator</h2>
    <h4>It's trigonometry, stupid!</h4>
    <form>
      <label for="sideA">
        Height Along the Wall:
        <input
          type="text"
          name="sideA"
          id="sideA"
          v-model="sideA"
          @input="springCalculator"
        />
      </label>

      <label for="sideB">
        Depth Along the Ceiling:
        <input
          type="text"
          name="sideA"
          id="sideB"
          v-model="sideB"
          @input="springCalculator"
        />
      </label>
    </form>
    Spring: {{ springOutput }}&#176;
  </div>
</template>
