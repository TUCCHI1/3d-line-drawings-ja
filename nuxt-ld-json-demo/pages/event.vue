<template>
  <UContainer>
    <div class="space-y-8">
      <!-- Header -->
      <div>
        <h1 class="text-3xl font-bold text-gray-900 dark:text-white mb-2">
          🎫 イベント (Event)
        </h1>
        <p class="text-gray-600 dark:text-gray-300">
          イベント情報を構造化して、Google検索やGoogleカレンダーに最適化
        </p>
      </div>

      <!-- Interactive Demo -->
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
        <!-- Input Form -->
        <UCard>
          <template #header>
            <h2 class="text-xl font-bold text-gray-900 dark:text-white">
              イベント情報を入力
            </h2>
          </template>

          <div class="space-y-4">
            <div>
              <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                イベント名
              </label>
              <UInput
                v-model="event.name"
                placeholder="例: Web技術カンファレンス 2024"
                size="lg"
              />
            </div>

            <div>
              <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                説明
              </label>
              <UTextarea
                v-model="event.description"
                placeholder="イベントの説明を入力..."
                :rows="3"
              />
            </div>

            <div class="grid grid-cols-2 gap-4">
              <div>
                <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                  開始日時
                </label>
                <UInput
                  v-model="event.startDate"
                  type="datetime-local"
                  size="lg"
                />
              </div>

              <div>
                <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                  終了日時
                </label>
                <UInput
                  v-model="event.endDate"
                  type="datetime-local"
                  size="lg"
                />
              </div>
            </div>

            <div>
              <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                開催形式
              </label>
              <USelect
                v-model="event.attendanceMode"
                :options="attendanceModeOptions"
                size="lg"
              />
            </div>

            <div>
              <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                会場名
              </label>
              <UInput
                v-model="event.locationName"
                placeholder="例: 東京国際フォーラム"
                size="lg"
              />
            </div>

            <div>
              <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                会場住所
              </label>
              <UInput
                v-model="event.locationAddress"
                placeholder="千代田区丸の内3-5-1"
                size="lg"
              />
            </div>

            <div class="grid grid-cols-2 gap-4">
              <div>
                <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                  チケット価格 (円)
                </label>
                <UInput
                  v-model="event.price"
                  type="number"
                  placeholder="5000"
                  size="lg"
                />
              </div>

              <div>
                <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                  在庫状況
                </label>
                <USelect
                  v-model="event.availability"
                  :options="availabilityOptions"
                  size="lg"
                />
              </div>
            </div>

            <div>
              <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                チケットURL
              </label>
              <UInput
                v-model="event.ticketUrl"
                placeholder="https://example.com/tickets"
                size="lg"
              />
            </div>

            <div>
              <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                主催者名
              </label>
              <UInput
                v-model="event.organizerName"
                placeholder="例: Web Tech Org"
                size="lg"
              />
            </div>
          </div>
        </UCard>

        <!-- Preview -->
        <div class="space-y-6">
          <!-- Event Card Preview -->
          <UCard>
            <template #header>
              <h2 class="text-xl font-bold text-gray-900 dark:text-white">
                検索結果での表示イメージ
              </h2>
            </template>

            <div class="space-y-4">
              <div>
                <h3 class="text-xl font-bold text-blue-600 dark:text-blue-400 mb-2">
                  {{ event.name || 'イベント名' }}
                </h3>
                <UBadge :color="attendanceModeColor[event.attendanceMode]" variant="subtle" class="mb-3">
                  {{ attendanceModeLabels[event.attendanceMode] }}
                </UBadge>
              </div>

              <div class="text-sm text-gray-700 dark:text-gray-300 space-y-2">
                <div class="flex items-start gap-2">
                  <span>📅</span>
                  <div>
                    <div>{{ formatDateTime(event.startDate) }}</div>
                    <div class="text-gray-500 dark:text-gray-400">
                      ～ {{ formatDateTime(event.endDate) }}
                    </div>
                  </div>
                </div>

                <div class="flex items-start gap-2">
                  <span>📍</span>
                  <div>
                    <div>{{ event.locationName || '会場名' }}</div>
                    <div class="text-gray-500 dark:text-gray-400">
                      {{ event.locationAddress || '住所' }}
                    </div>
                  </div>
                </div>

                <div class="flex items-center gap-2">
                  <span>🎫</span>
                  <div>
                    <span class="text-lg font-bold text-primary-600 dark:text-primary-400">
                      ¥{{ Number(event.price || 0).toLocaleString() }}
                    </span>
                    <UBadge
                      :color="event.availability === 'InStock' ? 'green' : 'red'"
                      variant="subtle"
                      class="ml-2"
                    >
                      {{ availabilityLabels[event.availability] }}
                    </UBadge>
                  </div>
                </div>

                <div class="flex items-start gap-2">
                  <span>👥</span>
                  <span>主催: {{ event.organizerName || '主催者名' }}</span>
                </div>
              </div>

              <p class="text-sm text-gray-600 dark:text-gray-400">
                {{ event.description || 'イベントの説明がここに表示されます...' }}
              </p>
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
            イベント構造化データの効果
          </h2>
        </template>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
          <div class="flex items-start gap-3">
            <div class="text-2xl">🔍</div>
            <div>
              <h3 class="font-semibold text-gray-900 dark:text-white">
                検索結果に表示
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                日時・場所・価格が検索結果に表示される
              </p>
            </div>
          </div>

          <div class="flex items-start gap-3">
            <div class="text-2xl">📱</div>
            <div>
              <h3 class="font-semibold text-gray-900 dark:text-white">
                カレンダー追加
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                ワンタップでGoogleカレンダーに追加可能
              </p>
            </div>
          </div>

          <div class="flex items-start gap-3">
            <div class="text-2xl">🎯</div>
            <div>
              <h3 class="font-semibold text-gray-900 dark:text-white">
                イベント検索最適化
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                「イベント 東京」などの検索で上位表示
              </p>
            </div>
          </div>

          <div class="flex items-start gap-3">
            <div class="text-2xl">🌐</div>
            <div>
              <h3 class="font-semibold text-gray-900 dark:text-white">
                オンライン対応
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                オンラインイベントの表示にも最適化
              </p>
            </div>
          </div>
        </div>
      </UCard>

      <!-- Event Status -->
      <UCard>
        <template #header>
          <h2 class="text-xl font-bold text-gray-900 dark:text-white">
            開催形式の種類
          </h2>
        </template>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
          <div class="p-4 border border-gray-200 dark:border-gray-700 rounded-lg">
            <h3 class="font-semibold text-gray-900 dark:text-white mb-2">
              オフライン
            </h3>
            <p class="text-sm text-gray-600 dark:text-gray-400">
              実際の会場で開催されるイベント
            </p>
          </div>

          <div class="p-4 border border-gray-200 dark:border-gray-700 rounded-lg">
            <h3 class="font-semibold text-gray-900 dark:text-white mb-2">
              オンライン
            </h3>
            <p class="text-sm text-gray-600 dark:text-gray-400">
              完全オンラインで開催されるイベント
            </p>
          </div>

          <div class="p-4 border border-gray-200 dark:border-gray-700 rounded-lg">
            <h3 class="font-semibold text-gray-900 dark:text-white mb-2">
              ハイブリッド
            </h3>
            <p class="text-sm text-gray-600 dark:text-gray-400">
              オフライン＋オンラインのハイブリッド開催
            </p>
          </div>
        </div>
      </UCard>
    </div>
  </UContainer>
