<template>
  <div class="min-h-screen flex flex-col">
    <AppHeader class="relative z-30 w-full" />
    <main class="flex-grow relative z-10">
      <slot />
    </main>
    <AppFooter class="relative z-10 bg-dark" />
  </div>
</template>