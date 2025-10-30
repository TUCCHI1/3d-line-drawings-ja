<template>
  <div class="min-h-screen bg-gradient-to-br from-blue-50 via-purple-50 to-pink-50 dark:from-gray-900 dark:via-purple-950 dark:to-blue-950">
    <!-- Header -->
    <UContainer>
      <header class="py-6">
        <nav class="flex items-center justify-between">
          <NuxtLink to="/" class="flex items-center gap-3 group">
            <div class="text-4xl transform group-hover:scale-110 transition-transform">✨</div>
            <div>
              <h1 class="text-2xl font-bold bg-gradient-to-r from-blue-600 to-purple-600 dark:from-blue-400 dark:to-purple-400 bg-clip-text text-transparent">
                Rich Results
              </h1>
              <p class="text-xs text-gray-600 dark:text-gray-400">
                Googleリッチリザルト完全ガイド
              </p>
            </div>
          </NuxtLink>

          <UButton
            color="gray"
            variant="ghost"
            icon="i-heroicons-moon"
            @click="toggleDarkMode"
          />
        </nav>
      </header>
    </UContainer>

    <!-- Navigation Tabs -->
    <UContainer>
      <div class="bg-white/50 dark:bg-gray-800/50 backdrop-blur-sm rounded-xl p-2 mb-6">
        <nav class="flex gap-2 overflow-x-auto">
          <NuxtLink
            v-for="link in navigation"
            :key="link.to"
            :to="link.to"
            class="px-4 py-2 text-sm font-medium whitespace-nowrap rounded-lg transition-all"
            :class="isActive(link.to)
              ? 'bg-gradient-to-r from-blue-500 to-purple-500 text-white shadow-lg transform scale-105'
              : 'text-gray-700 dark:text-gray-300 hover:bg-white/70 dark:hover:bg-gray-700/70'"
          >
            <span class="mr-2">{{ link.icon }}</span>
            {{ link.label }}
          </NuxtLink>
        </nav>
      </div>
    </UContainer>

    <!-- Main Content -->
    <main class="pb-12">
      <slot />
    </main>

    <!-- Footer -->
    <UContainer>
      <footer class="py-8 border-t border-gray-200/50 dark:border-gray-700/50">
        <div class="text-center text-sm text-gray-600 dark:text-gray-400">
          <p class="font-semibold mb-2">Googleリッチリザルトで検索結果を輝かせよう ✨</p>
          <p>Nuxt 3 × Nuxt UI で作成</p>
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
  { to: '/recipe', label: 'レシピ', icon: '🍳' },
  { to: '/faq', label: 'FAQ', icon: '❓' },
  { to: '/comparison', label: '比較表', icon: '📊' },
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
