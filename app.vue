<template>
  <div class="mx-auto max-w-4xl p-4 dark:bg-gray-900">
    <Layout /> <!-- Transform to NuxtLayout after fixing SSR bug, which causes hydration issues -->
    <main>
      <NuxtPage />
    </main>
    <hr>
  </div>
</template>