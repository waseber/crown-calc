<template>
  <div>
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
