<template>
  <div class="min-h-screen">
    <UContainer class="py-12">
      <UButton to="/" icon="i-heroicons-arrow-left" class="mb-6">
        Back to Home
      </UButton>

      <div class="grid lg:grid-cols-2 gap-8">
        <div>
          <h1 class="text-3xl font-bold mb-6">Event Schema Example</h1>

          <UCard>
            <img
              :src="event.image"
              :alt="event.name"
              class="w-full rounded-lg mb-4"
            >

            <h2 class="text-2xl font-bold mb-2">{{ event.name }}</h2>

            <p class="text-gray-700 dark:text-gray-300 mb-4">
              {{ event.description }}
            </p>

            <USeparator class="my-4" />

            <div class="space-y-4">
              <div>
                <p class="text-sm text-gray-500 dark:text-gray-400">Date & Time</p>
                <p class="font-semibold">
                  {{ formatDate(event.startDate) }} - {{ formatDate(event.endDate) }}
                </p>
              </div>

              <div>
                <p class="text-sm text-gray-500 dark:text-gray-400">Location</p>
                <p class="font-semibold">{{ event.location.name }}</p>
                <p class="text-sm">{{ event.location.address.streetAddress }}</p>
                <p class="text-sm">
                  {{ event.location.address.addressLocality }},
                  {{ event.location.address.addressRegion }}
                </p>
              </div>

              <div>
                <p class="text-sm text-gray-500 dark:text-gray-400">Organizer</p>
                <p class="font-semibold">{{ event.organizer.name }}</p>
              </div>

              <div>
                <p class="text-sm text-gray-500 dark:text-gray-400">Ticket Price</p>
                <p class="text-2xl font-bold text-primary">
                  {{ event.offers.priceCurrency }} {{ event.offers.price }}
                </p>
                <UBadge
                  :color="event.offers.availability === 'InStock' ? 'green' : 'red'"
                  class="mt-1"
                >
                  {{ event.offers.availability === 'InStock' ? 'Available' : 'Sold Out' }}
                </UBadge>
              </div>
            </div>

            <UButton color="primary" size="lg" block class="mt-6">
              Register Now
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
            title="Event Schema"
            description="イベント日時、場所、チケット価格が検索結果に表示されます。"
            class="mt-4"
          />
        </div>
      </div>
    </UContainer>
  </div>
</template>

<script setup lang="ts">
const event = {
  name: 'Nuxt 4 リリース記念カンファレンス',
  description: 'Nuxt 4の最新機能と実践的な開発手法を学ぶカンファレンス。業界のエキスパートが登壇します。',
  image: 'https://picsum.photos/800/400',
  startDate: '2025-11-15T10:00:00+09:00',
  endDate: '2025-11-15T18:00:00+09:00',
  eventStatus: 'https://schema.org/EventScheduled',
  eventAttendanceMode: 'https://schema.org/OfflineEventAttendanceMode',
  location: {
    '@type': 'Place',
    name: '東京コンベンションセンター',
    address: {
      '@type': 'PostalAddress',
      streetAddress: '1-1-1 有明',
      addressLocality: '江東区',
      addressRegion: '東京都',
      postalCode: '135-0000',
      addressCountry: 'JP'
    }
  },
  organizer: {
    '@type': 'Organization',
    name: 'Nuxt Community Japan',
    url: 'https://example.com'
  },
  offers: {
    '@type': 'Offer',
    url: 'https://example.com/event/tickets',
    price: '5000',
    priceCurrency: 'JPY',
    availability: 'InStock',
    validFrom: '2025-10-01T00:00:00+09:00'
  }
}

const jsonLd = {
  '@context': 'https://schema.org',
  '@type': 'Event',
  ...event
}

const formatDate = (dateString: string) => {
  return new Date(dateString).toLocaleString('ja-JP', {
    year: 'numeric',
    month: 'long',
    day: 'numeric',
    hour: '2-digit',
    minute: '2-digit'
  })
}

useHead({
  title: 'Event Schema',
  script: [
    {
      type: 'application/ld+json',
      innerHTML: JSON.stringify(jsonLd)
    }
  ]
})
</script>
