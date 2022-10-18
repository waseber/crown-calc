<template>
  <div class="container mx-auto">
    <header>
      <slot name="header" />
    </header>
    <aside>
      <slot name="aside" />
    </aside>
    <main>
      <slot />
    </main>
  </div>
</template>
