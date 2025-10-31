<template>
  <div class="min-h-screen">
    <UContainer class="py-12">
      <UButton to="/" icon="i-heroicons-arrow-left" class="mb-6">
        Back to Home
      </UButton>

      <div class="grid lg:grid-cols-2 gap-8">
        <div>
          <h1 class="text-3xl font-bold mb-6">Product Schema Example</h1>

          <UCard>
            <img
              :src="product.image"
              :alt="product.name"
              class="w-full rounded-lg mb-4"
            >

            <h2 class="text-2xl font-bold mb-2">{{ product.name }}</h2>

            <div class="flex items-center gap-2 mb-4">
              <div class="flex text-yellow-400">
                <span v-for="i in 5" :key="i">
                  {{ i <= Math.floor(product.aggregateRating.ratingValue) ? '★' : '☆' }}
                </span>
              </div>
              <span class="text-sm text-gray-600">
                {{ product.aggregateRating.ratingValue }}
                ({{ product.aggregateRating.reviewCount }} reviews)
              </span>
            </div>

            <p class="text-gray-700 dark:text-gray-300 mb-4">
              {{ product.description }}
            </p>

            <USeparator class="my-4" />

            <div class="space-y-2">
              <div class="flex justify-between">
                <span class="text-gray-600">Price</span>
                <span class="text-2xl font-bold text-primary">
                  {{ product.offers.priceCurrency }} {{ product.offers.price }}
                </span>
              </div>
              <div class="flex justify-between">
                <span class="text-gray-600">Availability</span>
                <UBadge :color="product.offers.availability === 'InStock' ? 'green' : 'red'">
                  {{ product.offers.availability === 'InStock' ? 'In Stock' : 'Out of Stock' }}
                </UBadge>
              </div>
              <div class="flex justify-between">
                <span class="text-gray-600">Brand</span>
                <span class="font-semibold">{{ product.brand.name }}</span>
              </div>
            </div>

            <UButton color="primary" size="lg" block class="mt-6">
              Add to Cart
            </UButton>
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
            title="Product Schema"
            description="価格、在庫状況、レビュー評価が検索結果に表示されます。"
            class="mt-4"
          />
        </div>
      </div>
    </UContainer>
  </div>
</template>

<script setup lang="ts">
const product = {
  name: 'Nuxt 4 完全ガイドブック',
  image: 'https://picsum.photos/600/600',
  description: 'Nuxt 4の全機能を網羅した決定版ガイド。初心者から上級者まで対応。',
  brand: {
    '@type': 'Brand',
    name: 'Tech Publishers'
  },
  offers: {
    '@type': 'Offer',
    url: 'https://example.com/product',
    priceCurrency: 'JPY',
    price: '3980',
    availability: 'InStock',
    priceValidUntil: '2025-12-31'
  },
  aggregateRating: {
    '@type': 'AggregateRating',
    ratingValue: 4.8,
    reviewCount: 127
  }
}

const jsonLd = {
  '@context': 'https://schema.org',
  '@type': 'Product',
  ...product
}

useHead({
  title: 'Product Schema',
  script: [
    {
      type: 'application/ld+json',
      innerHTML: JSON.stringify(jsonLd)
    }
  ]
})
</script>
