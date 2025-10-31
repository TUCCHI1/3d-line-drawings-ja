<template>
  <div class="min-h-screen">
    <UContainer class="py-12">
      <UButton to="/" icon="i-heroicons-arrow-left" class="mb-6">
        Back to Home
      </UButton>

      <div class="grid lg:grid-cols-2 gap-8">
        <div>
          <h1 class="text-3xl font-bold mb-6">{{ recipe.name }}</h1>

          <UCard>
            <img
              :src="recipe.image"
              :alt="recipe.name"
              class="w-full rounded-lg mb-4"
            >

            <p class="text-gray-700 dark:text-gray-300 mb-4">
              {{ recipe.description }}
            </p>

            <div class="grid grid-cols-3 gap-4 mb-6">
              <div class="text-center">
                <p class="text-sm text-gray-500">Prep Time</p>
                <p class="font-bold">{{ recipe.prepTime.replace('PT', '').replace('M', ' min') }}</p>
              </div>
              <div class="text-center">
                <p class="text-sm text-gray-500">Cook Time</p>
                <p class="font-bold">{{ recipe.cookTime.replace('PT', '').replace('M', ' min') }}</p>
              </div>
              <div class="text-center">
                <p class="text-sm text-gray-500">Servings</p>
                <p class="font-bold">{{ recipe.recipeYield }}</p>
              </div>
            </div>

            <USeparator class="my-4" />

            <h3 class="font-bold mb-2">Ingredients</h3>
            <ul class="list-disc list-inside mb-4 space-y-1">
              <li v-for="(ingredient, i) in recipe.recipeIngredient" :key="i">
                {{ ingredient }}
              </li>
            </ul>

            <h3 class="font-bold mb-2">Instructions</h3>
            <ol class="list-decimal list-inside space-y-2">
              <li
                v-for="(instruction, i) in recipe.recipeInstructions"
                :key="i"
                class="mb-2"
              >
                {{ instruction.text }}
              </li>
            </ol>
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
            title="Recipe Schema"
            description="調理時間、材料、手順が検索結果にリッチカードとして表示されます。"
            class="mt-4"
          />
        </div>
      </div>
    </UContainer>
  </div>
</template>

<script setup lang="ts">
const recipe = {
  name: '本格カレーライス',
  image: 'https://picsum.photos/800/500',
  description: '家庭で作れる本格的なカレーライスのレシピ。スパイスから作る本格派。',
  prepTime: 'PT20M',
  cookTime: 'PT40M',
  totalTime: 'PT60M',
  recipeYield: '4人分',
  recipeIngredient: [
    '鶏もも肉 400g',
    'たまねぎ 2個',
    'にんじん 1本',
    'じゃがいも 2個',
    'カレールー 1箱',
    '水 800ml',
    'サラダ油 大さじ2'
  ],
  recipeInstructions: [
    {
      '@type': 'HowToStep',
      text: '野菜を一口大に切る'
    },
    {
      '@type': 'HowToStep',
      text: '鍋に油をひき、鶏肉を炒める'
    },
    {
      '@type': 'HowToStep',
      text: '野菜を加えてさらに炒める'
    },
    {
      '@type': 'HowToStep',
      text: '水を加えて20分煮込む'
    },
    {
      '@type': 'HowToStep',
      text: 'カレールーを加えて10分煮込む'
    }
  ],
  author: {
    '@type': 'Person',
    name: '料理研究家 田中'
  }
}

const jsonLd = {
  '@context': 'https://schema.org',
  '@type': 'Recipe',
  ...recipe
}

useHead({
  title: 'Recipe Schema',
  script: [
    {
      type: 'application/ld+json',
      innerHTML: JSON.stringify(jsonLd)
    }
  ]
})
</script>
