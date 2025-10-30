# Nuxt 3 + Nuxt UI 実装手順書

## 📋 目次
1. [プロジェクトセットアップ](#1-プロジェクトセットアップ)
2. [依存関係のインストール](#2-依存関係のインストール)
3. [プロジェクト構造の作成](#3-プロジェクト構造の作成)
4. [型定義の作成](#4-型定義の作成)
5. [Composables の実装](#5-composables-の実装)
6. [コンポーネントの実装](#6-コンポーネントの実装)
7. [ページの実装](#7-ページの実装)
8. [スタイリングとテーマ設定](#8-スタイリングとテーマ設定)
9. [テストと検証](#9-テストと検証)
10. [デプロイ準備](#10-デプロイ準備)

---

## 1. プロジェクトセットアップ

### 1.1 新規 Nuxt プロジェクトの作成

```bash
# プロジェクトディレクトリに移動（または新規作成）
cd /Users/tucch1/dev

# Nuxt 3 プロジェクトを作成
npx nuxi@latest init ld-json-demo-nuxt

# プロジェクトディレクトリに移動
cd ld-json-demo-nuxt
```

**選択肢が表示された場合:**
- Package manager: `npm` または `pnpm`（推奨）
- Initialize git repository: `Yes`

### 1.2 Git の初期化（まだの場合）

```bash
git init
git add .
git commit -m "Initial Nuxt 3 project setup"
```

---

## 2. 依存関係のインストール

### 2.1 Nuxt UI のインストール

```bash
npm install @nuxt/ui
```

### 2.2 その他の依存関係

```bash
# アイコンライブラリ（Nuxt UI で使用）
npm install @iconify-json/heroicons

# コードハイライト用
npm install shiki

# TypeScript型チェック（開発時）
npm install -D @nuxt/devtools
```

### 2.3 package.json の確認

以下が含まれているか確認:

```json
{
  "dependencies": {
    "@nuxt/ui": "^2.x.x",
    "nuxt": "^3.x.x"
  }
}
```

---

## 3. プロジェクト構造の作成

### 3.1 ディレクトリ構造を作成

```bash
# ディレクトリ作成
mkdir -p types
mkdir -p composables
mkdir -p components
mkdir -p pages
mkdir -p public/images
mkdir -p assets/css

# ファイル作成
touch types/schema.ts
touch composables/useLdJson.ts
touch components/FeatureCard.vue
touch components/CodePreview.vue
touch components/SchemaExample.vue
touch components/InfoBox.vue
touch pages/index.vue
touch assets/css/custom.css
```

### 3.2 最終的なディレクトリ構造

```
ld-json-demo-nuxt/
├── nuxt.config.ts
├── app.vue
├── types/
│   └── schema.ts
├── composables/
│   └── useLdJson.ts
├── components/
│   ├── FeatureCard.vue
│   ├── CodePreview.vue
│   ├── SchemaExample.vue
│   └── InfoBox.vue
├── pages/
│   └── index.vue
├── assets/
│   └── css/
│       └── custom.css
├── public/
│   └── images/
└── package.json
```

---

## 4. 型定義の作成

### 4.1 `types/schema.ts` の実装

**目的:** JSON-LD の型安全性を確保

```typescript
// types/schema.ts

/**
 * Schema.org の基本的な型定義
 */
export interface SchemaBase {
  '@context': string
  '@type': string
}

/**
 * Product Schema
 */
export interface ProductSchema extends SchemaBase {
  '@type': 'Product'
  name: string
  image?: string | string[]
  description?: string
  brand?: {
    '@type': 'Brand'
    name: string
  }
  offers?: OfferSchema
  aggregateRating?: AggregateRatingSchema
}

/**
 * Offer Schema
 */
export interface OfferSchema {
  '@type': 'Offer'
  price: string
  priceCurrency: string
  availability: string
  url?: string
}

/**
 * AggregateRating Schema
 */
export interface AggregateRatingSchema {
  '@type': 'AggregateRating'
  ratingValue: string
  reviewCount: string
}

/**
 * Article Schema
 */
export interface ArticleSchema extends SchemaBase {
  '@type': 'Article' | 'BlogPosting' | 'NewsArticle'
  headline: string
  image?: string | string[]
  datePublished: string
  dateModified?: string
  author: PersonSchema | OrganizationSchema
  publisher: OrganizationSchema
  description?: string
}

/**
 * Person Schema
 */
export interface PersonSchema {
  '@type': 'Person'
  name: string
  url?: string
  image?: string
  jobTitle?: string
  sameAs?: string[]
  worksFor?: OrganizationSchema
  alumniOf?: OrganizationSchema
  knowsAbout?: string[]
}

/**
 * Organization Schema
 */
export interface OrganizationSchema {
  '@type': 'Organization'
  name: string
  url?: string
  logo?: ImageObjectSchema
  sameAs?: string[]
}

/**
 * ImageObject Schema
 */
export interface ImageObjectSchema {
  '@type': 'ImageObject'
  url: string
  width?: string
  height?: string
}

/**
 * Restaurant Schema
 */
export interface RestaurantSchema extends SchemaBase {
  '@type': 'Restaurant'
  name: string
  image?: string | string[]
  address: PostalAddressSchema
  telephone?: string
  servesCuisine?: string
  priceRange?: string
  aggregateRating?: AggregateRatingSchema
  openingHours?: string[]
}

/**
 * PostalAddress Schema
 */
export interface PostalAddressSchema {
  '@type': 'PostalAddress'
  streetAddress: string
  addressLocality: string
  addressRegion: string
  postalCode: string
  addressCountry: string
}

/**
 * Event Schema
 */
export interface EventSchema extends SchemaBase {
  '@type': 'Event'
  name: string
  startDate: string
  endDate?: string
  eventAttendanceMode?: string
  eventStatus?: string
  location: PlaceSchema
  offers?: OfferSchema
  organizer?: OrganizationSchema
  description?: string
}

/**
 * Place Schema
 */
export interface PlaceSchema {
  '@type': 'Place'
  name: string
  address: PostalAddressSchema
}

/**
 * タブの型定義
 */
export interface SchemaTab {
  key: string
  label: string
  icon: string
  schema: SchemaBase
  description: string
}

/**
 * 機能カードの型定義
 */
export interface FeatureItem {
  icon: string
  title: string
  description: string
}
```

**実装ポイント:**
- すべての Schema に `@context` と `@type` を含める
- オプショナルなフィールドは `?` を使用
- 入れ子構造も適切に型定義

---

## 5. Composables の実装

### 5.1 `composables/useLdJson.ts` の実装

**目的:** JSON-LD データの管理とヘッダーへの挿入

```typescript
// composables/useLdJson.ts

import type { SchemaBase } from '~/types/schema'

/**
 * JSON-LD を管理する Composable
 */
export const useLdJson = () => {
  /**
   * JSON-LD を <head> に追加
   */
  const setLdJson = (schema: SchemaBase) => {
    useHead({
      script: [
        {
          type: 'application/ld+json',
          innerHTML: JSON.stringify(schema, null, 2),
        },
      ],
    })
  }

  /**
   * JSON-LD を文字列として取得（表示用）
   */
  const stringifyLdJson = (schema: SchemaBase): string => {
    return JSON.stringify(schema, null, 2)
  }

  /**
   * JSON-LD の検証（基本的なチェック）
   */
  const validateLdJson = (schema: SchemaBase): boolean => {
    if (!schema['@context']) {
      console.error('Missing @context')
      return false
    }
    if (!schema['@type']) {
      console.error('Missing @type')
      return false
    }
    return true
  }

  return {
    setLdJson,
    stringifyLdJson,
    validateLdJson,
  }
}

/**
 * サンプルデータを提供する Composable
 */
export const useSampleSchemas = () => {
  const productSchema = {
    '@context': 'https://schema.org',
    '@type': 'Product',
    name: 'ワイヤレスヘッドホン WH-1000XM5',
    image: 'https://example.com/headphone.jpg',
    description: '高音質ノイズキャンセリングヘッドホン',
    brand: {
      '@type': 'Brand',
      name: 'Sony',
    },
    offers: {
      '@type': 'Offer',
      price: '45000',
      priceCurrency: 'JPY',
      availability: 'https://schema.org/InStock',
    },
    aggregateRating: {
      '@type': 'AggregateRating',
      ratingValue: '4.8',
      reviewCount: '127',
    },
  }

  const articleSchema = {
    '@context': 'https://schema.org',
    '@type': 'Article',
    headline: 'JSON-LDの完全ガイド',
    image: 'https://example.com/article.jpg',
    datePublished: '2024-10-30',
    dateModified: '2024-10-30',
    author: {
      '@type': 'Person',
      name: '山田太郎',
      url: 'https://example.com/author',
    },
    publisher: {
      '@type': 'Organization',
      name: 'Tech Blog',
      logo: {
        '@type': 'ImageObject',
        url: 'https://example.com/logo.png',
      },
    },
    description: '構造化データの基礎から応用まで',
  }

  const restaurantSchema = {
    '@context': 'https://schema.org',
    '@type': 'Restaurant',
    name: '寿司処 まつもと',
    image: 'https://example.com/restaurant.jpg',
    address: {
      '@type': 'PostalAddress',
      streetAddress: '東京都渋谷区1-2-3',
      addressLocality: '渋谷区',
      addressRegion: '東京都',
      postalCode: '150-0001',
      addressCountry: 'JP',
    },
    telephone: '+81-3-1234-5678',
    servesCuisine: 'Japanese',
    priceRange: '¥¥¥',
    aggregateRating: {
      '@type': 'AggregateRating',
      ratingValue: '4.5',
      reviewCount: '89',
    },
    openingHours: [
      'Mo-Fr 11:30-14:00',
      'Mo-Fr 17:00-22:00',
      'Sa-Su 11:30-22:00',
    ],
  }

  const eventSchema = {
    '@context': 'https://schema.org',
    '@type': 'Event',
    name: 'Web技術カンファレンス 2024',
    startDate: '2024-12-15T09:00',
    endDate: '2024-12-15T18:00',
    eventAttendanceMode: 'https://schema.org/OfflineEventAttendanceMode',
    eventStatus: 'https://schema.org/EventScheduled',
    location: {
      '@type': 'Place',
      name: '東京国際フォーラム',
      address: {
        '@type': 'PostalAddress',
        streetAddress: '千代田区丸の内3-5-1',
        addressLocality: '千代田区',
        postalCode: '100-0005',
        addressCountry: 'JP',
      },
    },
    offers: {
      '@type': 'Offer',
      url: 'https://example.com/tickets',
      price: '5000',
      priceCurrency: 'JPY',
      availability: 'https://schema.org/InStock',
      validFrom: '2024-10-01',
    },
    organizer: {
      '@type': 'Organization',
      name: 'Web Tech Org',
      url: 'https://example.com',
    },
  }

  const personSchema = {
    '@context': 'https://schema.org',
    '@type': 'Person',
    name: '山田太郎',
    jobTitle: 'ソフトウェアエンジニア',
    image: 'https://example.com/profile.jpg',
    url: 'https://yamada-taro.example.com',
    sameAs: [
      'https://twitter.com/yamada_taro',
      'https://github.com/yamada-taro',
      'https://www.linkedin.com/in/yamada-taro',
    ],
    worksFor: {
      '@type': 'Organization',
      name: 'Tech Company Inc.',
    },
    alumniOf: {
      '@type': 'Organization',
      name: '東京大学',
    },
    knowsAbout: ['JavaScript', 'Python', 'Web開発'],
  }

  return {
    productSchema,
    articleSchema,
    restaurantSchema,
    eventSchema,
    personSchema,
  }
}
```

**実装ポイント:**
- `useHead()` で動的に JSON-LD を追加
- サンプルデータは実際の値を使用
- 検証機能を含める

---

## 6. コンポーネントの実装

### 6.1 `components/FeatureCard.vue`

**目的:** 機能紹介カード

```vue
<template>
  <UCard :ui="{ body: { padding: 'p-6' } }">
    <div class="flex flex-col items-center text-center space-y-3">
      <div
        class="w-12 h-12 rounded-full bg-gradient-to-br from-primary-500 to-purple-600 flex items-center justify-center"
      >
        <UIcon :name="icon" class="w-6 h-6 text-white" />
      </div>
      <h4 class="font-semibold text-lg">{{ title }}</h4>
      <p class="text-gray-600 dark:text-gray-400 text-sm">{{ description }}</p>
    </div>
  </UCard>
</template>

<script setup lang="ts">
defineProps<{
  icon: string
  title: string
  description: string
}>()
</script>
```

### 6.2 `components/CodePreview.vue`

**目的:** コードブロックの表示（シンタックスハイライト付き）

```vue
<template>
  <div class="relative">
    <div class="absolute top-3 right-3 z-10">
      <UButton
        icon="i-heroicons-clipboard-document"
        size="sm"
        color="white"
        variant="solid"
        @click="copyCode"
      >
        {{ copied ? 'コピーしました！' : 'コピー' }}
      </UButton>
    </div>
    <pre
      class="bg-gray-900 dark:bg-gray-950 text-gray-100 p-6 rounded-lg overflow-x-auto"
    ><code>{{ formattedCode }}</code></pre>
  </div>
</template>

<script setup lang="ts">
const props = defineProps<{
  code: string | object
}>()

const copied = ref(false)

const formattedCode = computed(() => {
  if (typeof props.code === 'string') {
    return props.code
  }
  return JSON.stringify(props.code, null, 2)
})

const copyCode = async () => {
  try {
    await navigator.clipboard.writeText(formattedCode.value)
    copied.value = true
    setTimeout(() => {
      copied.value = false
    }, 2000)
  } catch (err) {
    console.error('Failed to copy:', err)
  }
}
</script>
```

### 6.3 `components/InfoBox.vue`

**目的:** 情報ボックス（ヒントや注意事項）

```vue
<template>
  <UAlert
    :icon="icon"
    :color="color"
    :variant="variant"
    :title="title"
    :description="description"
  >
    <template v-if="$slots.default" #description>
      <slot />
    </template>
  </UAlert>
</template>

<script setup lang="ts">
withDefaults(
  defineProps<{
    icon?: string
    color?: 'primary' | 'success' | 'warning' | 'error'
    variant?: 'solid' | 'outline' | 'soft'
    title?: string
    description?: string
  }>(),
  {
    icon: 'i-heroicons-information-circle',
    color: 'primary',
    variant: 'soft',
  }
)
</script>
```

### 6.4 `components/SchemaExample.vue`

**目的:** スキーマ例のタブ表示

```vue
<template>
  <div class="space-y-6">
    <UTabs v-model="selectedTab" :items="tabs">
      <template #item="{ item }">
        <div class="space-y-6">
          <div class="grid md:grid-cols-2 gap-6">
            <!-- プレビュー -->
            <UCard>
              <template #header>
                <h3 class="text-lg font-semibold">検索結果での見え方</h3>
              </template>
              <div v-if="item.key === 'product'" class="space-y-3">
                <h4 class="text-xl text-primary-600 font-semibold">
                  ワイヤレスヘッドホン WH-1000XM5
                </h4>
                <div class="text-2xl text-yellow-500">★★★★★</div>
                <p class="text-gray-600">評価: 4.8 (127件のレビュー)</p>
                <p class="text-3xl font-bold text-primary-600">¥45,000</p>
                <UBadge color="green" variant="subtle">在庫あり</UBadge>
              </div>
              <!-- 他のタイプのプレビューも同様に実装 -->
            </UCard>

            <!-- コード -->
            <div>
              <h3 class="text-lg font-semibold mb-4">JSON-LD コード</h3>
              <CodePreview :code="item.schema" />
            </div>
          </div>

          <!-- 説明 -->
          <InfoBox :title="item.description" />
        </div>
      </template>
    </UTabs>
  </div>
</template>

<script setup lang="ts">
const { productSchema, articleSchema, restaurantSchema, eventSchema, personSchema } =
  useSampleSchemas()

const selectedTab = ref(0)

const tabs = [
  {
    key: 'product',
    label: '商品',
    icon: 'i-heroicons-shopping-bag',
    schema: productSchema,
    description: 'ECサイトの商品ページで使用',
  },
  {
    key: 'article',
    label: '記事',
    icon: 'i-heroicons-document-text',
    schema: articleSchema,
    description: 'ブログ記事やニュース記事で使用',
  },
  {
    key: 'restaurant',
    label: 'レストラン',
    icon: 'i-heroicons-building-storefront',
    schema: restaurantSchema,
    description: '飲食店の情報ページで使用',
  },
  {
    key: 'event',
    label: 'イベント',
    icon: 'i-heroicons-ticket',
    schema: eventSchema,
    description: 'イベント告知ページで使用',
  },
  {
    key: 'person',
    label: '人物',
    icon: 'i-heroicons-user',
    schema: personSchema,
    description: '著者プロフィールなどで使用',
  },
]
</script>
```

---

## 7. ページの実装

### 7.1 `pages/index.vue`

**目的:** メインページ

```vue
<template>
  <div class="min-h-screen bg-gradient-to-br from-primary-500 to-purple-600">
    <UContainer class="py-12">
      <!-- ヘッダー -->
      <UCard class="mb-8">
        <template #header>
          <div class="text-center">
            <h1 class="text-4xl md:text-5xl font-bold text-primary-600 mb-3">
              🔍 application/ld+json 完全解説
            </h1>
            <p class="text-xl text-gray-600 dark:text-gray-400">
              構造化データで検索エンジンと会話する技術
            </p>
          </div>
        </template>
      </UCard>

      <!-- 概要セクション -->
      <UCard class="mb-8">
        <template #header>
          <h2 class="text-2xl font-bold text-primary-600">
            📚 application/ld+json とは？
          </h2>
        </template>

        <InfoBox
          title="JSON-LD (JSON for Linking Data)"
          description="Webページの内容を機械可読な形式で記述する標準フォーマットです。"
          class="mb-6"
        />

        <h3 class="text-xl font-semibold mb-4">🎯 なぜ必要？</h3>
        <p class="text-gray-700 dark:text-gray-300 mb-6">
          HTMLは人間が読むため、検索エンジンは「これは商品名なのか？価格なのか？」を完全には理解できません。JSON-LDを使うと、明示的に情報を伝えられます。
        </p>

        <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-4">
          <FeatureCard
            icon="i-heroicons-star"
            title="リッチスニペット"
            description="検索結果に星評価や価格を表示"
          />
          <FeatureCard
            icon="i-heroicons-chart-bar"
            title="ナレッジグラフ"
            description="検索結果右側の情報カード"
          />
          <FeatureCard
            icon="i-heroicons-microphone"
            title="音声検索"
            description="AlexaやGoogleアシスタント対応"
          />
          <FeatureCard
            icon="i-heroicons-link"
            title="リンクドデータ"
            description="Web上のデータを繋げる"
          />
        </div>
      </UCard>

      <!-- 基本構造セクション -->
      <UCard class="mb-8">
        <template #header>
          <h2 class="text-2xl font-bold text-primary-600">🏗️ 基本構造</h2>
        </template>

        <p class="mb-4">HTMLの&lt;script&gt;タグ内に記述します：</p>

        <CodePreview
          :code="{
            '@context': 'https://schema.org',
            '@type': 'Product',
            name: '商品名',
          }"
          class="mb-6"
        />

        <InfoBox title="重要なキー" color="primary" class="mb-4">
          <ul class="space-y-2">
            <li>
              <strong>@context</strong> - 語彙の定義元（ほぼ常に
              "https://schema.org"）
            </li>
            <li>
              <strong>@type</strong> - データの種類（Product, Article,
              Personなど）
            </li>
            <li>その他のフィールドは@typeによって変わる</li>
          </ul>
        </InfoBox>
      </UCard>

      <!-- 実践例セクション -->
      <UCard class="mb-8">
        <template #header>
          <h2 class="text-2xl font-bold text-primary-600">💻 実践例</h2>
        </template>

        <SchemaExample />
      </UCard>

      <!-- 実装方法セクション -->
      <UCard class="mb-8">
        <template #header>
          <h2 class="text-2xl font-bold text-primary-600">🛠️ 実装方法</h2>
        </template>

        <div class="space-y-6">
          <div>
            <h3 class="text-xl font-semibold mb-3">1. HTMLに直接記述</h3>
            <CodePreview
              code='<!DOCTYPE html>
<html>
<head>
  <script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "WebPage",
    "name": "ページタイトル"
  }
  </script>
</head>'
            />
          </div>

          <div>
            <h3 class="text-xl font-semibold mb-3">2. Nuxt 3 で useHead を使う</h3>
            <CodePreview
              code="useHead({
  script: [
    {
      type: 'application/ld+json',
      innerHTML: JSON.stringify({
        '@context': 'https://schema.org',
        '@type': 'Product',
        'name': '商品名'
      })
    }
  ]
})"
            />
          </div>
        </div>
      </UCard>

      <!-- テストツールセクション -->
      <UCard class="mb-8">
        <template #header>
          <h2 class="text-2xl font-bold text-primary-600">🧪 テストツール</h2>
        </template>

        <div class="grid md:grid-cols-2 gap-4 mb-6">
          <UCard>
            <h4 class="font-semibold text-lg mb-2">
              Google リッチリザルトテスト
            </h4>
            <p class="text-gray-600 dark:text-gray-400 mb-4">
              Googleでの表示を確認
            </p>
            <UButton
              to="https://search.google.com/test/rich-results"
              target="_blank"
              external
            >
              テストする →
            </UButton>
          </UCard>

          <UCard>
            <h4 class="font-semibold text-lg mb-2">Schema Markup Validator</h4>
            <p class="text-gray-600 dark:text-gray-400 mb-4">
              Schema.orgの公式検証ツール
            </p>
            <UButton
              to="https://validator.schema.org/"
              target="_blank"
              external
            >
              検証する →
            </UButton>
          </UCard>
        </div>

        <InfoBox title="テスト方法" color="primary">
          <ol class="space-y-2">
            <li>1. ページのURLまたはコードを入力</li>
            <li>2. 「テスト」ボタンをクリック</li>
            <li>3. エラーや警告を確認</li>
            <li>4. プレビューで表示を確認</li>
          </ol>
        </InfoBox>
      </UCard>

      <!-- ベストプラクティス -->
      <UCard class="mb-8">
        <template #header>
          <h2 class="text-2xl font-bold text-primary-600">
            ✨ ベストプラクティス
          </h2>
        </template>

        <div class="grid md:grid-cols-2 gap-6">
          <div>
            <h3 class="text-lg font-semibold text-green-600 mb-3">
              ✅ DO（推奨）
            </h3>
            <ul class="space-y-2 text-gray-700 dark:text-gray-300">
              <li>✓ 必須フィールドは必ず含める</li>
              <li>✓ 正確な情報を記述する</li>
              <li>✓ 画像は高解像度（最低 1200px推奨）</li>
              <li>✓ 日付はISO 8601形式（2024-10-30）</li>
              <li>✓ 定期的にテストツールで検証</li>
            </ul>
          </div>

          <div>
            <h3 class="text-lg font-semibold text-red-600 mb-3">
              ❌ DON'T（非推奨）
            </h3>
            <ul class="space-y-2 text-gray-700 dark:text-gray-300">
              <li>✗ ページ内容と異なる情報を記述</li>
              <li>✗ 過度に多くのタイプを設定</li>
              <li>✗ レビューの捏造</li>
              <li>✗ スパム的なキーワードの羅列</li>
              <li>✗ 未公開コンテンツの情報を含める</li>
            </ul>
          </div>
        </div>
      </UCard>

      <!-- メリット -->
      <UCard class="mb-8">
        <template #header>
          <h2 class="text-2xl font-bold text-primary-600">🎁 導入するメリット</h2>
        </template>

        <InfoBox color="success" variant="soft">
          <ul class="space-y-3">
            <li>
              <strong>CTR向上</strong> - 星評価表示で平均30%クリック率アップ
            </li>
            <li><strong>SEO改善</strong> - Googleが内容を正確に理解</li>
            <li>
              <strong>音声検索対応</strong> -
              スマートスピーカーで読み上げられる
            </li>
            <li>
              <strong>ブランド認知</strong> - ナレッジグラフに表示される可能性
            </li>
            <li>
              <strong>信頼性向上</strong> - 正確な情報提供で信頼獲得
            </li>
          </ul>
        </InfoBox>
      </UCard>

      <!-- フッター -->
      <div class="text-center text-white">
        <p class="mb-2">
          📖 もっと詳しく知りたい方は
          <UButton
            to="https://schema.org"
            target="_blank"
            external
            variant="link"
            color="white"
          >
            Schema.org
          </UButton>
          をチェック！
        </p>
        <p class="opacity-80 text-sm">
          Created with ❤️ for learning structured data
        </p>
      </div>
    </UContainer>
  </div>
</template>

<script setup lang="ts">
const { setLdJson } = useLdJson()

// ページのメタ情報を設定
useHead({
  title: 'application/ld+json 完全解説',
  meta: [
    {
      name: 'description',
      content: '構造化データで検索エンジンと会話する技術を学ぶ',
    },
  ],
})

// このページ自体にもJSON-LDを設定（例として）
setLdJson({
  '@context': 'https://schema.org',
  '@type': 'WebPage',
  name: 'application/ld+json 完全解説',
  description: '構造化データで検索エンジンと会話する技術',
})
</script>
```

---

## 8. スタイリングとテーマ設定

### 8.1 `nuxt.config.ts` の設定

```typescript
// nuxt.config.ts
export default defineNuxtConfig({
  devtools: { enabled: true },

  modules: ['@nuxt/ui'],

  ui: {
    // Nuxt UI のカスタマイズ
    global: true,
  },

  colorMode: {
    preference: 'light', // 'light', 'dark', 'system'
  },

  app: {
    head: {
      charset: 'utf-8',
      viewport: 'width=device-width, initial-scale=1',
      title: 'application/ld+json 完全解説',
      meta: [
        {
          name: 'description',
          content: '構造化データで検索エンジンと会話する技術',
        },
      ],
    },
  },
})
```

### 8.2 `app.vue` の設定

```vue
<template>
  <div>
    <NuxtPage />
  </div>
</template>

<script setup lang="ts">
// グローバル設定があればここに
</script>
```

### 8.3 カスタムスタイル（オプション）

```css
/* assets/css/custom.css */

/* カスタムグラデーション */
.gradient-bg {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

/* コードブロックのカスタムスタイル */
pre code {
  font-family: 'Monaco', 'Courier New', monospace;
  font-size: 14px;
  line-height: 1.6;
}
```

---

## 9. テストと検証

### 9.1 開発サーバーの起動

```bash
npm run dev
```

ブラウザで `http://localhost:3000` を開いて確認

### 9.2 チェックリスト

- [ ] すべてのタブが正常に切り替わる
- [ ] コードのコピー機能が動作する
- [ ] レスポンシブデザインが適用されている
- [ ] ダークモードの切り替えが動作する（オプション）
- [ ] 外部リンクが正しく開く
- [ ] JSON-LD が `<head>` に正しく挿入されている

### 9.3 JSON-LD の検証

1. Google リッチリザルトテストで検証
2. ブラウザの開発者ツールで `<head>` 内の `<script type="application/ld+json">` を確認
3. Console でエラーがないか確認

---

## 10. デプロイ準備

### 10.1 ビルド

```bash
# 本番用ビルド
npm run build

# プレビュー
npm run preview
```

### 10.2 静的サイト生成（SSG）

```bash
# nuxt.config.ts に追加
export default defineNuxtConfig({
  ssr: true,
  // または静的生成の場合
  nitro: {
    preset: 'static'
  }
})

# 生成
npm run generate
```

### 10.3 デプロイ先の例

**Vercel:**
```bash
npm install -g vercel
vercel
```

**Netlify:**
```bash
npm install -g netlify-cli
netlify deploy
```

**Cloudflare Pages:**
- ビルドコマンド: `npm run generate`
- 出力ディレクトリ: `.output/public`

---

## 🎉 完成！

以上で Nuxt 3 + Nuxt UI での実装が完了です。

## 次のステップ（オプション）

1. **アニメーション追加** - `@vueuse/motion` を使用
2. **多言語対応** - `@nuxtjs/i18n` を追加
3. **ブログ機能** - `@nuxt/content` で記事管理
4. **検索機能** - スキーマタイプの検索
5. **カスタムテーマ** - Tailwind の拡張

---

## トラブルシューティング

### Q: Nuxt UI のコンポーネントが表示されない
A: `nuxt.config.ts` に `@nuxt/ui` が正しく追加されているか確認

### Q: アイコンが表示されない
A: `@iconify-json/heroicons` がインストールされているか確認

### Q: ビルドエラーが出る
A:
```bash
rm -rf node_modules .nuxt
npm install
npm run dev
```

---

## 参考リンク

- [Nuxt 3 ドキュメント](https://nuxt.com/)
- [Nuxt UI ドキュメント](https://ui.nuxt.com/)
- [Schema.org](https://schema.org/)
- [Google 構造化データガイド](https://developers.google.com/search/docs/advanced/structured-data)
