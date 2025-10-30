<template>
  <UContainer>
    <div class="space-y-8">
      <!-- Header -->
      <div>
        <h1 class="text-3xl font-bold text-gray-900 dark:text-white mb-2">
          📝 記事 (Article)
        </h1>
        <p class="text-gray-600 dark:text-gray-300">
          ブログ記事やニュース記事の構造化データで、Googleニュースやリッチリザルトに最適化
        </p>
      </div>

      <!-- Interactive Demo -->
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
        <!-- Input Form -->
        <UCard>
          <template #header>
            <h2 class="text-xl font-bold text-gray-900 dark:text-white">
              記事情報を入力
            </h2>
          </template>

          <div class="space-y-4">
            <div>
              <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                記事タイトル
              </label>
              <UInput
                v-model="article.headline"
                placeholder="例: Nuxt 3の新機能完全ガイド"
                size="lg"
              />
              <p class="text-xs text-gray-500 dark:text-gray-400 mt-1">
                110文字以内推奨
              </p>
            </div>

            <div>
              <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                記事の説明
              </label>
              <UTextarea
                v-model="article.description"
                placeholder="記事の概要を入力..."
                :rows="3"
              />
            </div>

            <div>
              <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                著者名
              </label>
              <UInput
                v-model="article.authorName"
                placeholder="例: 山田太郎"
                size="lg"
              />
            </div>

            <div>
              <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                出版者名
              </label>
              <UInput
                v-model="article.publisherName"
                placeholder="例: Tech Blog"
                size="lg"
              />
            </div>

            <div class="grid grid-cols-2 gap-4">
              <div>
                <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                  公開日
                </label>
                <UInput
                  v-model="article.datePublished"
                  type="date"
                  size="lg"
                />
              </div>

              <div>
                <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                  更新日
                </label>
                <UInput
                  v-model="article.dateModified"
                  type="date"
                  size="lg"
                />
              </div>
            </div>

            <div>
              <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                記事タイプ
              </label>
              <USelect
                v-model="article.type"
                :options="articleTypes"
                size="lg"
              />
            </div>

            <div>
              <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                アイキャッチ画像URL
              </label>
              <UInput
                v-model="article.image"
                placeholder="https://example.com/article.jpg"
                size="lg"
              />
            </div>
          </div>
        </UCard>

        <!-- Preview -->
        <div class="space-y-6">
          <!-- Article Preview -->
          <UCard>
            <template #header>
              <h2 class="text-xl font-bold text-gray-900 dark:text-white">
                記事プレビュー
              </h2>
            </template>

            <article class="prose dark:prose-invert max-w-none">
              <h1 class="text-2xl font-bold text-gray-900 dark:text-white mb-2">
                {{ article.headline || '記事タイトル' }}
              </h1>

              <div class="flex items-center gap-4 text-sm text-gray-600 dark:text-gray-400 mb-4">
                <div class="flex items-center gap-2">
                  <div class="w-8 h-8 bg-primary-100 dark:bg-primary-900 rounded-full flex items-center justify-center">
                    <span class="text-primary-600 dark:text-primary-400">👤</span>
                  </div>
                  <span>{{ article.authorName || '著者名' }}</span>
                </div>
                <div>
                  公開: {{ article.datePublished || '2024-01-01' }}
                </div>
                <UBadge color="primary" variant="subtle">
                  {{ articleTypeLabels[article.type] }}
                </UBadge>
              </div>

              <div
                v-if="article.image"
                class="mb-4 rounded-lg overflow-hidden bg-gray-100 dark:bg-gray-800"
                style="aspect-ratio: 16/9;"
              >
                <div class="w-full h-full flex items-center justify-center text-gray-400">
                  🖼️ アイキャッチ画像
                </div>
              </div>

              <p class="text-gray-700 dark:text-gray-300">
                {{ article.description || '記事の説明がここに表示されます...' }}
              </p>

              <div class="mt-4 pt-4 border-t border-gray-200 dark:border-gray-700">
                <div class="flex items-center justify-between text-sm text-gray-600 dark:text-gray-400">
                  <span>📰 {{ article.publisherName || '出版者名' }}</span>
                  <span>更新: {{ article.dateModified || article.datePublished || '2024-01-01' }}</span>
                </div>
              </div>
            </article>
          </UCard>

          <!-- JSON-LD Code -->
          <UCard>
            <template #header>
              <h2 class="text-xl font-bold text-gray-900 dark:text-white">
                生成されるJSON-LD
              </h2>
            </template>

            <pre class="p-4 bg-gray-900 text-gray-100 rounded-lg overflow-x-auto text-sm">{{ formattedJsonLd }}</pre>

            <template #footer>
              <div class="flex gap-2">
                <UButton
                  color="primary"
                  variant="soft"
                  icon="i-heroicons-clipboard-document"
                  @click="copyToClipboard"
                >
                  コピー
                </UButton>
                <UButton
                  color="gray"
                  variant="soft"
                  icon="i-heroicons-arrow-path"
                  @click="resetForm"
                >
                  リセット
                </UButton>
              </div>
            </template>
          </UCard>
        </div>
      </div>

      <!-- Explanation -->
      <UCard>
        <template #header>
          <h2 class="text-xl font-bold text-gray-900 dark:text-white">
            記事タイプの違い
          </h2>
        </template>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
          <div class="p-4 border border-gray-200 dark:border-gray-700 rounded-lg">
            <h3 class="font-semibold text-gray-900 dark:text-white mb-2">
              Article
            </h3>
            <p class="text-sm text-gray-600 dark:text-gray-400">
              一般的な記事。ブログ投稿、解説記事など。
            </p>
          </div>

          <div class="p-4 border border-gray-200 dark:border-gray-700 rounded-lg">
            <h3 class="font-semibold text-gray-900 dark:text-white mb-2">
              BlogPosting
            </h3>
            <p class="text-sm text-gray-600 dark:text-gray-400">
              ブログ記事。個人ブログや企業ブログの投稿。
            </p>
          </div>

          <div class="p-4 border border-gray-200 dark:border-gray-700 rounded-lg">
            <h3 class="font-semibold text-gray-900 dark:text-white mb-2">
              NewsArticle
            </h3>
            <p class="text-sm text-gray-600 dark:text-gray-400">
              ニュース記事。報道記事、最新ニュース。Googleニュースに最適。
            </p>
          </div>
        </div>
      </UCard>

      <!-- Best Practices -->
      <UCard>
        <template #header>
          <h2 class="text-xl font-bold text-gray-900 dark:text-white">
            ベストプラクティス
          </h2>
        </template>

        <div class="space-y-4">
          <div class="flex items-start gap-3">
            <div class="text-xl">✅</div>
            <div>
              <h3 class="font-semibold text-gray-900 dark:text-white">
                タイトルは110文字以内
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                検索結果で完全に表示されるため
              </p>
            </div>
          </div>

          <div class="flex items-start gap-3">
            <div class="text-xl">✅</div>
            <div>
              <h3 class="font-semibold text-gray-900 dark:text-white">
                publisher（出版者）は必須
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                Googleはこれがないとエラーとして扱う
              </p>
            </div>
          </div>

          <div class="flex items-start gap-3">
            <div class="text-xl">✅</div>
            <div>
              <h3 class="font-semibold text-gray-900 dark:text-white">
                画像は高解像度（最低1200px）
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                Discover、Googleニュースで使用される
              </p>
            </div>
          </div>

          <div class="flex items-start gap-3">
            <div class="text-xl">✅</div>
            <div>
              <h3 class="font-semibold text-gray-900 dark:text-white">
                dateModifiedは正確に
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                内容を変更した場合は必ず更新する
              </p>
            </div>
          </div>
        </div>
      </UCard>
    </div>
  </UContainer>
