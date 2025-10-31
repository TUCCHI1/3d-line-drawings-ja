<template>
  <div class="min-h-screen">
    <UContainer class="py-12">
      <div class="text-center mb-12">
        <h1 class="text-4xl font-bold mb-4">JSON-LD Structured Data Demo</h1>
        <p class="text-xl text-gray-600 dark:text-gray-400">
          Nuxt 4.2 + Nuxt UI + JSON-LD Examples
        </p>
      </div>

      <UCard class="mb-8 bg-gradient-to-r from-blue-50 to-purple-50 dark:from-blue-950 dark:to-purple-950 border-2 border-blue-200 dark:border-blue-800">
        <div class="flex items-start gap-4">
          <div class="text-4xl">💡</div>
          <div class="flex-1">
            <h2 class="text-2xl font-bold mb-2">リッチスニペットとは？</h2>
            <p class="text-gray-700 dark:text-gray-300 mb-4">
              JSON-LDを使うと、検索結果に価格・評価・日時などの追加情報が表示されます。詳しく学びましょう！
            </p>
            <NuxtLink to="/rich-snippets">
              <UButton color="primary" size="lg" trailing-icon="i-heroicons-arrow-right">
                リッチスニペットを学ぶ
              </UButton>
            </NuxtLink>
          </div>
        </div>
      </UCard>

      <h2 class="text-2xl font-bold mb-6">JSON-LD デモ一覧</h2>

      <div class="grid gap-6 md:grid-cols-2 lg:grid-cols-3">
        <UCard
          v-for="example in examples"
          :key="example.path"
          class="hover:shadow-lg transition-shadow"
        >
          <template #header>
            <h3 class="text-xl font-semibold">{{ example.title }}</h3>
          </template>

          <p class="text-gray-600 dark:text-gray-400 mb-4">
            {{ example.description }}
          </p>

          <UBadge color="primary" variant="subtle">
            @type: {{ example.type }}
          </UBadge>

          <template #footer>
            <NuxtLink :to="example.path">
              <UButton color="primary" block>
                View Example
              </UButton>
            </NuxtLink>
          </template>
        </UCard>
      </div>

      <USeparator class="my-12" />

      <div class="prose dark:prose-invert max-w-none">
        <h2>JSON-LD (@type) とは？</h2>
        <p>
          <strong>JSON-LD</strong>は「JSON for Linking Data」の略で、
          構造化データをJSON形式で記述するフォーマットです。
        </p>
        <ul>
          <li><code>@type</code>: Schema.orgで定義されたデータ型を指定（Person, Article, Productなど）</li>
          <li><code>@context</code>: 通常は "https://schema.org" を指定</li>
          <li><strong>用途</strong>: SEO最適化、検索エンジンのリッチリザルト表示</li>
        </ul>
      </div>
    </UContainer>
  </div>
</template>

<script setup lang="ts">
useHead({
  title: 'Home'
})

const examples = [
  {
    title: 'Person',
    type: 'Person',
    description: '個人プロフィール情報を構造化データとして表現',
    path: '/person'
  },
  {
    title: 'Article',
    type: 'Article',
    description: 'ブログ記事やニュース記事のメタデータを表現',
    path: '/article'
  },
  {
    title: 'Product',
    type: 'Product',
    description: '商品情報、価格、在庫状況などを表現',
    path: '/product'
  },
  {
    title: 'Organization',
    type: 'Organization',
    description: '企業や組織の情報を構造化',
    path: '/organization'
  },
  {
    title: 'Recipe',
    type: 'Recipe',
    description: 'レシピの材料、手順、調理時間などを表現',
    path: '/recipe'
  },
  {
    title: 'Event',
    type: 'Event',
    description: 'イベント情報、開催日時、場所などを表現',
    path: '/event'
  }
]
</script>
