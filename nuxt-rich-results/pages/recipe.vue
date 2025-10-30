<template>
  <UContainer>
    <div class="space-y-8">
      <!-- Header -->
      <div class="text-center">
        <div class="text-7xl mb-4">🍳</div>
        <h1 class="text-4xl font-bold text-gray-900 dark:text-white mb-4">
          レシピリッチリザルト
        </h1>
        <p class="text-lg text-gray-600 dark:text-gray-300 max-w-2xl mx-auto">
          料理ブログ・レシピサイトで<strong>必須</strong>の機能
        </p>
      </div>

      <!-- Visual Example -->
      <UCard class="bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm">
        <template #header>
          <h2 class="text-2xl font-bold text-gray-900 dark:text-white">
            📱 Google検索結果での表示例
          </h2>
        </template>

        <div class="border-2 border-orange-300 dark:border-orange-700 rounded-xl p-6 bg-gradient-to-br from-orange-50 to-yellow-50 dark:from-orange-950 dark:to-yellow-950">
          <div class="flex gap-6">
            <!-- Recipe Image -->
            <div class="flex-shrink-0">
              <div class="w-32 h-32 bg-gradient-to-br from-orange-200 to-red-300 dark:from-orange-700 dark:to-red-600 rounded-lg flex items-center justify-center text-5xl">
                🍛
              </div>
            </div>

            <!-- Recipe Info -->
            <div class="flex-1">
              <div class="text-blue-600 dark:text-blue-400 text-xl font-medium mb-2">
                本格スパイスカレーの作り方
              </div>

              <!-- Rating -->
              <div class="flex items-center gap-2 mb-3">
                <div class="flex text-yellow-400 text-lg">
                  ★★★★★
                </div>
                <span class="text-sm text-gray-700 dark:text-gray-300">
                  4.9 (567件)
                </span>
              </div>

              <!-- Time, Calories, Difficulty -->
              <div class="flex gap-4 mb-3 text-sm text-gray-700 dark:text-gray-300">
                <div class="flex items-center gap-1">
                  <span>⏱️</span>
                  <span><strong>45分</strong></span>
                </div>
                <div class="flex items-center gap-1">
                  <span>🔥</span>
                  <span><strong>320kcal</strong></span>
                </div>
                <div class="flex items-center gap-1">
                  <span>📊</span>
                  <span><strong>中級</strong></span>
                </div>
              </div>

              <!-- Description -->
              <p class="text-sm text-gray-600 dark:text-gray-400">
                スパイスから作る本格カレー。玉ねぎをじっくり炒めて、トマトとスパイスで煮込んだ本格的な味わいです...
              </p>
            </div>
          </div>
        </div>
      </UCard>

      <!-- Key Features -->
      <UCard class="bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm">
        <template #header>
          <h2 class="text-2xl font-bold text-gray-900 dark:text-white">
            ✨ 表示される情報
          </h2>
        </template>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
          <div class="text-center p-4 bg-orange-50 dark:bg-orange-950 rounded-lg">
            <div class="text-4xl mb-3">⏱️</div>
            <h3 class="font-semibold text-gray-900 dark:text-white mb-2">調理時間</h3>
            <p class="text-sm text-gray-600 dark:text-gray-400">
              準備＋調理時間を表示
            </p>
          </div>

          <div class="text-center p-4 bg-red-50 dark:bg-red-950 rounded-lg">
            <div class="text-4xl mb-3">🔥</div>
            <h3 class="font-semibold text-gray-900 dark:text-white mb-2">カロリー</h3>
            <p class="text-sm text-gray-600 dark:text-gray-400">
              一人前のカロリー情報
            </p>
          </div>

          <div class="text-center p-4 bg-yellow-50 dark:bg-yellow-950 rounded-lg">
            <div class="text-4xl mb-3">⭐</div>
            <h3 class="font-semibold text-gray-900 dark:text-white mb-2">評価</h3>
            <p class="text-sm text-gray-600 dark:text-gray-400">
              星評価とレビュー数
            </p>
          </div>
        </div>
      </UCard>

      <!-- JSON-LD Example -->
      <UCard class="bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm">
        <template #header>
          <h2 class="text-2xl font-bold text-gray-900 dark:text-white">
            💻 実装方法（JSON-LD）
          </h2>
        </template>

        <pre class="p-4 bg-gray-900 text-gray-100 rounded-lg overflow-x-auto text-sm"><code>{
  "@context": "https://schema.org",
  "@type": "Recipe",
  "name": "本格スパイスカレー",
  "image": "https://example.com/curry.jpg",
  "description": "スパイスから作る本格カレー",
  "author": {
    "@type": "Person",
    "name": "山田シェフ"
  },
  "prepTime": "PT15M",
  "cookTime": "PT30M",
  "totalTime": "PT45M",
  "recipeYield": "4人分",
  "recipeCategory": "メインディッシュ",
  "recipeCuisine": "インド料理",
  "nutrition": {
    "@type": "NutritionInformation",
    "calories": "320 calories"
  },
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "4.9",
    "reviewCount": "567"
  },
  "recipeIngredient": [
    "玉ねぎ 2個",
    "トマト 3個",
    "カレー粉 大さじ3",
    "鶏肉 400g"
  ],
  "recipeInstructions": [
    {
      "@type": "HowToStep",
      "text": "玉ねぎをみじん切りにする"
    },
    {
      "@type": "HowToStep",
      "text": "玉ねぎを飴色になるまで炒める"
    }
  ]
}</code></pre>
      </UCard>

      <!-- Benefits -->
      <UCard class="bg-gradient-to-r from-orange-500 to-red-600 text-white">
        <template #header>
          <h2 class="text-2xl font-bold">
            📈 レシピリッチリザルトの効果
          </h2>
        </template>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
          <div class="flex items-start gap-4">
            <div class="text-3xl">🎯</div>
            <div>
              <h3 class="text-xl font-bold mb-2">検索結果で目立つ</h3>
              <p class="opacity-90">
                画像・調理時間・カロリーが表示され、視覚的に訴求
              </p>
            </div>
          </div>

          <div class="flex items-start gap-4">
            <div class="text-3xl">📱</div>
            <div>
              <h3 class="text-xl font-bold mb-2">Googleアシスタント対応</h3>
              <p class="opacity-90">
                「Hey Google、カレーの作り方を教えて」で音声検索に対応
              </p>
            </div>
          </div>
        </div>
      </UCard>

      <!-- Time Format -->
      <UCard class="bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm">
        <template #header>
          <h2 class="text-2xl font-bold text-gray-900 dark:text-white">
            ⏰ 時間のフォーマット（ISO 8601）
          </h2>
        </template>

        <div class="space-y-3">
          <div class="flex items-center gap-4">
            <code class="px-3 py-2 bg-gray-100 dark:bg-gray-800 rounded font-mono text-sm">
              PT15M
            </code>
            <span class="text-gray-700 dark:text-gray-300">= 15分</span>
          </div>

          <div class="flex items-center gap-4">
            <code class="px-3 py-2 bg-gray-100 dark:bg-gray-800 rounded font-mono text-sm">
              PT1H30M
            </code>
            <span class="text-gray-700 dark:text-gray-300">= 1時間30分</span>
          </div>

          <div class="flex items-center gap-4">
            <code class="px-3 py-2 bg-gray-100 dark:bg-gray-800 rounded font-mono text-sm">
              PT45M
            </code>
            <span class="text-gray-700 dark:text-gray-300">= 45分</span>
          </div>
        </div>
      </UCard>
    </div>
  </UContainer>
</template>

<script setup lang="ts">
useHead({
  title: 'レシピリッチリザルト - 料理ブログ必須の機能',
  meta: [
    {
      name: 'description',
      content: 'レシピリッチリザルトの実装方法。調理時間・カロリー・評価を検索結果に表示して、料理ブログのアクセスを増やす。'
    }
  ]
})
</script>
