<template>
  <div class="min-h-screen">
    <UContainer class="py-12">
      <UButton to="/" icon="i-heroicons-arrow-left" class="mb-6">
        Back to Home
      </UButton>

      <div class="grid lg:grid-cols-2 gap-8">
        <div>
          <h1 class="text-3xl font-bold mb-6">Person Schema Example</h1>

          <UCard>
            <template #header>
              <h2 class="text-xl font-semibold">Profile Information</h2>
            </template>

            <div class="space-y-4">
              <div>
                <p class="text-sm text-gray-500 dark:text-gray-400">Name</p>
                <p class="font-semibold">{{ person.name }}</p>
              </div>
              <div>
                <p class="text-sm text-gray-500 dark:text-gray-400">Job Title</p>
                <p class="font-semibold">{{ person.jobTitle }}</p>
              </div>
              <div>
                <p class="text-sm text-gray-500 dark:text-gray-400">Email</p>
                <p class="font-semibold">{{ person.email }}</p>
              </div>
              <div>
                <p class="text-sm text-gray-500 dark:text-gray-400">Telephone</p>
                <p class="font-semibold">{{ person.telephone }}</p>
              </div>
              <div>
                <p class="text-sm text-gray-500 dark:text-gray-400">Website</p>
                <ULink :to="person.url" target="_blank" class="text-primary">
                  {{ person.url }}
                </ULink>
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
            title="SEO Benefits"
            description="このJSON-LDは検索エンジンに人物情報を提供し、リッチスニペットとして表示される可能性があります。"
            class="mt-4"
          />
        </div>
      </div>
    </UContainer>
  </div>
</template>

<script setup lang="ts">
const person = {
  name: '山田太郎',
  jobTitle: 'フロントエンドエンジニア',
  email: 'taro.yamada@example.com',
  telephone: '+81-90-1234-5678',
  url: 'https://example.com'
}

const jsonLd = {
  '@context': 'https://schema.org',
  '@type': 'Person',
  name: person.name,
  jobTitle: person.jobTitle,
  email: person.email,
  telephone: person.telephone,
  url: person.url
}

useHead({
  title: 'Person Schema',
  script: [
    {
      type: 'application/ld+json',
      innerHTML: JSON.stringify(jsonLd)
    }
  ]
})
</script>
