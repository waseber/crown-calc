<script setup>
const props = defineProps({
  background: { type: String },
});

// Computed
const backgroundClasses = computed(() => {
  if (props.background) return ["bg-no-repeat", "bg-center", "bg-cover"];
});
</script>

<template>
  <div
    :style="background ? `background-image: ${background}` : ''"
    :class="['min-w-full', 'min-h-screen', 'bg-gray-300', backgroundClasses]"
  >
    <div class="mx-auto bg-gray-900 bg-opacity-70">
      <header>
        <slot name="header" />
      </header>
      <main>
        <slot />
      </main>
      <aside>
        <slot name="aside" />
      </aside>
    </div>
  </div>
</template>