</template>

<script setup lang="ts">
const tomorrow = new Date()
tomorrow.setDate(tomorrow.getDate() + 1)
const tomorrowStr = tomorrow.toISOString().slice(0, 16)

const event = ref({
  name: 'Web技術カンファレンス 2024',
  description: '最新のWeb技術トレンドについて学べる技術カンファレンス。Nuxt、React、Vue.jsなどのセッションが盛りだくさん。',
  startDate: tomorrowStr,
  endDate: tomorrowStr,
  attendanceMode: 'OfflineEventAttendanceMode',
  locationName: '東京国際フォーラム',
  locationAddress: '千代田区丸の内3-5-1',
  price: '5000',
  availability: 'InStock',
  ticketUrl: 'https://example.com/tickets',
  organizerName: 'Web Tech Org'
})

const attendanceModeOptions = [
  { label: 'オフライン', value: 'OfflineEventAttendanceMode' },
  { label: 'オンライン', value: 'OnlineEventAttendanceMode' },
  { label: 'ハイブリッド', value: 'MixedEventAttendanceMode' }
]

const attendanceModeLabels: Record<string, string> = {
  OfflineEventAttendanceMode: 'オフライン',
  OnlineEventAttendanceMode: 'オンライン',
  MixedEventAttendanceMode: 'ハイブリッド'
}

