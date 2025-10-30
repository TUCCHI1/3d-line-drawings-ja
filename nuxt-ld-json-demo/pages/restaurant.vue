<template>
  <UContainer>
    <div class="space-y-8">
      <!-- Header -->
      <div>
        <h1 class="text-3xl font-bold text-gray-900 dark:text-white mb-2">
          🍽️ レストラン (Restaurant)
        </h1>
        <p class="text-gray-600 dark:text-gray-300">
          店舗情報、営業時間、評価を構造化して、Googleマップや検索結果に最適化
        </p>
      </div>

      <!-- Interactive Demo -->
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
        <!-- Input Form -->
        <UCard>
          <template #header>
            <h2 class="text-xl font-bold text-gray-900 dark:text-white">
              レストラン情報を入力
            </h2>
          </template>

          <div class="space-y-4">
            <div>
              <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                店名
              </label>
              <UInput
                v-model="restaurant.name"
                placeholder="例: 寿司処 まつもと"
                size="lg"
              />
            </div>

            <div>
              <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                住所
              </label>
              <UInput
                v-model="restaurant.address"
                placeholder="東京都渋谷区1-2-3"
                size="lg"
              />
            </div>

            <div class="grid grid-cols-2 gap-4">
              <div>
                <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                  電話番号
                </label>
                <UInput
                  v-model="restaurant.telephone"
                  placeholder="+81-3-1234-5678"
                  size="lg"
                />
              </div>

              <div>
                <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                  郵便番号
                </label>
                <UInput
                  v-model="restaurant.postalCode"
                  placeholder="150-0001"
                  size="lg"
                />
              </div>
            </div>

            <div>
              <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                料理ジャンル
              </label>
              <USelect
                v-model="restaurant.cuisine"
                :options="cuisineOptions"
                size="lg"
              />
            </div>

            <div>
              <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                価格帯
              </label>
              <USelect
                v-model="restaurant.priceRange"
                :options="priceRangeOptions"
                size="lg"
              />
            </div>

            <div class="grid grid-cols-2 gap-4">
              <div>
                <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                  評価 (1-5)
                </label>
                <UInput
                  v-model="restaurant.ratingValue"
                  type="number"
                  min="1"
                  max="5"
                  step="0.1"
                  placeholder="4.5"
                  size="lg"
                />
              </div>

              <div>
                <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                  レビュー数
                </label>
                <UInput
                  v-model="restaurant.reviewCount"
                  type="number"
                  placeholder="89"
                  size="lg"
                />
              </div>
            </div>

            <div>
              <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                営業時間（平日）
              </label>
              <UInput
                v-model="restaurant.openingHoursWeekday"
                placeholder="Mo-Fr 11:30-22:00"
                size="lg"
              />
              <p class="text-xs text-gray-500 dark:text-gray-400 mt-1">
                Mo=月, Tu=火, We=水, Th=木, Fr=金, Sa=土, Su=日
              </p>
            </div>

            <div>
              <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                営業時間（土日）
              </label>
              <UInput
                v-model="restaurant.openingHoursWeekend"
                placeholder="Sa-Su 11:30-23:00"
                size="lg"
              />
            </div>
          </div>
        </UCard>

        <!-- Preview -->
        <div class="space-y-6">
          <!-- Restaurant Card Preview -->
          <UCard>
            <template #header>
              <h2 class="text-xl font-bold text-gray-900 dark:text-white">
                検索結果での表示イメージ
              </h2>
            </template>

            <div class="space-y-4">
              <div>
                <h3 class="text-xl font-bold text-blue-600 dark:text-blue-400 mb-1">
                  {{ restaurant.name || '店名' }}
                </h3>
                <div class="flex items-center gap-2 mb-2">
                  <div class="flex">
                    <span
                      v-for="i in 5"
                      :key="i"
                      class="text-lg"
                      :class="i <= Math.floor(Number(restaurant.ratingValue) || 0) ? 'text-yellow-400' : 'text-gray-300 dark:text-gray-600'"
                    >
                      ★
                    </span>
                  </div>
                  <span class="text-sm text-gray-600 dark:text-gray-400">
                    {{ restaurant.ratingValue || '0' }} ({{ restaurant.reviewCount || '0' }}件)
                  </span>
                </div>
                <UBadge color="primary" variant="subtle" class="mb-2">
                  {{ cuisineLabels[restaurant.cuisine] }}
                </UBadge>
                <UBadge color="gray" variant="subtle" class="mb-2 ml-2">
                  {{ restaurant.priceRange }}
                </UBadge>
              </div>

              <div class="text-sm text-gray-700 dark:text-gray-300 space-y-2">
                <div class="flex items-start gap-2">
                  <span>📍</span>
                  <span>{{ restaurant.address || '住所が表示されます' }}</span>
                </div>
                <div class="flex items-start gap-2">
                  <span>📞</span>
                  <span>{{ restaurant.telephone || '電話番号' }}</span>
                </div>
                <div class="flex items-start gap-2">
                  <span>🕐</span>
                  <div>
                    <div>平日: {{ restaurant.openingHoursWeekday || '11:30-22:00' }}</div>
                    <div>土日: {{ restaurant.openingHoursWeekend || '11:30-23:00' }}</div>
                  </div>
                </div>
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

      <!-- Benefits -->
      <UCard>
        <template #header>
          <h2 class="text-xl font-bold text-gray-900 dark:text-white">
            レストラン構造化データの効果
          </h2>
        </template>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
          <div class="flex items-start gap-3">
            <div class="text-2xl">🗺️</div>
            <div>
              <h3 class="font-semibold text-gray-900 dark:text-white">
                Googleマップ連携
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                営業時間や評価がGoogleマップに表示
              </p>
            </div>
          </div>

          <div class="flex items-start gap-3">
            <div class="text-2xl">⭐</div>
            <div>
              <h3 class="font-semibold text-gray-900 dark:text-white">
                星評価表示
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                検索結果に星評価が表示される
              </p>
            </div>
          </div>

          <div class="flex items-start gap-3">
            <div class="text-2xl">📱</div>
            <div>
              <h3 class="font-semibold text-gray-900 dark:text-white">
                ワンタップ電話
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                モバイルから直接電話できる
              </p>
            </div>
          </div>

          <div class="flex items-start gap-3">
            <div class="text-2xl">🔍</div>
            <div>
              <h3 class="font-semibold text-gray-900 dark:text-white">
                ローカル検索最適化
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                「近くのレストラン」検索で上位表示
              </p>
            </div>
          </div>
        </div>
      </UCard>
    </div>
  </UContainer>
