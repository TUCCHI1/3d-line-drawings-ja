<template>
  <div class="min-h-screen">
    <UContainer class="py-12">
      <UButton to="/" icon="i-heroicons-arrow-left" class="mb-6">
        Back to Home
      </UButton>

      <div class="max-w-4xl mx-auto">
        <h1 class="text-4xl font-bold mb-6">リッチスニペット（Rich Snippets）とは？</h1>

        <UCard class="mb-8">
          <div class="prose dark:prose-invert max-w-none">
            <p class="text-lg">
              <strong>リッチスニペット</strong>（Rich Snippets）または<strong>リッチリザルト</strong>（Rich Results）とは、
              検索エンジンの検索結果ページに表示される、通常のタイトルとディスクリプション以外の<strong>追加情報</strong>のことです。
            </p>
            <p>
              JSON-LD形式で構造化データを提供することで、GoogleなどのサーチエンジンがWebページの内容を正確に理解し、
              検索結果に視覚的に魅力的な情報を表示できるようになります。
            </p>
          </div>
        </UCard>

        <h2 class="text-3xl font-bold mb-6">なぜ重要なのか？</h2>

        <div class="grid md:grid-cols-3 gap-4 mb-8">
          <UCard>
            <div class="flex items-start gap-3">
              <div class="text-2xl">👁️</div>
              <div>
                <h3 class="font-bold mb-2">視認性向上</h3>
                <p class="text-sm text-gray-600 dark:text-gray-400">
                  検索結果で目立ち、クリック率（CTR）が向上します
                </p>
              </div>
            </div>
          </UCard>

          <UCard>
            <div class="flex items-start gap-3">
              <div class="text-2xl">📊</div>
              <div>
                <h3 class="font-bold mb-2">情報の明確化</h3>
                <p class="text-sm text-gray-600 dark:text-gray-400">
                  ユーザーが求める情報を事前に提供できます
                </p>
              </div>
            </div>
          </UCard>

          <UCard>
            <div class="flex items-start gap-3">
              <div class="text-2xl">🎯</div>
              <div>
                <h3 class="font-bold mb-2">SEO効果</h3>
                <p class="text-sm text-gray-600 dark:text-gray-400">
                  検索エンジンがコンテンツを正確に理解できます
                </p>
              </div>
            </div>
          </UCard>
        </div>

        <h2 class="text-3xl font-bold mb-6">リッチスニペットの種類と表示例</h2>

        <div class="space-y-6">
          <!-- Recipe Rich Snippet -->
          <UCard>
            <div class="grid md:grid-cols-2 gap-6">
              <div>
                <div class="flex items-center gap-2 mb-3">
                  <UBadge color="orange">Recipe</UBadge>
                  <h3 class="text-xl font-bold">レシピ</h3>
                </div>
                <p class="text-gray-600 dark:text-gray-400 mb-4">
                  調理時間、カロリー、評価、レビュー数などが表示されます
                </p>
                <div class="space-y-2 text-sm">
                  <div class="flex items-center gap-2">
                    <span class="font-semibold">表示情報:</span>
                  </div>
                  <ul class="list-disc list-inside pl-4 space-y-1">
                    <li>調理時間・準備時間</li>
                    <li>星評価とレビュー数</li>
                    <li>カロリー情報</li>
                    <li>レシピ画像</li>
                  </ul>
                </div>
              </div>
              <div class="bg-gray-100 dark:bg-gray-800 p-4 rounded-lg">
                <div class="text-xs text-gray-500 mb-2">検索結果イメージ</div>
                <div class="bg-white dark:bg-gray-900 p-3 rounded border">
                  <div class="text-blue-600 text-sm font-semibold mb-1">本格カレーライスのレシピ</div>
                  <div class="flex items-center gap-2 mb-1">
                    <div class="flex text-yellow-400 text-xs">★★★★★</div>
                    <span class="text-xs text-gray-600">4.8 (127)</span>
                  </div>
                  <div class="text-xs text-gray-600 flex gap-3">
                    <span>⏱️ 60分</span>
                    <span>🔥 450 kcal</span>
                  </div>
                </div>
              </div>
            </div>
          </UCard>

          <!-- Product Rich Snippet -->
          <UCard>
            <div class="grid md:grid-cols-2 gap-6">
              <div>
                <div class="flex items-center gap-2 mb-3">
                  <UBadge color="blue">Product</UBadge>
                  <h3 class="text-xl font-bold">商品</h3>
                </div>
                <p class="text-gray-600 dark:text-gray-400 mb-4">
                  価格、在庫状況、レビュー評価などが表示されます
                </p>
                <div class="space-y-2 text-sm">
                  <div class="flex items-center gap-2">
                    <span class="font-semibold">表示情報:</span>
                  </div>
                  <ul class="list-disc list-inside pl-4 space-y-1">
                    <li>価格と通貨</li>
                    <li>在庫状況</li>
                    <li>レビュー評価</li>
                    <li>ブランド名</li>
                  </ul>
                </div>
              </div>
              <div class="bg-gray-100 dark:bg-gray-800 p-4 rounded-lg">
                <div class="text-xs text-gray-500 mb-2">検索結果イメージ</div>
                <div class="bg-white dark:bg-gray-900 p-3 rounded border">
                  <div class="text-blue-600 text-sm font-semibold mb-1">Nuxt 4 完全ガイドブック</div>
                  <div class="flex items-center gap-2 mb-1">
                    <div class="flex text-yellow-400 text-xs">★★★★★</div>
                    <span class="text-xs text-gray-600">4.8 (127)</span>
                  </div>
                  <div class="text-sm font-bold text-green-600">¥3,980</div>
                  <div class="text-xs text-green-600">在庫あり</div>
                </div>
              </div>
            </div>
          </UCard>

          <!-- Event Rich Snippet -->
          <UCard>
            <div class="grid md:grid-cols-2 gap-6">
              <div>
                <div class="flex items-center gap-2 mb-3">
                  <UBadge color="purple">Event</UBadge>
                  <h3 class="text-xl font-bold">イベント</h3>
                </div>
                <p class="text-gray-600 dark:text-gray-400 mb-4">
                  開催日時、場所、チケット価格などが表示されます
                </p>
                <div class="space-y-2 text-sm">
                  <div class="flex items-center gap-2">
                    <span class="font-semibold">表示情報:</span>
                  </div>
                  <ul class="list-disc list-inside pl-4 space-y-1">
                    <li>開催日時</li>
                    <li>開催場所</li>
                    <li>チケット価格</li>
                    <li>主催者情報</li>
                  </ul>
                </div>
              </div>
              <div class="bg-gray-100 dark:bg-gray-800 p-4 rounded-lg">
                <div class="text-xs text-gray-500 mb-2">検索結果イメージ</div>
                <div class="bg-white dark:bg-gray-900 p-3 rounded border">
                  <div class="text-blue-600 text-sm font-semibold mb-1">Nuxt 4 カンファレンス</div>
                  <div class="text-xs text-gray-600 space-y-1">
                    <div>📅 2025年11月15日 10:00 - 18:00</div>
                    <div>📍 東京コンベンションセンター</div>
                    <div>💴 ¥5,000</div>
                  </div>
                </div>
              </div>
            </div>
          </UCard>

          <!-- Article Rich Snippet -->
          <UCard>
            <div class="grid md:grid-cols-2 gap-6">
              <div>
                <div class="flex items-center gap-2 mb-3">
                  <UBadge color="green">Article</UBadge>
                  <h3 class="text-xl font-bold">記事</h3>
                </div>
                <p class="text-gray-600 dark:text-gray-400 mb-4">
                  公開日、著者、ヘッドライン画像などが表示されます
                </p>
                <div class="space-y-2 text-sm">
                  <div class="flex items-center gap-2">
                    <span class="font-semibold">表示情報:</span>
                  </div>
                  <ul class="list-disc list-inside pl-4 space-y-1">
                    <li>公開日・更新日</li>
                    <li>著者名</li>
                    <li>記事画像</li>
                    <li>キーワード</li>
                  </ul>
                </div>
              </div>
              <div class="bg-gray-100 dark:bg-gray-800 p-4 rounded-lg">
                <div class="text-xs text-gray-500 mb-2">検索結果イメージ</div>
                <div class="bg-white dark:bg-gray-900 p-3 rounded border">
                  <div class="text-blue-600 text-sm font-semibold mb-1">Nuxt 4.2の新機能ガイド</div>
                  <div class="text-xs text-gray-600 mb-1">
                    佐藤花子 · 2025年10月31日
                  </div>
                  <div class="text-xs text-gray-700 dark:text-gray-300">
                    Nuxt 4.2でJSON-LD構造化データを実装する方法を詳しく解説...
                  </div>
                </div>
              </div>
            </div>
          </UCard>
        </div>

        <USeparator class="my-8" />

        <UCard>
          <h2 class="text-2xl font-bold mb-4">実装方法</h2>
          <div class="prose dark:prose-invert max-w-none">
            <p>
              リッチスニペットを表示させるには、ページのHTMLに<code>&lt;script type="application/ld+json"&gt;</code>タグを使って
              JSON-LD形式の構造化データを埋め込みます。
            </p>
            <p>
              Nuxtアプリでは、<code>useHead()</code>コンポーザブルを使用して簡単に実装できます：
            </p>
          </div>

          <div class="bg-gray-900 text-gray-100 p-4 rounded-lg mt-4 overflow-x-auto">
            <pre class="text-sm"><code>useHead({
  script: [
    {
      type: 'application/ld+json',
      innerHTML: JSON.stringify({
        '@context': 'https://schema.org',
        '@type': 'Recipe',
        name: 'カレーライス',
        cookTime: 'PT40M',
        // ... その他のプロパティ
      })
    }
  ]
})</code></pre>
          </div>
        </UCard>

        <div class="mt-8 flex gap-4">
          <UButton to="/" size="lg" color="gray" variant="outline">
            ホームに戻る
          </UButton>
          <UButton
            to="https://developers.google.com/search/docs/appearance/structured-data/search-gallery"
            target="_blank"
            size="lg"
            trailing-icon="i-heroicons-arrow-top-right-on-square"
          >
            Google公式ドキュメント
          </UButton>
        </div>
      </div>
    </UContainer>
  </div>
</template>

<script setup lang="ts">
useHead({
  title: 'リッチスニペットとは'
})
</script>
