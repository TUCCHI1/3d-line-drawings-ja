<template>
  <UContainer>
    <div class="space-y-8">
      <!-- Header -->
      <div class="text-center">
        <div class="text-7xl mb-4">📊</div>
        <h1 class="text-4xl font-bold text-gray-900 dark:text-white mb-4">
          リッチリザルト比較表
        </h1>
        <p class="text-lg text-gray-600 dark:text-gray-300 max-w-2xl mx-auto">
          あなたのサイトに<strong>最適なリッチリザルト</strong>を見つけよう
        </p>
      </div>

      <!-- Comparison Table -->
      <UCard class="bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm overflow-x-auto">
        <template #header>
          <h2 class="text-2xl font-bold text-gray-900 dark:text-white">
            📋 主要リッチリザルトの比較
          </h2>
        </template>

        <div class="overflow-x-auto">
          <table class="w-full text-sm">
            <thead>
              <tr class="border-b-2 border-gray-300 dark:border-gray-700">
                <th class="text-left p-4 font-bold text-gray-900 dark:text-white">種類</th>
                <th class="text-left p-4 font-bold text-gray-900 dark:text-white">難易度</th>
                <th class="text-left p-4 font-bold text-gray-900 dark:text-white">CTR向上</th>
                <th class="text-left p-4 font-bold text-gray-900 dark:text-white">対象サイト</th>
                <th class="text-left p-4 font-bold text-gray-900 dark:text-white">主な表示情報</th>
              </tr>
            </thead>
            <tbody>
              <tr class="border-b border-gray-200 dark:border-gray-700 hover:bg-gray-50 dark:hover:bg-gray-800">
                <td class="p-4">
                  <div class="flex items-center gap-2">
                    <span class="text-2xl">🛍️</span>
                    <span class="font-semibold text-gray-900 dark:text-white">商品</span>
                  </div>
                </td>
                <td class="p-4">
                  <UBadge color="orange" variant="subtle">中</UBadge>
                </td>
                <td class="p-4">
                  <div class="flex items-center gap-1">
                    <span class="text-green-600 dark:text-green-400 font-bold">+40%</span>
                    <span class="text-2xl">📈</span>
                  </div>
                </td>
                <td class="p-4 text-gray-700 dark:text-gray-300">
                  ECサイト、製品ページ
                </td>
                <td class="p-4 text-gray-700 dark:text-gray-300">
                  価格、評価、在庫、画像
                </td>
              </tr>

              <tr class="border-b border-gray-200 dark:border-gray-700 hover:bg-gray-50 dark:hover:bg-gray-800">
                <td class="p-4">
                  <div class="flex items-center gap-2">
                    <span class="text-2xl">🍳</span>
                    <span class="font-semibold text-gray-900 dark:text-white">レシピ</span>
                  </div>
                </td>
                <td class="p-4">
                  <UBadge color="orange" variant="subtle">中</UBadge>
                </td>
                <td class="p-4">
                  <div class="flex items-center gap-1">
                    <span class="text-green-600 dark:text-green-400 font-bold">+35%</span>
                    <span class="text-2xl">📈</span>
                  </div>
                </td>
                <td class="p-4 text-gray-700 dark:text-gray-300">
                  料理ブログ、レシピサイト
                </td>
                <td class="p-4 text-gray-700 dark:text-gray-300">
                  調理時間、カロリー、評価
                </td>
              </tr>

              <tr class="border-b border-gray-200 dark:border-gray-700 hover:bg-gray-50 dark:hover:bg-gray-800">
                <td class="p-4">
                  <div class="flex items-center gap-2">
                    <span class="text-2xl">❓</span>
                    <span class="font-semibold text-gray-900 dark:text-white">FAQ</span>
                  </div>
                </td>
                <td class="p-4">
                  <UBadge color="green" variant="subtle">易</UBadge>
                </td>
                <td class="p-4">
                  <div class="flex items-center gap-1">
                    <span class="text-green-600 dark:text-green-400 font-bold">+30%</span>
                    <span class="text-2xl">📈</span>
                  </div>
                </td>
                <td class="p-4 text-gray-700 dark:text-gray-300">
                  全てのサイト
                </td>
                <td class="p-4 text-gray-700 dark:text-gray-300">
                  Q&A、よくある質問
                </td>
              </tr>

              <tr class="border-b border-gray-200 dark:border-gray-700 hover:bg-gray-50 dark:hover:bg-gray-800">
                <td class="p-4">
                  <div class="flex items-center gap-2">
                    <span class="text-2xl">📰</span>
                    <span class="font-semibold text-gray-900 dark:text-white">記事</span>
                  </div>
                </td>
                <td class="p-4">
                  <UBadge color="green" variant="subtle">易</UBadge>
                </td>
                <td class="p-4">
                  <div class="flex items-center gap-1">
                    <span class="text-green-600 dark:text-green-400 font-bold">+25%</span>
                    <span class="text-2xl">📈</span>
                  </div>
                </td>
                <td class="p-4 text-gray-700 dark:text-gray-300">
                  ブログ、ニュースサイト
                </td>
                <td class="p-4 text-gray-700 dark:text-gray-300">
                  著者、公開日、画像
                </td>
              </tr>

              <tr class="border-b border-gray-200 dark:border-gray-700 hover:bg-gray-50 dark:hover:bg-gray-800">
                <td class="p-4">
                  <div class="flex items-center gap-2">
                    <span class="text-2xl">🎬</span>
                    <span class="font-semibold text-gray-900 dark:text-white">動画</span>
                  </div>
                </td>
                <td class="p-4">
                  <UBadge color="orange" variant="subtle">中</UBadge>
                </td>
                <td class="p-4">
                  <div class="flex items-center gap-1">
                    <span class="text-green-600 dark:text-green-400 font-bold">+45%</span>
                    <span class="text-2xl">🚀</span>
                  </div>
                </td>
                <td class="p-4 text-gray-700 dark:text-gray-300">
                  動画サイト、チュートリアル
                </td>
                <td class="p-4 text-gray-700 dark:text-gray-300">
                  サムネイル、再生時間
                </td>
              </tr>

              <tr class="hover:bg-gray-50 dark:hover:bg-gray-800">
                <td class="p-4">
                  <div class="flex items-center gap-2">
                    <span class="text-2xl">🎫</span>
                    <span class="font-semibold text-gray-900 dark:text-white">イベント</span>
                  </div>
                </td>
                <td class="p-4">
                  <UBadge color="orange" variant="subtle">中</UBadge>
                </td>
                <td class="p-4">
                  <div class="flex items-center gap-1">
                    <span class="text-green-600 dark:text-green-400 font-bold">+38%</span>
                    <span class="text-2xl">📈</span>
                  </div>
                </td>
                <td class="p-4 text-gray-700 dark:text-gray-300">
                  イベントサイト、セミナー
                </td>
                <td class="p-4 text-gray-700 dark:text-gray-300">
                  日時、場所、チケット価格
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </UCard>

      <!-- Decision Guide -->
      <UCard class="bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm">
        <template #header>
          <h2 class="text-2xl font-bold text-gray-900 dark:text-white">
            🎯 どれを選ぶべき？
          </h2>
        </template>

        <div class="space-y-6">
          <!-- E-Commerce -->
          <div class="border-l-4 border-blue-500 pl-6 py-4 bg-blue-50 dark:bg-blue-950 rounded-r-lg">
            <div class="flex items-start gap-4">
              <div class="text-4xl">🛒</div>
              <div>
                <h3 class="text-xl font-bold text-gray-900 dark:text-white mb-2">
                  ECサイト・通販サイトなら
                </h3>
                <p class="text-gray-700 dark:text-gray-300 mb-3">
                  <strong>商品リッチリザルト</strong>が最優先。価格と評価が表示されることでCTRが40%向上します。
                </p>
                <UButton to="/product" color="blue" size="sm">
                  商品リッチリザルトを見る →
                </UButton>
              </div>
            </div>
          </div>

          <!-- Recipe Sites -->
          <div class="border-l-4 border-orange-500 pl-6 py-4 bg-orange-50 dark:bg-orange-950 rounded-r-lg">
            <div class="flex items-start gap-4">
              <div class="text-4xl">👨‍🍳</div>
              <div>
                <h3 class="text-xl font-bold text-gray-900 dark:text-white mb-2">
                  料理ブログ・レシピサイトなら
                </h3>
                <p class="text-gray-700 dark:text-gray-300 mb-3">
                  <strong>レシピリッチリザルト</strong>は必須。調理時間とカロリーが表示されユーザーの意思決定をサポート。
                </p>
                <UButton to="/recipe" color="orange" size="sm">
                  レシピリッチリザルトを見る →
                </UButton>
              </div>
            </div>
          </div>

          <!-- All Sites -->
          <div class="border-l-4 border-purple-500 pl-6 py-4 bg-purple-50 dark:bg-purple-950 rounded-r-lg">
            <div class="flex items-start gap-4">
              <div class="text-4xl">🌐</div>
              <div>
                <h3 class="text-xl font-bold text-gray-900 dark:text-white mb-2">
                  どんなサイトでも
                </h3>
                <p class="text-gray-700 dark:text-gray-300 mb-3">
                  <strong>FAQリッチリザルト</strong>は全てのサイトで使える万能型。実装も最も簡単。
                </p>
                <UButton to="/faq" color="purple" size="sm">
                  FAQリッチリザルトを見る →
                </UButton>
              </div>
            </div>
          </div>
        </div>
      </UCard>

      <!-- Implementation Priority -->
      <UCard class="bg-gradient-to-r from-green-500 to-teal-600 text-white">
        <template #header>
          <h2 class="text-2xl font-bold">
            ⚡ 実装の優先順位
          </h2>
        </template>

        <div class="space-y-4">
          <div class="flex items-start gap-4">
            <div class="flex-shrink-0 w-10 h-10 bg-white/20 rounded-full flex items-center justify-center font-bold text-xl">
              1
            </div>
            <div>
              <h3 class="text-xl font-bold mb-2">まずはFAQから</h3>
              <p class="opacity-90">
                最も簡単で、どんなサイトでも効果があります。まずはFAQページを作成しましょう。
              </p>
            </div>
          </div>

          <div class="flex items-start gap-4">
            <div class="flex-shrink-0 w-10 h-10 bg-white/20 rounded-full flex items-center justify-center font-bold text-xl">
              2
            </div>
            <div>
              <h3 class="text-xl font-bold mb-2">サイトの種類に応じて追加</h3>
              <p class="opacity-90">
                商品ページがあれば商品リッチリザルト、レシピがあればレシピリッチリザルトを追加。
              </p>
            </div>
          </div>

          <div class="flex items-start gap-4">
            <div class="flex-shrink-0 w-10 h-10 bg-white/20 rounded-full flex items-center justify-center font-bold text-xl">
              3
            </div>
            <div>
              <h3 class="text-xl font-bold mb-2">効果を測定して最適化</h3>
              <p class="opacity-90">
                Google Search Consoleで効果を確認し、より効果の高いリッチリザルトに注力しましょう。
              </p>
            </div>
          </div>
        </div>
      </UCard>

      <!-- Common Mistakes -->
      <UCard class="bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm">
        <template #header>
          <h2 class="text-2xl font-bold text-gray-900 dark:text-white">
            ⚠️ よくある失敗
          </h2>
        </template>

        <div class="space-y-4">
          <div class="flex items-start gap-3">
            <div class="text-2xl">❌</div>
            <div>
              <h3 class="font-semibold text-gray-900 dark:text-white mb-1">
                すべてのページに全てのリッチリザルトを実装
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                関係ないリッチリザルトを実装するとペナルティの可能性があります
              </p>
            </div>
          </div>

          <div class="flex items-start gap-3">
            <div class="text-2xl">❌</div>
            <div>
              <h3 class="font-semibold text-gray-900 dark:text-white mb-1">
                虚偽の情報を記載
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                実際のページ内容と異なる情報を構造化データに記載すると、Googleからペナルティを受けます
              </p>
            </div>
          </div>

          <div class="flex items-start gap-3">
            <div class="text-2xl">❌</div>
            <div>
              <h3 class="font-semibold text-gray-900 dark:text-white mb-1">
                テストせずに公開
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                必ずGoogleのリッチリザルトテストで検証してから公開しましょう
              </p>
            </div>
          </div>
        </div>
      </UCard>
    </div>
  </UContainer>
</template>

<script setup lang="ts">
useHead({
  title: 'リッチリザルト比較表 - あなたに最適なリッチリザルトを見つける',
  meta: [
    {
      name: 'description',
      content: '各リッチリザルトの特徴、難易度、効果を比較。あなたのサイトに最適なリッチリザルトを見つけて、検索結果のCTRを最大化しましょう。'
    }
  ]
})
</script>
