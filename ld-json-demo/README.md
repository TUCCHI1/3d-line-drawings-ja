# application/ld+json 完全解説デモ

構造化データ（JSON-LD）の基礎から実践までを学べるインタラクティブな解説ページです。

## 🎯 このプロジェクトについて

`application/ld+json` は、Webページの内容を機械可読な形式で記述するための技術です。
Google などの検索エンジンがページの内容を正確に理解し、リッチスニペット（星評価、価格表示など）を表示するために使用されます。

## 📚 学べる内容

- **JSON-LD の基礎概念**
- **5つの実践例**（商品、記事、レストラン、イベント、人物）
- **各種フレームワークでの実装方法**（Nuxt、Next.js、HTML）
- **ベストプラクティス**
- **テストツールの使い方**

## 🚀 使い方

### 1. ローカルで開く

```bash
# プロジェクトディレクトリに移動
cd /Users/tucch1/dev/ld-json-demo

# ブラウザで開く（MacOS）
open index.html

# または、Windowsの場合
start index.html

# または、Linuxの場合
xdg-open index.html
```

### 2. ローカルサーバーで起動（推奨）

より正確な動作確認のため、ローカルサーバーで起動することを推奨します：

```bash
# Pythonを使う場合
python3 -m http.server 8000

# Node.jsのhttp-serverを使う場合
npx http-server -p 8000

# PHPを使う場合
php -S localhost:8000
```

ブラウザで `http://localhost:8000` を開きます。

## 🔍 主な機能

### インタラクティブなタブ切り替え
- 商品（Product）
- 記事（Article）
- レストラン（Restaurant）
- イベント（Event）
- 人物（Person）

各タブでは、実際の検索結果での見え方とJSON-LDコードを確認できます。

### 実装例
- HTMLに直接記述する方法
- Nuxt 3での実装
- Next.jsでの実装

### テストツールへのリンク
- Google リッチリザルトテスト
- Schema Markup Validator

## 📖 よく使うSchema.orgタイプ

| カテゴリ | タイプ |
|---------|--------|
| 商品・サービス | Product, Offer, Review |
| コンテンツ | Article, BlogPosting, NewsArticle |
| ビジネス | LocalBusiness, Restaurant, Organization |
| イベント | Event, Course, WebinarEvent |
| 人物・チーム | Person, Organization |
| レシピ・料理 | Recipe, HowTo |
| 動画・音楽 | VideoObject, MusicRecording |
| FAQ・Q&A | FAQPage, QAPage |

## ✨ ベストプラクティス

### ✅ DO（推奨）
- 必須フィールドは必ず含める
- 正確な情報を記述する
- 画像は高解像度（最低 1200px推奨）
- 日付はISO 8601形式（2024-10-30）
- 定期的にテストツールで検証

### ❌ DON'T（非推奨）
- ページ内容と異なる情報を記述
- レビューの捏造
- スパム的なキーワードの羅列

## 🎁 導入するメリット

1. **CTR向上** - 星評価表示で平均30%クリック率アップ
2. **SEO改善** - Googleが内容を正確に理解
3. **音声検索対応** - スマートスピーカーで読み上げられる
4. **ブランド認知** - ナレッジグラフに表示される可能性
5. **信頼性向上** - 正確な情報提供で信頼獲得

## 🔗 参考リンク

- [Schema.org 公式サイト](https://schema.org)
- [Google 構造化データガイド](https://developers.google.com/search/docs/advanced/structured-data/intro-structured-data)
- [JSON-LD 公式サイト](https://json-ld.org/)
- [Google リッチリザルトテスト](https://search.google.com/test/rich-results)

## 📝 ライセンス

MIT License - 自由に使用・改変してください

## 🙋 フィードバック

改善提案やバグ報告は大歓迎です！
