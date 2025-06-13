# Astro スターターキット: ベーシック

```sh
npm create astro@latest -- --template basics
```

[![Open in StackBlitz](https://developer.stackblitz.com/img/open_in_stackblitz.svg)](https://stackblitz.com/github/withastro/astro/tree/latest/examples/basics)
[![Open with CodeSandbox](https://assets.codesandbox.io/github/button-edit-lime.svg)](https://codesandbox.io/p/sandbox/github/withastro/astro/tree/latest/examples/basics)
[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/withastro/astro?devcontainer_path=.devcontainer/basics/devcontainer.json)

> 🧑‍🚀 **経験豊富な宇宙飛行士ですか？** このファイルを削除してください。楽しんで！

![just-the-basics](https://github.com/withastro/astro/assets/2244813/a0a5533c-a856-4198-8470-2d67b1d7c554)

## 🚀 プロジェクト構造

Astroプロジェクトの内部には、以下のフォルダとファイルが表示されます：

```text
/
├── public/
│   └── favicon.svg
├── src/
│   ├── assets/
│   │   ├── astro.svg
│   │   └── background.svg
│   ├── components/
│   │   └── Welcome.astro
│   ├── layouts/
│   │   └── Layout.astro
│   └── pages/
│       └── index.astro
├── astro.config.mjs
├── package.json
└── tsconfig.json
```

Astroプロジェクトのフォルダ構造について詳しく知りたい場合は、[プロジェクト構造に関するガイド](https://docs.astro.build/ja/basics/project-structure/)を参照してください。

## 🧞 コマンド

すべてのコマンドは、ターミナルからプロジェクトのルートで実行されます：

| コマンド                   | アクション                                       |
| :------------------------ | :----------------------------------------------- |
| `npm install`             | 依存関係をインストール                            |
| `npm run dev`             | `localhost:4321`でローカル開発サーバーを起動      |
| `npm run build`           | 本番サイトを`./dist/`にビルド                     |
| `npm run preview`         | デプロイ前にビルドをローカルでプレビュー          |
| `npm run astro ...`       | `astro add`、`astro check`などのCLIコマンドを実行 |
| `npm run astro -- --help` | Astro CLIの使用方法のヘルプを表示                 |

## 🎨 カスタマイズ方法

### 1. ページの追加

新しいページを追加するには、`src/pages/`ディレクトリに`.astro`ファイルを作成します：

```astro
// src/pages/about.astro
---
import Layout from '../layouts/Layout.astro';
---

<Layout title="About">
  <h1>私たちについて</h1>
  <p>ここに内容を追加...</p>
</Layout>
```

### 2. コンポーネントの作成

再利用可能なコンポーネントを`src/components/`に作成：

```astro
// src/components/Card.astro
---
export interface Props {
  title: string;
  body: string;
}

const { title, body } = Astro.props;
---

<div class="card">
  <h2>{title}</h2>
  <p>{body}</p>
</div>

<style>
  .card {
    padding: 1.5rem;
    background-color: #f3f4f6;
    border-radius: 0.5rem;
  }
</style>
```

### 3. レイアウトのカスタマイズ

`src/layouts/Layout.astro`を編集して、サイト全体のレイアウトを変更：

```astro
---
export interface Props {
  title: string;
}

const { title } = Astro.props;
---

<!doctype html>
<html lang="ja">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>{title}</title>
  </head>
  <body>
    <header>
      <!-- ナビゲーションを追加 -->
    </header>
    <main>
      <slot />
    </main>
    <footer>
      <!-- フッターを追加 -->
    </footer>
  </body>
</html>
```

### 4. スタイリング

Astroは複数のスタイリング方法をサポート：

**コンポーネントスコープのCSS：**
```astro
<style>
  h1 {
    color: purple;
    font-size: 4rem;
  }
</style>
```

**グローバルCSS：**
```astro
<style is:global>
  body {
    margin: 0;
    font-family: system-ui;
  }
</style>
```

**CSSフレームワークの追加（例：Tailwind CSS）：**
```sh
npm run astro add tailwind
```

### 5. 画像とアセット

- **静的アセット**: `public/`フォルダに配置（そのまま提供される）
- **処理されるアセット**: `src/assets/`に配置（最適化される）

```astro
---
import { Image } from 'astro:assets';
import myImage from '../assets/my-image.png';
---

<Image src={myImage} alt="説明" />
```

### 6. インテグレーションの追加

Astroは多くのインテグレーションをサポート：

```sh
# React を追加
npm run astro add react

# Tailwind CSS を追加
npm run astro add tailwind

# MDX サポートを追加
npm run astro add mdx
```

### 7. 環境変数

`.env`ファイルを作成して環境変数を管理：

```env
PUBLIC_API_URL=https://api.example.com
SECRET_API_KEY=your-secret-key
```

Astroコンポーネントでの使用：
```astro
---
const apiUrl = import.meta.env.PUBLIC_API_URL;
// PUBLIC_ プレフィックスがついた変数のみクライアントで利用可能
---
```

### 8. デプロイ

Astroは静的サイトを生成するため、多くのホスティングサービスにデプロイ可能：

- **Netlify**: `npm run build`を実行し、`dist/`フォルダをデプロイ
- **Vercel**: Astroプロジェクトを自動検出
- **GitHub Pages**: GitHub Actionsを使用して自動デプロイ

## 👀 もっと詳しく知りたいですか？

[ドキュメント](https://docs.astro.build/ja/)をチェックするか、[Discordサーバー](https://astro.build/chat)に参加してください。