<template>
  <UContainer>
    <div class="space-y-8">
      <!-- Header -->
      <div>
        <h1 class="text-3xl font-bold text-gray-900 dark:text-white mb-2">
          🛍️ 商品 (Product)
        </h1>
        <p class="text-gray-600 dark:text-gray-300">
          商品情報を構造化して、検索結果に価格・評価・在庫状況を表示
        </p>
      </div>

      <!-- Interactive Demo -->
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
        <!-- Input Form -->
        <UCard>
          <template #header>
            <h2 class="text-xl font-bold text-gray-900 dark:text-white">
              商品情報を入力
            </h2>
          </template>

          <div class="space-y-4">
            <div>
              <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                商品名
              </label>
              <UInput
                v-model="product.name"
                placeholder="例: ワイヤレスヘッドホン WH-1000XM5"
                size="lg"
              />
            </div>

            <div>
              <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                ブランド
              </label>
              <UInput
                v-model="product.brand"
                placeholder="例: Sony"
                size="lg"
              />
            </div>

            <div>
              <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                説明
              </label>
              <UTextarea
                v-model="product.description"
                placeholder="商品の説明を入力..."
                :rows="3"
              />
            </div>

            <div class="grid grid-cols-2 gap-4">
              <div>
                <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                  価格 (円)
                </label>
                <UInput
                  v-model="product.price"
                  type="number"
                  placeholder="45000"
                  size="lg"
                />
              </div>

              <div>
                <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                  在庫状況
                </label>
                <USelect
                  v-model="product.availability"
                  :options="availabilityOptions"
                  size="lg"
                />
              </div>
            </div>

            <div class="grid grid-cols-2 gap-4">
              <div>
                <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                  評価 (1-5)
                </label>
                <UInput
                  v-model="product.ratingValue"
                  type="number"
                  min="1"
                  max="5"
                  step="0.1"
                  placeholder="4.8"
                  size="lg"
                />
              </div>

              <div>
                <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                  レビュー数
                </label>
                <UInput
                  v-model="product.reviewCount"
                  type="number"
                  placeholder="127"
                  size="lg"
                />
              </div>
            </div>

            <div>
              <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                画像URL
              </label>
              <UInput
                v-model="product.image"
                placeholder="https://example.com/product.jpg"
                size="lg"
              />
            </div>
          </div>
        </UCard>

        <!-- Preview -->
        <div class="space-y-6">
          <!-- Search Result Preview -->
          <UCard>
            <template #header>
              <h2 class="text-xl font-bold text-gray-900 dark:text-white">
                検索結果での表示イメージ
              </h2>
            </template>

            <div class="p-4 bg-white dark:bg-gray-800 rounded-lg border border-gray-200 dark:border-gray-700">
              <div class="text-blue-600 dark:text-blue-400 text-lg font-medium mb-1">
                {{ product.name || '商品名' }}
              </div>
              <div class="text-gray-500 dark:text-gray-400 text-sm mb-2">
                {{ product.brand || 'ブランド名' }}
              </div>
              <div class="flex items-center gap-2 mb-2">
                <div class="flex">
                  <span
                    v-for="i in 5"
                    :key="i"
                    class="text-xl"
                    :class="i <= Math.floor(Number(product.ratingValue) || 0) ? 'text-yellow-400' : 'text-gray-300 dark:text-gray-600'"
                  >
                    ★
                  </span>
                </div>
                <span class="text-sm text-gray-600 dark:text-gray-400">
                  {{ product.ratingValue || '0' }} ({{ product.reviewCount || '0' }}件)
                </span>
              </div>
              <div class="text-2xl font-bold text-gray-900 dark:text-white mb-2">
                ¥{{ Number(product.price || 0).toLocaleString() }}
              </div>
              <div>
                <UBadge
                  :color="product.availability === 'InStock' ? 'green' : 'red'"
                  variant="subtle"
                >
                  {{ availabilityLabels[product.availability] }}
                </UBadge>
              </div>
            </div>
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
            実装方法
          </h2>
        </template>

        <div class="space-y-4">
          <p class="text-gray-700 dark:text-gray-300">
            Nuxt 3で<code class="px-2 py-1 bg-gray-100 dark:bg-gray-800 rounded text-sm">useHead()</code>を使って実装します：
          </p>

          <pre class="p-4 bg-gray-900 text-gray-100 rounded-lg overflow-x-auto text-sm"><code>&lt;script setup&gt;
const product = ref({
  name: 'ワイヤレスヘッドホン',
  price: '45000'
})

