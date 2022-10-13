<template>
  <div>
    <header>
      <slot name="header" />
    </header>
    <slot name="hidden" />
    <main>
      <slot />
    </main>
  </div>
</template>
