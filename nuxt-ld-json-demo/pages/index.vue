<template>
  <UContainer>
    <div class="space-y-8">
      <!-- Hero Section -->
      <UCard>
        <div class="text-center py-12">
          <div class="text-6xl mb-6">🔍</div>
          <h1 class="text-4xl font-bold text-gray-900 dark:text-white mb-4">
            application/ld+json
          </h1>
          <p class="text-xl text-gray-600 dark:text-gray-300 max-w-2xl mx-auto mb-6">
            構造化データで検索エンジンと会話する技術
          </p>
          <div class="flex gap-4 justify-center flex-wrap">
            <UBadge color="primary" variant="subtle" size="lg">
              Nuxt 3
            </UBadge>
            <UBadge color="primary" variant="subtle" size="lg">
              Nuxt UI
            </UBadge>
            <UBadge color="primary" variant="subtle" size="lg">
              Schema.org
            </UBadge>
          </div>
        </div>
      </UCard>

      <!-- What is JSON-LD -->
      <UCard>
        <template #header>
          <h2 class="text-2xl font-bold text-gray-900 dark:text-white">
            JSON-LD とは？
          </h2>
        </template>

        <div class="space-y-4">
          <p class="text-gray-700 dark:text-gray-300">
            <strong>JSON-LD (JSON for Linking Data)</strong> は、Webページの内容を機械可読な形式で記述する標準フォーマットです。
            検索エンジンがページの内容を正確に理解し、より豊かな検索結果を提供するために使用されます。
          </p>

          <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mt-6">
            <div class="p-4 bg-primary-50 dark:bg-primary-950 rounded-lg">
              <h3 class="font-semibold text-primary-700 dark:text-primary-300 mb-2">
                リッチスニペット
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                検索結果に星評価や価格を表示
              </p>
            </div>

            <div class="p-4 bg-green-50 dark:bg-green-950 rounded-lg">
              <h3 class="font-semibold text-green-700 dark:text-green-300 mb-2">
                SEO改善
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                Googleが内容を正確に理解
              </p>
            </div>

            <div class="p-4 bg-purple-50 dark:bg-purple-950 rounded-lg">
              <h3 class="font-semibold text-purple-700 dark:text-purple-300 mb-2">
                音声検索対応
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                AlexaやGoogleアシスタント対応
              </p>
            </div>

            <div class="p-4 bg-orange-50 dark:bg-orange-950 rounded-lg">
              <h3 class="font-semibold text-orange-700 dark:text-orange-300 mb-2">
                信頼性向上
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                正確な情報提供で信頼獲得
              </p>
            </div>
          </div>
        </div>
      </UCard>

      <!-- Basic Structure -->
      <UCard>
        <template #header>
          <h2 class="text-2xl font-bold text-gray-900 dark:text-white">
            基本構造
          </h2>
        </template>

        <div class="space-y-4">
          <p class="text-gray-700 dark:text-gray-300">
            HTMLの<code class="px-2 py-1 bg-gray-100 dark:bg-gray-800 rounded text-sm">&lt;script&gt;</code>タグ内に記述します：
          </p>

          <pre class="p-4 bg-gray-900 text-gray-100 rounded-lg overflow-x-auto"><code>&lt;script type="application/ld+json"&gt;
{
  "@context": "https://schema.org",
  "@type": "Product",
  "name": "商品名",
  "description": "商品の説明"
}
&lt;/script&gt;</code></pre>

          <UAlert
            icon="i-heroicons-information-circle"
            color="primary"
            variant="soft"
            title="重要なキー"
            description="@context: 語彙の定義元 (ほぼ常に https://schema.org) / @type: データの種類 (Product, Article, Personなど)"
          />
        </div>
      </UCard>

      <!-- Examples Grid -->
      <div>
        <h2 class="text-2xl font-bold text-gray-900 dark:text-white mb-6">
          実践例
        </h2>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
          <UCard
            class="hover:shadow-lg transition-shadow cursor-pointer"
            @click="navigateTo('/product')"
          >
            <div class="text-center">
              <div class="text-5xl mb-4">🛍️</div>
              <h3 class="text-xl font-bold text-gray-900 dark:text-white mb-2">
                商品 (Product)
              </h3>
              <p class="text-gray-600 dark:text-gray-400 mb-4">
                商品名、価格、評価、在庫状況などを構造化
              </p>
              <UButton color="primary" variant="soft" block>
                詳しく見る →
              </UButton>
            </div>
          </UCard>

          <UCard
            class="hover:shadow-lg transition-shadow cursor-pointer"
            @click="navigateTo('/article')"
          >
            <div class="text-center">
              <div class="text-5xl mb-4">📝</div>
              <h3 class="text-xl font-bold text-gray-900 dark:text-white mb-2">
                記事 (Article)
              </h3>
              <p class="text-gray-600 dark:text-gray-400 mb-4">
                ブログ記事、ニュース記事の構造化データ
              </p>
              <UButton color="primary" variant="soft" block>
                詳しく見る →
              </UButton>
            </div>
          </UCard>

          <UCard
            class="hover:shadow-lg transition-shadow cursor-pointer"
            @click="navigateTo('/restaurant')"
          >
            <div class="text-center">
              <div class="text-5xl mb-4">🍽️</div>
              <h3 class="text-xl font-bold text-gray-900 dark:text-white mb-2">
                レストラン (Restaurant)
              </h3>
              <p class="text-gray-600 dark:text-gray-400 mb-4">
                店舗情報、営業時間、評価、料理ジャンル
              </p>
              <UButton color="primary" variant="soft" block>
                詳しく見る →
              </UButton>
            </div>
          </UCard>

          <UCard
            class="hover:shadow-lg transition-shadow cursor-pointer"
            @click="navigateTo('/event')"
          >
            <div class="text-center">
              <div class="text-5xl mb-4">🎫</div>
              <h3 class="text-xl font-bold text-gray-900 dark:text-white mb-2">
                イベント (Event)
              </h3>
              <p class="text-gray-600 dark:text-gray-400 mb-4">
                開催日時、場所、チケット価格、主催者情報
              </p>
              <UButton color="primary" variant="soft" block>
                詳しく見る →
              </UButton>
            </div>
          </UCard>
        </div>
      </div>

      <!-- Benefits -->
      <UCard>
        <template #header>
          <h2 class="text-2xl font-bold text-gray-900 dark:text-white">
            導入するメリット
          </h2>
        </template>

        <div class="space-y-3">
          <div class="flex items-start gap-3">
            <div class="text-2xl">📈</div>
            <div>
              <h3 class="font-semibold text-gray-900 dark:text-white">
                CTR向上
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                星評価表示で平均30%クリック率アップ
              </p>
            </div>
          </div>

          <div class="flex items-start gap-3">
            <div class="text-2xl">🔍</div>
            <div>
              <h3 class="font-semibold text-gray-900 dark:text-white">
                検索順位改善
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                Googleが内容を正確に理解し、適切にランキング
              </p>
            </div>
          </div>

          <div class="flex items-start gap-3">
            <div class="text-2xl">🎤</div>
            <div>
              <h3 class="font-semibold text-gray-900 dark:text-white">
                音声検索最適化
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                スマートスピーカーで読み上げられる
              </p>
            </div>
          </div>

          <div class="flex items-start gap-3">
            <div class="text-2xl">✨</div>
            <div>
              <h3 class="font-semibold text-gray-900 dark:text-white">
                ナレッジグラフ表示
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                検索結果右側の情報カードに表示される可能性
              </p>
            </div>
          </div>
        </div>
      </UCard>

      <!-- Testing Tools -->
      <UCard>
        <template #header>
          <h2 class="text-2xl font-bold text-gray-900 dark:text-white">
            テストツール
          </h2>
        </template>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
          <a
            href="https://search.google.com/test/rich-results"
            target="_blank"
            class="block p-4 border border-gray-200 dark:border-gray-700 rounded-lg hover:border-primary-500 transition-colors"
          >
            <h3 class="font-semibold text-gray-900 dark:text-white mb-2">
              Google リッチリザルトテスト
            </h3>
            <p class="text-sm text-gray-600 dark:text-gray-400 mb-3">
              Googleでの表示を確認
            </p>
            <UButton color="primary" variant="outline" size="sm">
              テストする →
            </UButton>
          </a>

          <a
            href="https://validator.schema.org/"
            target="_blank"
            class="block p-4 border border-gray-200 dark:border-gray-700 rounded-lg hover:border-primary-500 transition-colors"
          >
            <h3 class="font-semibold text-gray-900 dark:text-white mb-2">
              Schema Markup Validator
            </h3>
            <p class="text-sm text-gray-600 dark:text-gray-400 mb-3">
              Schema.orgの公式検証ツール
            </p>
            <UButton color="primary" variant="outline" size="sm">
              検証する →
            </UButton>
          </a>
        </div>
      </UCard>
    </div>
  </UContainer>
</template>

<script setup lang="ts">
// ページのメタデータ
useHead({
  title: 'JSON-LD デモ - 構造化データの実践ガイド',
  meta: [
    {
      name: 'description',
      content: 'Nuxt 3とNuxt UIで学ぶapplication/ld+jsonの実装方法。商品、記事、レストラン、イベントなど実践的な例を紹介。'
    }
  ]
})

// WebPageの構造化データ
useHead({
  script: [
    {
      type: 'application/ld+json',
      innerHTML: JSON.stringify({
        '@context': 'https://schema.org',
        '@type': 'WebSite',
        'name': 'JSON-LD Demo',
        'description': '構造化データ（application/ld+json）の実践的なデモサイト',
        'url': 'https://example.com',
        'potentialAction': {
          '@type': 'SearchAction',
          'target': 'https://example.com/search?q={search_term_string}',
          'query-input': 'required name=search_term_string'
        }
      })
    }
  ]
})
</script>
