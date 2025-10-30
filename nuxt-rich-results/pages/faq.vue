<template>
  <UContainer>
    <div class="space-y-8">
      <!-- Header -->
      <div class="text-center">
        <div class="text-7xl mb-4">❓</div>
        <h1 class="text-4xl font-bold text-gray-900 dark:text-white mb-4">
          FAQリッチリザルト
        </h1>
        <p class="text-lg text-gray-600 dark:text-gray-300 max-w-2xl mx-auto">
          <strong>最も簡単に実装できる</strong>リッチリザルト
        </p>
      </div>

      <!-- Visual Example -->
      <UCard class="bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm">
        <template #header>
          <h2 class="text-2xl font-bold text-gray-900 dark:text-white">
            📱 Google検索結果での表示例
          </h2>
        </template>

        <div class="border-2 border-purple-300 dark:border-purple-700 rounded-xl p-6 bg-gradient-to-br from-purple-50 to-blue-50 dark:from-purple-950 dark:to-blue-950">
          <!-- FAQ Item -->
          <div class="space-y-4">
            <div class="text-blue-600 dark:text-blue-400 text-xl font-medium mb-4">
              リッチリザルトについてよくある質問 - Example.com
            </div>

            <!-- Question 1 -->
            <div class="border-l-4 border-purple-500 pl-4 py-2">
              <div class="font-semibold text-gray-900 dark:text-white mb-2 flex items-center gap-2">
                <span class="text-purple-600 dark:text-purple-400">Q:</span>
                リッチリザルトとは何ですか？
              </div>
              <div class="text-gray-700 dark:text-gray-300 text-sm">
                リッチリザルトは、Google検索結果に表示される視覚的に豊かな情報です。価格、評価、画像などが表示されます。
              </div>
            </div>

            <!-- Question 2 -->
            <div class="border-l-4 border-blue-500 pl-4 py-2">
              <div class="font-semibold text-gray-900 dark:text-white mb-2 flex items-center gap-2">
                <span class="text-blue-600 dark:text-blue-400">Q:</span>
                実装は難しいですか？
              </div>
              <div class="text-gray-700 dark:text-gray-300 text-sm">
                いいえ。HTMLにJSON-LDを追加するだけで、数分で実装できます。プログラミングの知識は必要ありません。
              </div>
            </div>

            <!-- Question 3 -->
            <div class="border-l-4 border-green-500 pl-4 py-2">
              <div class="font-semibold text-gray-900 dark:text-white mb-2 flex items-center gap-2">
                <span class="text-green-600 dark:text-green-400">Q:</span>
                効果はどれくらいですか？
              </div>
              <div class="text-gray-700 dark:text-gray-300 text-sm">
                平均してCTRが30-40%向上します。商品ページでは特に効果が高く、40%以上の改善も報告されています。
              </div>
            </div>
          </div>
        </div>
      </UCard>

      <!-- Key Features -->
      <UCard class="bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm">
        <template #header>
          <h2 class="text-2xl font-bold text-gray-900 dark:text-white">
            ✨ FAQリッチリザルトの特徴
          </h2>
        </template>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
          <div class="text-center p-4 bg-purple-50 dark:bg-purple-950 rounded-lg">
            <div class="text-4xl mb-3">⚡</div>
            <h3 class="font-semibold text-gray-900 dark:text-white mb-2">実装が簡単</h3>
            <p class="text-sm text-gray-600 dark:text-gray-400">
              Q&Aを追加するだけ
            </p>
          </div>

          <div class="text-center p-4 bg-blue-50 dark:bg-blue-950 rounded-lg">
            <div class="text-4xl mb-3">📊</div>
            <h3 class="font-semibold text-gray-900 dark:text-white mb-2">スペース拡大</h3>
            <p class="text-sm text-gray-600 dark:text-gray-400">
              検索結果の占有率アップ
            </p>
          </div>

          <div class="text-center p-4 bg-green-50 dark:bg-green-950 rounded-lg">
            <div class="text-4xl mb-3">🎯</div>
            <h3 class="font-semibold text-gray-900 dark:text-white mb-2">信頼性向上</h3>
            <p class="text-sm text-gray-600 dark:text-gray-400">
              事前に疑問を解消
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

        <div class="space-y-4">
          <p class="text-gray-700 dark:text-gray-300">
            FAQPageタイプを使って、Q&Aを構造化します：
          </p>

          <pre class="p-4 bg-gray-900 text-gray-100 rounded-lg overflow-x-auto text-sm"><code>{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "リッチリザルトとは何ですか？",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "リッチリザルトは、Google検索結果に表示される視覚的に豊かな情報です。"
      }
    },
    {
      "@type": "Question",
      "name": "実装は難しいですか？",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "いいえ。HTMLにJSON-LDを追加するだけで簡単に実装できます。"
      }
    },
    {
      "@type": "Question",
      "name": "効果はどれくらいですか？",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "平均してCTRが30-40%向上します。"
      }
    }
  ]
}</code></pre>

          <UAlert
            color="purple"
            variant="soft"
            icon="i-heroicons-sparkles"
            title="ポイント"
            description="質問と回答のペアを mainEntity 配列に追加していくだけで OK です"
          />
        </div>
      </UCard>

      <!-- Benefits -->
      <UCard class="bg-gradient-to-r from-purple-500 to-blue-600 text-white">
        <template #header>
          <h2 class="text-2xl font-bold">
            📈 FAQリッチリザルトの効果
          </h2>
        </template>

        <div class="space-y-4">
          <div class="flex items-start gap-4">
            <div class="text-3xl">📏</div>
            <div>
              <h3 class="text-xl font-bold mb-2">検索結果の占有スペース拡大</h3>
              <p class="opacity-90">
                Q&Aが展開表示され、他の検索結果を押し下げる効果
              </p>
            </div>
          </div>

          <div class="flex items-start gap-4">
            <div class="text-3xl">🛡️</div>
            <div>
              <h3 class="text-xl font-bold mb-2">信頼性とブランディング</h3>
              <p class="opacity-90">
                よくある質問に答えることで、専門性と信頼性をアピール
              </p>
            </div>
          </div>

          <div class="flex items-start gap-4">
            <div class="text-3xl">⚡</div>
            <div>
              <h3 class="text-xl font-bold mb-2">実装の簡単さ</h3>
              <p class="opacity-90">
                他のリッチリザルトと比べて、最も簡単に実装できる
              </p>
            </div>
          </div>
        </div>
      </UCard>

      <!-- Best Practices -->
      <UCard class="bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm">
        <template #header>
          <h2 class="text-2xl font-bold text-gray-900 dark:text-white">
            💡 ベストプラクティス
          </h2>
        </template>

        <div class="space-y-4">
          <div class="flex items-start gap-3">
            <div class="text-2xl">✅</div>
            <div>
              <h3 class="font-semibold text-gray-900 dark:text-white mb-1">
                実際のユーザーの質問を使う
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                カスタマーサポートやコメントで実際に聞かれる質問を使うと効果的
              </p>
            </div>
          </div>

          <div class="flex items-start gap-3">
            <div class="text-2xl">✅</div>
            <div>
              <h3 class="font-semibold text-gray-900 dark:text-white mb-1">
                回答は簡潔に（300文字以内推奨）
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                長すぎる回答は表示されない可能性があります
              </p>
            </div>
          </div>

          <div class="flex items-start gap-3">
            <div class="text-2xl">✅</div>
            <div>
              <h3 class="font-semibold text-gray-900 dark:text-white mb-1">
                最低3つ以上のQ&Aを用意
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                質問が少なすぎると表示されない場合があります
              </p>
            </div>
          </div>

          <div class="flex items-start gap-3">
            <div class="text-2xl">❌</div>
            <div>
              <h3 class="font-semibold text-gray-900 dark:text-white mb-1">
                広告的な内容は避ける
              </h3>
              <p class="text-sm text-gray-600 dark:text-gray-400">
                純粋な質問と回答の形式を保つ
              </p>
            </div>
          </div>
        </div>
      </UCard>

      <!-- Use Cases -->
      <div>
        <h2 class="text-2xl font-bold text-gray-900 dark:text-white mb-6 text-center">
          🎯 FAQリッチリザルトが効果的なケース
        </h2>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
          <UCard class="bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm">
            <div class="flex items-start gap-3">
              <div class="text-3xl">🏪</div>
              <div>
                <h3 class="font-semibold text-gray-900 dark:text-white mb-2">
                  ECサイト
                </h3>
                <p class="text-sm text-gray-600 dark:text-gray-400">
                  配送、返品、支払い方法などの質問
                </p>
              </div>
            </div>
          </UCard>

          <UCard class="bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm">
            <div class="flex items-start gap-3">
              <div class="text-3xl">💼</div>
              <div>
                <h3 class="font-semibold text-gray-900 dark:text-white mb-2">
                  サービスサイト
                </h3>
                <p class="text-sm text-gray-600 dark:text-gray-400">
                  料金プラン、契約方法、サポート体制
                </p>
              </div>
            </div>
          </UCard>

          <UCard class="bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm">
            <div class="flex items-start gap-3">
              <div class="text-3xl">🏥</div>
              <div>
                <h3 class="font-semibold text-gray-900 dark:text-white mb-2">
                  医療・健康
                </h3>
                <p class="text-sm text-gray-600 dark:text-gray-400">
                  症状、治療法、予防方法の質問
                </p>
              </div>
            </div>
          </UCard>

          <UCard class="bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm">
            <div class="flex items-start gap-3">
              <div class="text-3xl">📚</div>
              <div>
                <h3 class="font-semibold text-gray-900 dark:text-white mb-2">
                  教育サイト
                </h3>
                <p class="text-sm text-gray-600 dark:text-gray-400">
                  学習方法、カリキュラム、資格取得
                </p>
              </div>
            </div>
          </UCard>
        </div>
      </div>
    </div>
  </UContainer>
</template>

<script setup lang="ts">
useHead({
  title: 'FAQリッチリザルト - 最も簡単に実装できるリッチリザルト',
  meta: [
    {
      name: 'description',
      content: 'FAQリッチリザルトの実装方法。よくある質問を構造化して検索結果に表示し、CTRとユーザー体験を向上させる。'
    }
  ]
})
</script>
