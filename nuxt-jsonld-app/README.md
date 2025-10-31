# Nuxt 4.2 + Nuxt UI - JSON-LD Demo App

このプロジェクトは、**Nuxt 4.2** と **Nuxt UI** を使用して、JSON-LD構造化データの実装方法を示すデモアプリです。

## 📚 JSON-LD (`@type`) とは？

**JSON-LD** (JSON for Linking Data) は、構造化データをJSON形式で記述するフォーマットです。

### 主要な要素

- **`@context`**: スキーマの名前空間を定義（通常は `"https://schema.org"`）
- **`@type`**: データの種類を指定（Person, Article, Product, Organizationなど）
- **`@id`**: リソースの一意な識別子（オプション）

### なぜJSON-LDが重要なのか？

1. **SEO最適化**: Google、Bing等の検索エンジンがページ内容を理解しやすくなる
2. **リッチリザルト**: 検索結果にレーティング、価格、画像などが表示される
3. **構造化データ**: 機械可読形式でコンテンツを提供

## 🎯 実装例

このアプリでは以下のJSON-LD `@type` の例を実装しています：

| @type | 用途 | ページ |
|-------|------|--------|
| `Person` | 個人プロフィール情報 | `/person` |
| `Article` | ブログ記事・ニュース記事 | `/article` |
| `Product` | 商品情報・ECサイト | `/product` |
| `Organization` | 企業・組織情報 | `/organization` |
| `Recipe` | レシピ情報 | `/recipe` |
| `Event` | イベント情報 | `/event` |

## 🚀 セットアップ

```bash
# 依存関係のインストール
npm install

# 開発サーバーの起動 (http://localhost:3000)
npm run dev

# 本番ビルド
npm run build

# 本番プレビュー
npm run preview
```

## 💡 Nuxt 4.2でJSON-LDを実装する方法

### 方法1: `useHead()` を使用（推奨）

```vue
<script setup lang="ts">
const jsonLd = {
  '@context': 'https://schema.org',
  '@type': 'Person',
  name: '山田太郎',
  jobTitle: 'フロントエンドエンジニア'
}

useHead({
  script: [
    {
      type: 'application/ld+json',
      children: JSON.stringify(jsonLd)
    }
  ]
})
</script>
```

### 方法2: `useSeoMeta()` と組み合わせる

```vue
<script setup lang="ts">
useSeoMeta({
  title: 'My Page',
  description: 'This is my page description'
})

useHead({
  script: [
    {
      type: 'application/ld+json',
      children: JSON.stringify({
        '@context': 'https://schema.org',
        '@type': 'WebPage',
        name: 'My Page'
      })
    }
  ]
})
</script>
```

## 🎨 Nuxt UI コンポーネント使用例

このアプリでは以下のNuxt UIコンポーネントを使用しています：

- `UContainer`: レスポンシブなコンテナ
- `UCard`: カードレイアウト
- `UButton`: ボタンコンポーネント
- `UBadge`: バッジ表示
- `UAlert`: アラート通知
- `USeparator`: 区切り線
- `ULink`: リンクコンポーネント
- `UAvatar`: アバター表示

## 🔍 JSON-LDのテスト方法

1. **Rich Results Test (Google)**
   - https://search.google.com/test/rich-results
   - URLまたはコードを入力してテスト

2. **Schema Markup Validator**
   - https://validator.schema.org/
   - JSON-LDの妥当性を検証

3. **ブラウザの開発者ツール**
   ```javascript
   // コンソールで実行
   document.querySelectorAll('script[type="application/ld+json"]')
   ```

## 💎 Nuxt Tips: `useAsyncData` と `useFetch` の違い

### 重要なNuxt Tip！

Nuxtで非同期データを取得する際、**`useAsyncData`** と **`useFetch`** の2つの方法がありますが、使い分けが重要です。

#### `useFetch` - シンプルなAPI取得

```vue
<script setup lang="ts">
// 内部的にuseAsyncDataを使用
const { data, pending, error } = await useFetch('/api/users')
</script>
```

**特徴:**
- `useAsyncData` + `$fetch` のショートハンド
- URLを直接指定するだけで使える
- 自動的にキーを生成

#### `useAsyncData` - 柔軟なデータ取得

```vue
<script setup lang="ts">
// より柔軟な制御が可能
const { data, pending, error } = await useAsyncData(
  'user-data', // キー（キャッシュ管理に使用）
  () => $fetch('/api/users'),
  {
    // オプション
    server: true,    // サーバーサイドで実行
    lazy: false,     // 遅延ロード
    default: () => [], // デフォルト値
    transform: (data) => data.map(u => u.name) // データ変換
  }
)
</script>
```

**特徴:**
- キーを明示的に指定できる（キャッシュ制御）
- 複雑なデータ変換が可能
- より細かいオプション制御

#### 使い分けのポイント

| 状況 | 使うべきもの | 理由 |
|------|------------|------|
| シンプルなAPI取得 | `useFetch` | コードが短くシンプル |
| 複数の処理を組み合わせ | `useAsyncData` | 柔軟な制御が可能 |
| キャッシュを明示的に管理 | `useAsyncData` | キーを自分で指定できる |
| データ変換が必要 | `useAsyncData` | `transform`オプションが使える |

#### 実践例

```vue
<script setup lang="ts">
// ❌ useFetchで複雑な処理は避ける
const { data } = await useFetch('/api/users')
const processed = data.value?.map(u => ({ ...u, fullName: `${u.first} ${u.last}` }))

// ✅ useAsyncDataで変換処理を含める
const { data } = await useAsyncData(
  'processed-users',
  () => $fetch('/api/users'),
  {
    transform: (users) => users.map(u => ({
      ...u,
      fullName: `${u.first} ${u.last}`
    }))
  }
)
</script>
```

**メモ**: `useFetch`は`useAsyncData(url, () => $fetch(url))`の糖衣構文です。シンプルな場合は`useFetch`、複雑な場合は`useAsyncData`を選びましょう！

## 📖 参考リンク

- [Nuxt 4 Documentation](https://nuxt.com/docs)
- [Nuxt UI Documentation](https://ui.nuxt.com)
- [Schema.org Documentation](https://schema.org/)
- [Google Search Central - Structured Data](https://developers.google.com/search/docs/appearance/structured-data/intro-structured-data)

## 🛠️ 技術スタック

- **Nuxt 4.2**: Vue.jsフレームワーク
- **Nuxt UI 4.1**: UIコンポーネントライブラリ
- **TypeScript**: 型安全な開発
- **JSON-LD**: 構造化データ

## 📝 ライセンス

MIT

---

**Made with Nuxt 4.2 + Nuxt UI**
