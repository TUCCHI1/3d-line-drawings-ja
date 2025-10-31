<template>
  <UApp>
    <NuxtLayout>
      <NuxtPage :key="$route.fullPath" />
    </NuxtLayout>
  </UApp>
</template>

<script setup lang="ts">
// Global meta tags and SEO setup
useHead({
  titleTemplate: '%s - JSON-LD Demo App',
  meta: [
    { name: 'description', content: 'Nuxt 4.2 + Nuxt UI app demonstrating JSON-LD structured data' }
  ]
})
</script>