const attendanceModeColor: Record<string, string> = {
  OfflineEventAttendanceMode: 'blue',
  OnlineEventAttendanceMode: 'purple',
  MixedEventAttendanceMode: 'green'
}

const availabilityOptions = [
  { label: 'チケット販売中', value: 'InStock' },
  { label: '完売', value: 'SoldOut' },
  { label: '予約受付中', value: 'PreOrder' }
]

const availabilityLabels: Record<string, string> = {
  InStock: '販売中',
  SoldOut: '完売',
  PreOrder: '予約受付中'
}

const formatDateTime = (dateStr: string) => {
  if (!dateStr) return '未設定'
  const date = new Date(dateStr)
  return date.toLocaleString('ja-JP', {
    year: 'numeric',
    month: '2-digit',
    day: '2-digit',
    hour: '2-digit',
    minute: '2-digit'
  })
}

const jsonLd = computed(() => ({
  '@context': 'https://schema.org',
  '@type': 'Event',
  'name': event.value.name,
  'description': event.value.description,
  'startDate': event.value.startDate,
  'endDate': event.value.endDate,
  'eventAttendanceMode': `https://schema.org/${event.value.attendanceMode}`,
  'eventStatus': 'https://schema.org/EventScheduled',
  'location': {
    '@type': 'Place',
    'name': event.value.locationName,
    'address': {
      '@type': 'PostalAddress',
      'streetAddress': event.value.locationAddress,
      'addressLocality': '千代田区',
      'addressCountry': 'JP'
    }
  },
  'offers': {
    '@type': 'Offer',
    'url': event.value.ticketUrl,
    'price': event.value.price,
    'priceCurrency': 'JPY',
    'availability': `https://schema.org/${event.value.availability}`,
    'validFrom': new Date().toISOString().split('T')[0]
  },
  'organizer': {
    '@type': 'Organization',
    'name': event.value.organizerName,
    'url': 'https://example.com'
  }
}))

const formattedJsonLd = computed(() => JSON.stringify(jsonLd.value, null, 2))

// 実際のJSON-LDをページに追加
useHead({
  title: `${event.value.name} - イベント情報`,
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
  event.value = {
    name: 'Web技術カンファレンス 2024',
    description: '最新のWeb技術トレンドについて学べる技術カンファレンス。Nuxt、React、Vue.jsなどのセッションが盛りだくさん。',
    startDate: tomorrowStr,
    endDate: tomorrowStr,
    attendanceMode: 'OfflineEventAttendanceMode',
    locationName: '東京国際フォーラム',
    locationAddress: '千代田区丸の内3-5-1',
    price: '5000',
    availability: 'InStock',
    ticketUrl: 'https://example.com/tickets',
    organizerName: 'Web Tech Org'
  }
}
</script>
