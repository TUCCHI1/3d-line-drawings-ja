<template>
  <div class="min-h-screen">
    <UContainer class="py-12">
      <UButton to="/" icon="i-heroicons-arrow-left" class="mb-6">
        Back to Home
      </UButton>

      <div class="grid lg:grid-cols-2 gap-8">
        <div>
          <h1 class="text-3xl font-bold mb-6">Organization Schema Example</h1>

          <UCard>
            <div class="text-center mb-6">
              <img
                :src="organization.logo"
                :alt="organization.name"
                class="w-32 h-32 mx-auto mb-4 rounded-full"
              >
              <h2 class="text-2xl font-bold">{{ organization.name }}</h2>
            </div>

            <USeparator class="my-4" />

            <div class="space-y-4">
              <div>
                <p class="text-sm text-gray-500 dark:text-gray-400">Address</p>
                <p>
                  {{ organization.address.streetAddress }}<br>
                  {{ organization.address.addressLocality }},
                  {{ organization.address.addressRegion }}
                  {{ organization.address.postalCode }}
                </p>
              </div>

              <div>
                <p class="text-sm text-gray-500 dark:text-gray-400">Contact</p>
                <p>Tel: {{ organization.telephone }}</p>
                <p>Email: {{ organization.email }}</p>
              </div>

              <div>
                <p class="text-sm text-gray-500 dark:text-gray-400">Website</p>
                <ULink :to="organization.url" target="_blank" class="text-primary">
                  {{ organization.url }}
                </ULink>
              </div>

              <div>
                <p class="text-sm text-gray-500 dark:text-gray-400">Social Media</p>
                <div class="flex gap-2 mt-2">
                  <ULink
                    v-for="social in organization.sameAs"
                    :key="social"
                    :to="social"
                    target="_blank"
                  >
                    <UButton size="sm" variant="outline">
                      {{ getSocialName(social) }}
                    </UButton>
                  </ULink>
                </div>
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
            title="Organization Schema"
            description="企業情報、所在地、連絡先が検索結果のナレッジパネルに表示されます。"
            class="mt-4"
          />
        </div>
      </div>
    </UContainer>
  </div>
</template>

<script setup lang="ts">
const organization = {
  name: 'Tech Innovation株式会社',
  url: 'https://example.com',
  logo: 'https://picsum.photos/200/200',
  telephone: '+81-3-1234-5678',
  email: 'info@example.com',
  address: {
    '@type': 'PostalAddress',
    streetAddress: '1-2-3 渋谷',
    addressLocality: '渋谷区',
    addressRegion: '東京都',
    postalCode: '150-0000',
    addressCountry: 'JP'
  },
  sameAs: [
    'https://twitter.com/example',
    'https://facebook.com/example',
    'https://linkedin.com/company/example'
  ]
}

const jsonLd = {
  '@context': 'https://schema.org',
  '@type': 'Organization',
  ...organization
}

const getSocialName = (url: string) => {
  try {
    const hostname = new URL(url).hostname
    return hostname.split('.')[0]
  } catch {
    return 'social'
  }
}

useHead({
  title: 'Organization Schema',
  script: [
    {
      type: 'application/ld+json',
      innerHTML: JSON.stringify(jsonLd)
    }
  ]
})
</script>
