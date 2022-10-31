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
    :class="[
      'flex',
      'w-screen',
      'h-screen',
      'items-center',
      'justify-center',
      'bg-gray-600',
      backgroundClasses,
    ]"
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
