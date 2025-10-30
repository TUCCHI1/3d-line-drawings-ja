<template>
  <UContainer>
    <div class="space-y-8">
      <!-- Header -->
      <div class="text-center">
        <div class="text-7xl mb-4">🛍️</div>
        <h1 class="text-4xl font-bold text-gray-900 dark:text-white mb-4">
          商品リッチリザルト
        </h1>
        <p class="text-lg text-gray-600 dark:text-gray-300 max-w-2xl mx-auto">
          ECサイトで<strong>CTRが40%向上</strong>する最強の機能
        </p>
      </div>

      <!-- Visual Example -->
      <UCard class="bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm">
        <template #header>
          <h2 class="text-2xl font-bold text-gray-900 dark:text-white">
            📱 Google検索結果での表示例
          </h2>
        </template>

        <div class="space-y-4">
          <p class="text-gray-700 dark:text-gray-300">
            商品リッチリザルトでは、以下の情報が検索結果に表示されます：
          </p>

          <!-- Mock Google Search Result -->
          <div class="border-2 border-blue-300 dark:border-blue-700 rounded-xl p-6 bg-gradient-to-br from-blue-50 to-purple-50 dark:from-blue-950 dark:to-purple-950">
            <div class="flex gap-6">
              <!-- Product Image -->
              <div class="flex-shrink-0">
                <div class="w-32 h-32 bg-gradient-to-br from-gray-200 to-gray-300 dark:from-gray-700 dark:to-gray-600 rounded-lg flex items-center justify-center text-5xl">
                  🎧
                </div>
              </div>

              <!-- Product Info -->
              <div class="flex-1">
                <div class="text-blue-600 dark:text-blue-400 text-xl font-medium mb-2 hover:underline cursor-pointer">
                  ワイヤレスヘッドホン WH-1000XM5 - ソニー公式
                </div>
                <div class="text-green-700 dark:text-green-400 text-sm mb-3">
                  https://www.sony.jp › headphone › wh-1000xm5
                </div>

                <!-- Rating -->
                <div class="flex items-center gap-2 mb-3">
                  <div class="flex text-yellow-400 text-lg">
                    ★★★★★
                  </div>
                  <span class="text-sm text-gray-700 dark:text-gray-300">
                    評価: <strong>4.8</strong> (1,234件のレビュー)
                  </span>
                </div>

                <!-- Price & Availability -->
                <div class="flex items-center gap-4 mb-3">
                  <div class="text-3xl font-bold text-gray-900 dark:text-white">
                    ¥45,000
                  </div>
                  <UBadge color="green" size="lg">
                    在庫あり
                  </UBadge>
                </div>

                <!-- Description -->
                <p class="text-sm text-gray-600 dark:text-gray-400">
                  業界最高クラスのノイズキャンセリング性能。長時間の快適な装着感で、音楽を存分に楽しめます...
                </p>
              </div>
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

        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
          <div class="flex items-start gap-4">
            <div class="flex-shrink-0 text-4xl">🖼️</div>
            <div>
              <h3 class="text-lg font-semibold text-gray-900 dark:text-white mb-2">
                商品画像
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                サムネイル画像が表示され、視覚的に商品を訴求
              </p>
            </div>
          </div>

          <div class="flex items-start gap-4">
            <div class="flex-shrink-0 text-4xl">💰</div>
            <div>
              <h3 class="text-lg font-semibold text-gray-900 dark:text-white mb-2">
                価格情報
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                価格が大きく表示され、ユーザーの意思決定をサポート
              </p>
            </div>
          </div>

          <div class="flex items-start gap-4">
            <div class="flex-shrink-0 text-4xl">⭐</div>
            <div>
              <h3 class="text-lg font-semibold text-gray-900 dark:text-white mb-2">
                評価・レビュー
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                星評価とレビュー数で信頼性を向上
              </p>
            </div>
          </div>

          <div class="flex items-start gap-4">
            <div class="flex-shrink-0 text-4xl">📦</div>
            <div>
              <h3 class="text-lg font-semibold text-gray-900 dark:text-white mb-2">
                在庫状況
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                在庫ありかどうかが一目で分かる
              </p>
            </div>
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

        <div class="space-y-4">
          <p class="text-gray-700 dark:text-gray-300">
            以下のJSON-LDコードをHTMLの<code class="px-2 py-1 bg-gray-100 dark:bg-gray-800 rounded">&lt;head&gt;</code>内に追加します：
          </p>

          <pre class="p-4 bg-gray-900 text-gray-100 rounded-lg overflow-x-auto text-sm"><code>{
  "@context": "https://schema.org",
  "@type": "Product",
  "name": "ワイヤレスヘッドホン WH-1000XM5",
  "image": "https://example.com/headphone.jpg",
  "description": "業界最高クラスのノイズキャンセリング性能",
  "brand": {
    "@type": "Brand",
    "name": "Sony"
  },
  "offers": {
    "@type": "Offer",
    "price": "45000",
    "priceCurrency": "JPY",
    "availability": "https://schema.org/InStock",
    "url": "https://example.com/product"
  },
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "4.8",
    "reviewCount": "1234"
  }
}</code></pre>

          <UAlert
            color="blue"
            variant="soft"
            icon="i-heroicons-information-circle"
            title="重要"
            description="画像は最低696px以上、できれば1200px以上の高解像度を推奨します"
          />
        </div>
      </UCard>

      <!-- Benefits -->
      <UCard class="bg-gradient-to-r from-blue-500 to-purple-600 text-white">
        <template #header>
          <h2 class="text-2xl font-bold">
            📈 商品リッチリザルトの効果
          </h2>
        </template>

        <div class="space-y-4">
          <div class="flex items-start gap-4">
            <div class="text-3xl">🎯</div>
            <div>
              <h3 class="text-xl font-bold mb-2">CTR 40%向上</h3>
              <p class="opacity-90">
                価格と評価が表示されることで、クリック率が大幅にアップ
              </p>
            </div>
          </div>

          <div class="flex items-start gap-4">
            <div class="text-3xl">💎</div>
            <div>
              <h3 class="text-xl font-bold mb-2">質の高いトラフィック</h3>
              <p class="opacity-90">
                価格を見て興味を持ったユーザーだけがクリックするため、CVRも向上
              </p>
            </div>
          </div>

          <div class="flex items-start gap-4">
            <div class="text-3xl">🏆</div>
            <div>
              <h3 class="text-xl font-bold mb-2">競合と差別化</h3>
              <p class="opacity-90">
                同じ検索結果でリッチリザルトがある方が圧倒的に目立つ
              </p>
            </div>
          </div>
        </div>
      </UCard>

      <!-- Requirements -->
      <UCard class="bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm">
        <template #header>
          <h2 class="text-2xl font-bold text-gray-900 dark:text-white">
            ✅ 必須フィールド
          </h2>
        </template>

        <div class="space-y-3">
          <div class="flex items-center gap-3">
            <UBadge color="red" variant="solid">必須</UBadge>
            <span class="text-gray-900 dark:text-white font-semibold">name</span>
            <span class="text-gray-600 dark:text-gray-400">- 商品名</span>
          </div>

          <div class="flex items-center gap-3">
            <UBadge color="red" variant="solid">必須</UBadge>
            <span class="text-gray-900 dark:text-white font-semibold">image</span>
            <span class="text-gray-600 dark:text-gray-400">- 商品画像URL</span>
          </div>

          <div class="flex items-center gap-3">
            <UBadge color="orange" variant="solid">推奨</UBadge>
            <span class="text-gray-900 dark:text-white font-semibold">offers.price</span>
            <span class="text-gray-600 dark:text-gray-400">- 価格</span>
          </div>

          <div class="flex items-center gap-3">
            <UBadge color="orange" variant="solid">推奨</UBadge>
            <span class="text-gray-900 dark:text-white font-semibold">aggregateRating</span>
            <span class="text-gray-600 dark:text-gray-400">- 評価情報</span>
          </div>

          <div class="flex items-center gap-3">
            <UBadge color="gray" variant="solid">任意</UBadge>
            <span class="text-gray-900 dark:text-white font-semibold">brand</span>
            <span class="text-gray-600 dark:text-gray-400">- ブランド名</span>
          </div>
        </div>
      </UCard>

      <!-- Testing -->
      <div class="text-center py-8 bg-gradient-to-r from-green-100 to-blue-100 dark:from-green-950 dark:to-blue-950 rounded-2xl">
        <h2 class="text-2xl font-bold text-gray-900 dark:text-white mb-4">
          🧪 実装後はテストを忘れずに
        </h2>
        <p class="text-gray-700 dark:text-gray-300 mb-6">
          Googleの公式テストツールで確認しましょう
        </p>
        <UButton
          to="https://search.google.com/test/rich-results"
          target="_blank"
          size="lg"
          color="green"
        >
          リッチリザルトテストを開く →
        </UButton>
      </div>
    </div>
  </UContainer>
</template>

<script setup lang="ts">
useHead({
  title: '商品リッチリザルト - Google検索でCTR 40%向上',
  meta: [
    {
      name: 'description',
      content: '商品リッチリザルトの実装方法と効果を詳しく解説。価格・評価・在庫状況を検索結果に表示してCTRを大幅に向上させる方法。'
    }
  ]
})
</script>