</template>

<script setup lang="ts">
const today = new Date().toISOString().split('T')[0]

const article = ref({
  headline: 'Nuxt 3とJSON-LDで作るSEO最適化されたWebサイト',
  description: 'Nuxt 3の最新機能を活用して、構造化データを実装し、検索エンジン最適化を実現する方法を詳しく解説します。',
  authorName: '山田太郎',
  publisherName: 'Tech Blog',
  datePublished: today,
  dateModified: today,
  type: 'BlogPosting',
  image: 'https://example.com/article-image.jpg'
})

const articleTypes = [
  { label: 'Article（一般記事）', value: 'Article' },
  { label: 'BlogPosting（ブログ記事）', value: 'BlogPosting' },
  { label: 'NewsArticle（ニュース記事）', value: 'NewsArticle' }
]

const articleTypeLabels: Record<string, string> = {
  Article: 'Article',
  BlogPosting: 'Blog',
  NewsArticle: 'News'
}

const jsonLd = computed(() => ({
  '@context': 'https://schema.org',
  '@type': article.value.type,
  'headline': article.value.headline,
  'image': article.value.image,
  'datePublished': article.value.datePublished,
  'dateModified': article.value.dateModified,
  'author': {
    '@type': 'Person',
    'name': article.value.authorName
  },
  'publisher': {
    '@type': 'Organization',
    'name': article.value.publisherName,
    'logo': {
      '@type': 'ImageObject',
      'url': 'https://example.com/logo.png'
    }
  },
  'description': article.value.description
}))

const formattedJsonLd = computed(() => JSON.stringify(jsonLd.value, null, 2))

// 実際のJSON-LDをページに追加
useHead({
  title: article.value.headline,
  meta: [
    {
      name: 'description',
      content: article.value.description
    }
  ],
  script: [
    {
      type: 'application/ld+json',
      innerHTML: () => JSON.stringify(jsonLd.value)
    }
  ]
})

const copyToClipboard = async () => {
  await navigator.clipboard.writeText(formattedJsonLd.value)
}

const resetForm = () => {
  article.value = {
    headline: 'Nuxt 3とJSON-LDで作るSEO最適化されたWebサイト',
    description: 'Nuxt 3の最新機能を活用して、構造化データを実装し、検索エンジン最適化を実現する方法を詳しく解説します。',
    authorName: '山田太郎',
    publisherName: 'Tech Blog',
    datePublished: today,
    dateModified: today,
    type: 'BlogPosting',
    image: 'https://example.com/article-image.jpg'
  }
}
</script>