useHead({
  script: [
    {
      type: 'application/ld+json',
      innerHTML: JSON.stringify({
        '@context': 'https://schema.org',
        '@type': 'Product',
        'name': product.value.name,
        'offers': {
          '@type': 'Offer',
          'price': product.value.price,
          'priceCurrency': 'JPY'
        }
      })
    }
  ]
})
&lt;/script&gt;</code></pre>
        </div>
      </UCard>

      <!-- Field Descriptions -->
      <UCard>
        <template #header>
          <h2 class="text-xl font-bold text-gray-900 dark:text-white">
            フィールド説明
          </h2>
        </template>

        <div class="space-y-3">
          <div class="flex items-start gap-3">
            <UBadge color="primary" variant="soft">必須</UBadge>
            <div class="flex-1">
              <h3 class="font-semibold text-gray-900 dark:text-white">name</h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                商品の名前
              </p>
            </div>
          </div>

          <div class="flex items-start gap-3">
            <UBadge color="primary" variant="soft">必須</UBadge>
            <div class="flex-1">
              <h3 class="font-semibold text-gray-900 dark:text-white">image</h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                商品画像のURL（最低1200px推奨）
              </p>
            </div>
          </div>

          <div class="flex items-start gap-3">
            <UBadge color="gray" variant="soft">推奨</UBadge>
            <div class="flex-1">
              <h3 class="font-semibold text-gray-900 dark:text-white">offers</h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                価格情報（price, priceCurrency, availability）
              </p>
            </div>
          </div>

          <div class="flex items-start gap-3">
            <UBadge color="gray" variant="soft">推奨</UBadge>
            <div class="flex-1">
              <h3 class="font-semibold text-gray-900 dark:text-white">aggregateRating</h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                評価情報（ratingValue, reviewCount）
              </p>
            </div>
          </div>

          <div class="flex items-start gap-3">
            <UBadge color="gray" variant="soft">任意</UBadge>
            <div class="flex-1">
              <h3 class="font-semibold text-gray-900 dark:text-white">brand</h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                ブランド情報
              </p>
            </div>
          </div>
        </div>
      </UCard>
    </div>
  </UContainer>
</template>

<script setup lang="ts">
const product = ref({
  name: 'ワイヤレスヘッドホン WH-1000XM5',
  brand: 'Sony',
  description: '業界最高クラスのノイズキャンセリング性能を持つプレミアムヘッドホン',
  price: '45000',
  availability: 'InStock',
  ratingValue: '4.8',
  reviewCount: '127',
  image: 'https://example.com/product.jpg'
})

const availabilityOptions = [
  { label: '在庫あり', value: 'InStock' },
  { label: '在庫なし', value: 'OutOfStock' },
  { label: '予約受付中', value: 'PreOrder' }
]

const availabilityLabels: Record<string, string> = {
  InStock: '在庫あり',
  OutOfStock: '在庫なし',
  PreOrder: '予約受付中'
}

const jsonLd = computed(() => ({
  '@context': 'https://schema.org',
  '@type': 'Product',
  'name': product.value.name,
  'image': product.value.image,
  'description': product.value.description,
  'brand': {
    '@type': 'Brand',
    'name': product.value.brand
  },
  'offers': {
    '@type': 'Offer',
    'price': product.value.price,
    'priceCurrency': 'JPY',
    'availability': `https://schema.org/${product.value.availability}`
  },
  'aggregateRating': {
    '@type': 'AggregateRating',
    'ratingValue': product.value.ratingValue,
    'reviewCount': product.value.reviewCount
  }
}))

const formattedJsonLd = computed(() => JSON.stringify(jsonLd.value, null, 2))

// 実際のJSON-LDをページに追加
useHead({
  title: `商品ページ - ${product.value.name}`,
  script: [
    {
      type: 'application/ld+json',
      innerHTML: () => JSON.stringify(jsonLd.value)
    }
  ]
})

const copyToClipboard = async () => {
  await navigator.clipboard.writeText(formattedJsonLd.value)
  // TODO: Add toast notification
}

const resetForm = () => {
  product.value = {
    name: 'ワイヤレスヘッドホン WH-1000XM5',
    brand: 'Sony',
    description: '業界最高クラスのノイズキャンセリング性能を持つプレミアムヘッドホン',
    price: '45000',
    availability: 'InStock',
    ratingValue: '4.8',
    reviewCount: '127',
    image: 'https://example.com/product.jpg'
  }
}
</script>
