<template>
  <UContainer>
    <div class="space-y-12">
      <!-- Hero Section -->
      <div class="text-center py-12">
        <div class="text-8xl mb-6 animate-bounce">✨</div>
        <h1 class="text-5xl font-bold bg-gradient-to-r from-blue-600 via-purple-600 to-pink-600 dark:from-blue-400 dark:via-purple-400 dark:to-pink-400 bg-clip-text text-transparent mb-4">
          Googleリッチリザルト
        </h1>
        <p class="text-xl text-gray-700 dark:text-gray-300 max-w-3xl mx-auto mb-8">
          検索結果を**劇的に目立たせる**、Googleの最強機能
        </p>
        <div class="flex gap-4 justify-center flex-wrap">
          <UBadge color="blue" variant="subtle" size="lg">CTR 30%アップ</UBadge>
          <UBadge color="purple" variant="subtle" size="lg">SEO効果大</UBadge>
          <UBadge color="pink" variant="subtle" size="lg">無料で使える</UBadge>
        </div>
      </div>

      <!-- What is Rich Results -->
      <UCard class="bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm">
        <template #header>
          <h2 class="text-3xl font-bold text-gray-900 dark:text-white">
            🤔 リッチリザルトとは？
          </h2>
        </template>

        <div class="space-y-6">
          <p class="text-lg text-gray-700 dark:text-gray-300">
            リッチリザルト（Rich Results）とは、<strong>Google検索結果に表示される、通常の青いリンクよりも視覚的に豊かな表示</strong>のことです。
          </p>

          <!-- Comparison -->
          <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
            <!-- Normal Result -->
            <div class="border-2 border-red-300 dark:border-red-700 rounded-lg p-6 bg-white dark:bg-gray-900">
              <div class="text-red-600 dark:text-red-400 font-semibold mb-3 flex items-center gap-2">
                <span>❌</span>
                <span>通常の検索結果</span>
              </div>
              <div>
                <div class="text-blue-600 dark:text-blue-400 text-lg mb-1">
                  おいしいカレーの作り方
                </div>
                <div class="text-green-700 dark:text-green-400 text-xs mb-2">
                  https://example.com/curry-recipe
                </div>
                <div class="text-gray-600 dark:text-gray-400 text-sm">
                  スパイスから作る本格カレーのレシピをご紹介します。玉ねぎをじっくり炒めて、トマトとスパイスで煮込んだ...
                </div>
              </div>
            </div>

            <!-- Rich Result -->
            <div class="border-2 border-green-400 dark:border-green-600 rounded-lg p-6 bg-gradient-to-br from-green-50 to-blue-50 dark:from-green-950 dark:to-blue-950">
              <div class="text-green-600 dark:text-green-400 font-semibold mb-3 flex items-center gap-2">
                <span>✅</span>
                <span>リッチリザルト</span>
              </div>
              <div>
                <div class="flex gap-4">
                  <div class="w-20 h-20 bg-orange-200 dark:bg-orange-800 rounded-lg flex items-center justify-center text-3xl">
                    🍛
                  </div>
                  <div class="flex-1">
                    <div class="text-blue-600 dark:text-blue-400 text-lg mb-1">
                      おいしいカレーの作り方
                    </div>
                    <div class="flex items-center gap-2 mb-2">
                      <div class="flex text-yellow-400">
                        ★★★★★
                      </div>
                      <span class="text-sm text-gray-600 dark:text-gray-400">4.8 (234件)</span>
                    </div>
                    <div class="flex gap-3 text-sm text-gray-700 dark:text-gray-300">
                      <span>⏱️ 45分</span>
                      <span>🔥 320kcal</span>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <UAlert
            color="blue"
            variant="soft"
            icon="i-heroicons-light-bulb"
            title="ポイント"
            description="リッチリザルトは画像・星評価・価格などが表示され、クリック率が大幅にアップします"
          />
        </div>
      </UCard>

      <!-- Types of Rich Results -->
      <div>
        <h2 class="text-3xl font-bold text-gray-900 dark:text-white mb-6 text-center">
          📚 リッチリザルトの種類
        </h2>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          <UCard
            class="hover:shadow-2xl transition-all cursor-pointer transform hover:scale-105 bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm"
            @click="navigateTo('/product')"
          >
            <div class="text-center">
              <div class="text-6xl mb-4">🛍️</div>
              <h3 class="text-xl font-bold text-gray-900 dark:text-white mb-2">
                商品リッチリザルト
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400 mb-4">
                価格・在庫・評価を表示
              </p>
              <UBadge color="green" variant="subtle">
                CTR +40%
              </UBadge>
            </div>
          </UCard>

          <UCard
            class="hover:shadow-2xl transition-all cursor-pointer transform hover:scale-105 bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm"
            @click="navigateTo('/recipe')"
          >
            <div class="text-center">
              <div class="text-6xl mb-4">🍳</div>
              <h3 class="text-xl font-bold text-gray-900 dark:text-white mb-2">
                レシピリッチリザルト
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400 mb-4">
                調理時間・カロリー・評価
              </p>
              <UBadge color="orange" variant="subtle">
                料理サイト必須
              </UBadge>
            </div>
          </UCard>

          <UCard
            class="hover:shadow-2xl transition-all cursor-pointer transform hover:scale-105 bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm"
            @click="navigateTo('/faq')"
          >
            <div class="text-center">
              <div class="text-6xl mb-4">❓</div>
              <h3 class="text-xl font-bold text-gray-900 dark:text-white mb-2">
                FAQリッチリザルト
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400 mb-4">
                Q&Aが検索結果に展開表示
              </p>
              <UBadge color="blue" variant="subtle">
                簡単実装
              </UBadge>
            </div>
          </UCard>

          <UCard class="bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm">
            <div class="text-center">
              <div class="text-6xl mb-4">📰</div>
              <h3 class="text-xl font-bold text-gray-900 dark:text-white mb-2">
                記事リッチリザルト
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400 mb-4">
                著者・公開日・画像を表示
              </p>
              <UBadge color="purple" variant="subtle">
                ブログ推奨
              </UBadge>
            </div>
          </UCard>

          <UCard class="bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm">
            <div class="text-center">
              <div class="text-6xl mb-4">🎬</div>
              <h3 class="text-xl font-bold text-gray-900 dark:text-white mb-2">
                動画リッチリザルト
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400 mb-4">
                サムネイル・再生時間
              </p>
              <UBadge color="red" variant="subtle">
                動画サイト向け
              </UBadge>
            </div>
          </UCard>

          <UCard class="bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm">
            <div class="text-center">
              <div class="text-6xl mb-4">🎫</div>
              <h3 class="text-xl font-bold text-gray-900 dark:text-white mb-2">
                イベントリッチリザルト
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400 mb-4">
                日時・場所・チケット価格
              </p>
              <UBadge color="pink" variant="subtle">
                イベント必須
              </UBadge>
            </div>
          </UCard>
        </div>
      </div>

      <!-- Benefits -->
      <UCard class="bg-gradient-to-r from-blue-500 to-purple-600 text-white">
        <template #header>
          <h2 class="text-3xl font-bold">
            🎁 リッチリザルトのメリット
          </h2>
        </template>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
          <div class="flex items-start gap-4">
            <div class="text-4xl">📈</div>
            <div>
              <h3 class="text-xl font-bold mb-2">CTR（クリック率）が大幅アップ</h3>
              <p class="opacity-90">
                星評価や画像が表示されることで、平均30-40%クリック率が向上します
              </p>
            </div>
          </div>

          <div class="flex items-start gap-4">
            <div class="text-4xl">👁️</div>
            <div>
              <h3 class="text-xl font-bold mb-2">検索結果で圧倒的に目立つ</h3>
              <p class="opacity-90">
                通常の青いリンクの中で、リッチリザルトは一際目立ちます
              </p>
            </div>
          </div>

          <div class="flex items-start gap-4">
            <div class="text-4xl">🎯</div>
            <div>
              <h3 class="text-xl font-bold mb-2">ターゲットユーザーが増える</h3>
              <p class="opacity-90">
                詳細情報が表示されることで、本当に興味のあるユーザーがクリック
              </p>
            </div>
          </div>

          <div class="flex items-start gap-4">
            <div class="text-4xl">💰</div>
            <div>
              <h3 class="text-xl font-bold mb-2">無料で使える</h3>
              <p class="opacity-90">
                構造化データを実装するだけ。広告費は一切不要です
              </p>
            </div>
          </div>

          <div class="flex items-start gap-4">
            <div class="text-4xl">🌐</div>
            <div>
              <h3 class="text-xl font-bold mb-2">Googleが公式サポート</h3>
              <p class="opacity-90">
                Googleが推奨している正式な機能なので安心して使えます
              </p>
            </div>
          </div>

          <div class="flex items-start gap-4">
            <div class="text-4xl">📱</div>
            <div>
              <h3 class="text-xl font-bold mb-2">モバイルで特に効果的</h3>
              <p class="opacity-90">
                スマホ画面で情報が一目で分かり、ユーザー体験が向上
              </p>
            </div>
          </div>
        </div>
      </UCard>

      <!-- How it Works -->
      <UCard class="bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm">
        <template #header>
          <h2 class="text-3xl font-bold text-gray-900 dark:text-white">
            ⚙️ リッチリザルトの仕組み
          </h2>
        </template>

        <div class="space-y-6">
          <div class="flex items-start gap-4">
            <div class="flex-shrink-0 w-12 h-12 bg-blue-100 dark:bg-blue-900 rounded-full flex items-center justify-center text-xl font-bold text-blue-600 dark:text-blue-300">
              1
            </div>
            <div class="flex-1">
              <h3 class="text-lg font-semibold text-gray-900 dark:text-white mb-2">
                構造化データ（JSON-LD）を追加
              </h3>
              <p class="text-gray-600 dark:text-gray-400">
                ページのHTMLに、機械可読な形式でデータを記述します
              </p>
            </div>
          </div>

          <div class="flex items-start gap-4">
            <div class="flex-shrink-0 w-12 h-12 bg-purple-100 dark:bg-purple-900 rounded-full flex items-center justify-center text-xl font-bold text-purple-600 dark:text-purple-300">
              2
            </div>
            <div class="flex-1">
              <h3 class="text-lg font-semibold text-gray-900 dark:text-white mb-2">
                Googleがクロール・解析
              </h3>
              <p class="text-gray-600 dark:text-gray-400">
                Googlebotがページを訪問し、構造化データを読み取ります
              </p>
            </div>
          </div>

          <div class="flex items-start gap-4">
            <div class="flex-shrink-0 w-12 h-12 bg-green-100 dark:bg-green-900 rounded-full flex items-center justify-center text-xl font-bold text-green-600 dark:text-green-300">
              3
            </div>
            <div class="flex-1">
              <h3 class="text-lg font-semibold text-gray-900 dark:text-white mb-2">
                リッチリザルトとして表示
              </h3>
              <p class="text-gray-600 dark:text-gray-400">
                検索結果に豊かな情報が表示されるようになります
              </p>
            </div>
          </div>
        </div>
      </UCard>

      <!-- Call to Action -->
      <div class="text-center py-12 bg-gradient-to-r from-pink-100 via-purple-100 to-blue-100 dark:from-pink-950 dark:via-purple-950 dark:to-blue-950 rounded-2xl">
        <h2 class="text-3xl font-bold text-gray-900 dark:text-white mb-4">
          🚀 今すぐ始めよう
        </h2>
        <p class="text-lg text-gray-700 dark:text-gray-300 mb-8 max-w-2xl mx-auto">
          各ページで具体的な実装方法と実例を確認できます
        </p>
        <div class="flex gap-4 justify-center flex-wrap">
          <UButton to="/product" size="lg" color="blue">
            商品リッチリザルトを見る
          </UButton>
          <UButton to="/recipe" size="lg" color="orange" variant="outline">
            レシピリッチリザルトを見る
          </UButton>
          <UButton to="/faq" size="lg" color="purple" variant="outline">
            FAQリッチリザルトを見る
          </UButton>
        </div>
      </div>
    </div>
  </UContainer>
</template>

<script setup lang="ts">
useHead({
  title: 'Googleリッチリザルト完全ガイド',
  meta: [
    {
      name: 'description',
      content: 'Googleリッチリザルトの種類、メリット、実装方法を分かりやすく解説。検索結果のCTRを30%以上向上させる方法を学びましょう。'
    }
  ]
})
</script>
