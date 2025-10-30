<template>
  <div class="min-h-screen bg-gray-50 dark:bg-gray-900">
    <!-- Header -->
    <UContainer>
      <header class="py-6">
        <nav class="flex items-center justify-between">
          <NuxtLink to="/" class="flex items-center gap-3">
            <div class="text-3xl">🔍</div>
            <div>
              <h1 class="text-xl font-bold text-gray-900 dark:text-white">
                JSON-LD Demo
              </h1>
              <p class="text-xs text-gray-500 dark:text-gray-400">
                構造化データの実践ガイド
              </p>
            </div>
          </NuxtLink>

          <div class="flex items-center gap-4">
            <UButton
              color="gray"
              variant="ghost"
              icon="i-heroicons-moon"
              @click="toggleDarkMode"
            />
          </div>
        </nav>
      </header>
    </UContainer>

    <!-- Navigation Tabs -->
    <UContainer>
      <div class="border-b border-gray-200 dark:border-gray-700">
        <nav class="flex gap-4 overflow-x-auto">
          <NuxtLink
            v-for="link in navigation"
            :key="link.to"
            :to="link.to"
            class="px-4 py-3 text-sm font-medium whitespace-nowrap border-b-2 transition-colors"
            :class="isActive(link.to)
              ? 'border-primary-500 text-primary-600 dark:text-primary-400'
              : 'border-transparent text-gray-600 dark:text-gray-400 hover:text-gray-900 dark:hover:text-gray-200 hover:border-gray-300 dark:hover:border-gray-600'"
          >
            <span class="mr-2">{{ link.icon }}</span>
            {{ link.label }}
          </NuxtLink>
        </nav>
      </div>
    </UContainer>

    <!-- Main Content -->
    <main class="py-8">
      <slot />
    </main>

    <!-- Footer -->
    <UContainer>
      <footer class="py-8 border-t border-gray-200 dark:border-gray-700">
        <div class="text-center text-sm text-gray-600 dark:text-gray-400">
          <p>Nuxt × Nuxt UI で作る application/ld+json デモ</p>
          <p class="mt-2">
            <a
              href="https://schema.org"
              target="_blank"
              class="text-primary-600 dark:text-primary-400 hover:underline"
            >
              Schema.org
            </a>
            の仕様に準拠
          </p>
        </div>
      </footer>
    </UContainer>
  </div>
</template>

<script setup lang="ts">
const route = useRoute()
const colorMode = useColorMode()

const navigation = [
  { to: '/', label: 'ホーム', icon: '🏠' },
  { to: '/product', label: '商品', icon: '🛍️' },
  { to: '/article', label: '記事', icon: '📝' },
  { to: '/restaurant', label: 'レストラン', icon: '🍽️' },
  { to: '/event', label: 'イベント', icon: '🎫' },
]

const isActive = (path: string) => {
  if (path === '/') {
    return route.path === '/'
  }
  return route.path.startsWith(path)
}

const toggleDarkMode = () => {
  colorMode.preference = colorMode.value === 'dark' ? 'light' : 'dark'
}
</script>
