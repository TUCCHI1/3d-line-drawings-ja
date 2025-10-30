# Nuxt × Nuxt UI で学ぶ JSON-LD デモ

Nuxt 3とNuxt UIを使った、**application/ld+json（構造化データ）** の実践的なデモアプリケーションです。

## 🎯 このプロジェクトについて

このプロジェクトは、Webページに構造化データを実装する方法を、インタラクティブに学べるデモサイトです。
商品、記事、レストラン、イベントなど、実際のビジネスで使える4つのユースケースを網羅しています。

## ✨ 特徴

### 📚 4つの実践例

1. **🛍️ 商品 (Product)**
   - 商品名、価格、評価、在庫状況
   - 検索結果に星評価と価格を表示

2. **📝 記事 (Article)**
   - ブログ記事、ニュース記事
   - 著者、公開日、出版者情報
   - Googleニュース対応

3. **🍽️ レストラン (Restaurant)**
   - 店舗情報、営業時間、評価
   - Googleマップ連携
   - ローカル検索最適化

4. **🎫 イベント (Event)**
   - 開催日時、場所、チケット情報
   - Googleカレンダー連携
   - オンライン/オフライン対応

### 🎮 インタラクティブな機能

- **リアルタイムプレビュー**: 入力した情報がすぐに反映
- **検索結果シミュレーション**: Googleでの表示イメージを確認
- **JSON-LD生成**: 実装に使えるコードを自動生成
- **コピー機能**: ワンクリックでコードをコピー

### 🎨 美しいUI

- **Nuxt UI**: モダンで美しいコンポーネント
- **ダークモード対応**: ライト/ダークモード切り替え
- **レスポンシブデザイン**: スマホからデスクトップまで対応
- **直感的なナビゲーション**: タブで簡単にページ切り替え

## 🚀 セットアップ

### 依存関係のインストール

```bash
npm install
```

### 開発サーバーの起動

```bash
npm run dev
```

ブラウザで `http://localhost:3000` を開きます。

### 本番ビルド

```bash
npm run build
npm run preview
```

## 📁 プロジェクト構造

```
nuxt-ld-json-demo/
├── layouts/
│   └── default.vue          # 共通レイアウト（ナビゲーション）
├── pages/
│   ├── index.vue            # トップページ（概要説明）
│   ├── product.vue          # 商品ページ
│   ├── article.vue          # 記事ページ
│   ├── restaurant.vue       # レストランページ
│   └── event.vue            # イベントページ
├── components/              # 再利用可能なコンポーネント
└── nuxt.config.ts           # Nuxt設定ファイル
```

## 💡 使い方

### 1. トップページで概要を理解

JSON-LDとは何か、どんなメリットがあるのかを学びます。

### 2. 各ページで実践

- フォームに情報を入力
- 検索結果での表示イメージを確認
- 生成されたJSON-LDコードをコピー
- 自分のプロジェクトに貼り付け

### 3. 実装例を参考にする

各ページのコードを見て、`useHead()`での実装方法を学びます。

## 🔧 技術スタック

- **[Nuxt 3](https://nuxt.com/)** - フルスタックVueフレームワーク
- **[Nuxt UI](https://ui.nuxt.com/)** - 美しいUIコンポーネントライブラリ
- **[Tailwind CSS](https://tailwindcss.com/)** - ユーティリティファーストCSS
- **[TypeScript](https://www.typescriptlang.org/)** - 型安全な開発
- **[Schema.org](https://schema.org)** - 構造化データの標準仕様

## 📖 学べる内容

### JSON-LDの基礎

- `@context`と`@type`の役割
- 必須フィールドと推奨フィールド
- 正しいデータ形式

### Nuxt 3での実装

- `useHead()`の使い方
- リアクティブな構造化データ
- SSR対応の実装

### ベストプラクティス

- Google推奨の実装方法
- よくある間違いの回避
- テストツールの使い方

## 🧪 テストツール

実装したJSON-LDは以下のツールでテストできます：

- [Google リッチリザルトテスト](https://search.google.com/test/rich-results)
- [Schema Markup Validator](https://validator.schema.org/)

## 🎁 導入するメリット

1. **CTR向上** - 星評価表示で平均30%クリック率アップ
2. **SEO改善** - Googleが内容を正確に理解
3. **音声検索対応** - AlexaやGoogleアシスタント対応
4. **ナレッジグラフ** - 検索結果右側の情報カードに表示
5. **信頼性向上** - 正確な情報提供で信頼獲得

## 📚 参考リンク

- [Schema.org 公式サイト](https://schema.org)
- [Google 構造化データガイド](https://developers.google.com/search/docs/advanced/structured-data/intro-structured-data)
- [JSON-LD 公式サイト](https://json-ld.org/)
- [Nuxt 3 ドキュメント](https://nuxt.com/docs)
- [Nuxt UI ドキュメント](https://ui.nuxt.com/)

## 📝 ライセンス

MIT License - 自由に使用・改変してください

## 🙋 質問・フィードバック

改善提案やバグ報告は大歓迎です！

---

Made with ❤️ using Nuxt 3 and Nuxt UI
