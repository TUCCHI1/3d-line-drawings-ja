<template>
  <div class="min-h-screen">
    <UContainer class="py-12">
      <UButton to="/" icon="i-heroicons-arrow-left" class="mb-6">
        Back to Home
      </UButton>

      <div class="grid lg:grid-cols-2 gap-8">
        <div>
          <h1 class="text-3xl font-bold mb-6">{{ article.headline }}</h1>

          <UCard>
            <div class="space-y-4">
              <img
                :src="article.image"
                :alt="article.headline"
                class="w-full rounded-lg"
              >

              <div class="flex items-center gap-2">
                <UAvatar
                  :alt="article.author.name"
                  size="sm"
                />
                <div>
                  <p class="font-semibold text-sm">{{ article.author.name }}</p>
                  <p class="text-xs text-gray-500">{{ formatDate(article.datePublished) }}</p>
                </div>
              </div>

              <USeparator />

              <p class="text-gray-700 dark:text-gray-300">
                {{ article.description }}
              </p>

              <div class="flex gap-2">
                <UBadge
                  v-for="keyword in article.keywords.split(', ')"
                  :key="keyword"
                  variant="subtle"
                >
                  {{ keyword }}
                </UBadge>
              </div>
            </div>
          </UCard>
        </div>

        <div>
          <h2 class="text-2xl font-bold mb-4">JSON-LD Code</h2>
          <UCard>
            <pre class="text-xs overflow-x-auto"><code>{{ JSON.stringify(jsonLd, null, 2) }}</code></pre>
          </UCard>

          <UAlert
            color="primary"
            variant="subtle"
            title="Article Schema"
            description="Googleの検索結果で記事のヘッドライン、画像、公開日が表示されます。"
            class="mt-4"
          />
        </div>
      </div>
    </UContainer>
  </div>
</template>

<script setup lang="ts">
const article = {
  '@type': 'Article',
  headline: 'Nuxt 4.2の新機能とJSON-LD実装ガイド',
  image: 'https://picsum.photos/800/400',
  datePublished: '2025-10-31T09:00:00+09:00',
  dateModified: '2025-10-31T12:00:00+09:00',
  author: {
    '@type': 'Person',
    name: '佐藤花子'
  },
  publisher: {
    '@type': 'Organization',
    name: 'Tech Blog',
    logo: {
      '@type': 'ImageObject',
      url: 'https://example.com/logo.png'
    }
  },
  description: 'Nuxt 4.2でJSON-LD構造化データを実装する方法を詳しく解説します。SEO最適化とリッチリザルト表示のベストプラクティスを学びましょう。',
  keywords: 'Nuxt, JSON-LD, SEO, 構造化データ'
}

const jsonLd = {
  '@context': 'https://schema.org',
  ...article
}

const formatDate = (dateString: string) => {
  return new Date(dateString).toLocaleDateString('ja-JP', {
    year: 'numeric',
    month: 'long',
    day: 'numeric'
  })
}

useHead({
  title: 'Article Schema',
  script: [
    {
      type: 'application/ld+json',
      innerHTML: JSON.stringify(jsonLd)
    }
  ]
})
</script>