</template>

<script setup lang="ts">
const restaurant = ref({
  name: '寿司処 まつもと',
  address: '東京都渋谷区1-2-3',
  telephone: '+81-3-1234-5678',
  postalCode: '150-0001',
  cuisine: 'Japanese',
  priceRange: '¥¥¥',
  ratingValue: '4.5',
  reviewCount: '89',
  openingHoursWeekday: 'Mo-Fr 11:30-22:00',
  openingHoursWeekend: 'Sa-Su 11:30-23:00'
})

const cuisineOptions = [
  { label: '和食', value: 'Japanese' },
  { label: 'イタリアン', value: 'Italian' },
  { label: 'フレンチ', value: 'French' },
  { label: '中華', value: 'Chinese' },
  { label: 'アメリカン', value: 'American' },
  { label: 'その他', value: 'Other' }
]

const cuisineLabels: Record<string, string> = {
  Japanese: '和食',
  Italian: 'イタリアン',
  French: 'フレンチ',
  Chinese: '中華',
  American: 'アメリカン',
  Other: 'その他'
}

const priceRangeOptions = [
  { label: '¥ - リーズナブル', value: '¥' },
  { label: '¥¥ - 普通', value: '¥¥' },
  { label: '¥¥¥ - 高め', value: '¥¥¥' },
  { label: '¥¥¥¥ - 高級', value: '¥¥¥¥' }
]

const jsonLd = computed(() => ({
  '@context': 'https://schema.org',
  '@type': 'Restaurant',
  'name': restaurant.value.name,
  'image': 'https://example.com/restaurant.jpg',
  'address': {
    '@type': 'PostalAddress',
    'streetAddress': restaurant.value.address,
    'addressLocality': '渋谷区',
    'addressRegion': '東京都',
    'postalCode': restaurant.value.postalCode,
    'addressCountry': 'JP'
  },
  'telephone': restaurant.value.telephone,
  'servesCuisine': restaurant.value.cuisine,
  'priceRange': restaurant.value.priceRange,
  'aggregateRating': {
    '@type': 'AggregateRating',
    'ratingValue': restaurant.value.ratingValue,
    'reviewCount': restaurant.value.reviewCount
  },
  'openingHours': [
    restaurant.value.openingHoursWeekday,
    restaurant.value.openingHoursWeekend
  ]
}))

const formattedJsonLd = computed(() => JSON.stringify(jsonLd.value, null, 2))

// 実際のJSON-LDをページに追加
useHead({
  title: `${restaurant.value.name} - レストラン情報`,
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
  restaurant.value = {
    name: '寿司処 まつもと',
    address: '東京都渋谷区1-2-3',
    telephone: '+81-3-1234-5678',
    postalCode: '150-0001',
    cuisine: 'Japanese',
    priceRange: '¥¥¥',
    ratingValue: '4.5',
    reviewCount: '89',
    openingHoursWeekday: 'Mo-Fr 11:30-22:00',
    openingHoursWeekend: 'Sa-Su 11:30-23:00'
  }
}
</script>
