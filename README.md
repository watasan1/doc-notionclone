# doc-notionclone

## タイトル

【初心者向け React ハンズオン】ミニ Notion クローンで学ぶ、状態管理マスター勉強会

## 開催日

2025年11月

## 参考URL

https://beginner-react.connpass.com/event/376960/

## こんな方におすすめ

React/Next.js の基本的な扱いに慣れてきた方
React の状態管理について学びたい方
React エンジニアとしての転職/就職を目指している方
React/ Next.js を使った簡単なプロジェクトにチャレンジしてみたい方



## 課題

イシュー管理アプリ

レベル：初級〜中級

## 概要

Notion 風のイシュー管理アプリを構築します。

アイデアをブロックとして管理したり、ToDo をデータベースビューでの表示・編集、複数ページでの管理機能を実装します。

（様々なライブラリを使用・比較し、React の状態管理をマスターしましょう

## 学習する内容

今回のテーマは、React における状態管理について、学習します。

useState、immer、useContext、Zustand など、
React の状態管理において、各ライブラリの特徴と利点を比較し、理解を深めてください。

useState による基本的な状態管理
immer によるイミュータブルな記述の簡略化
Context API による グローバルな状態管理
Zustand によるグローバルでハイパフォーマンスな状態管理
Vite を用いた React 環境構築
TypeScript による型チェック
Tailwind CSS を用いたスタイリング
shadcn/ui によるコンポーネントの導入
GitHub Pages へのデプロイ
この勉強会を通して、React/Next.js を使った成果物を１つ構築することを目指します！

## システム要件

Node.js 環境（v20.9.0 以上）が構築されたPCが必要です
Git/ GitHub環境（アカウント）の用意
HTML/CSS/JavaScriptの基礎知識が必要です
Reactの基礎（Progateレベルの内容）は理解している前提の内容となっております


## 要件定義

アイデアブロック管理：
アイデアをブロックとして追加・削除・並び替えできる。
ToDo データベースビュー：
ToDo をテーブル形式で表示・管理する。
詳細表示：
ToDo クリックで右サイドバーに詳細ページを表示する。
ページ管理：
複数ページの作成・切り替え・削除を行う。


アイデアブロック機能
 ユーザーがページにアクセスすると、アイデアを入力できるフォームが表示されている。
 追加したアイデアが、ブロック形式で縦に一覧表示される。
 アイデアブロックをドラッグ&ドロップで並び替えできる。
 アイデアブロックを削除できる。
ToDo データベース機能
 ToDo をテーブル形式（データベースビュー）で表示できる。
 ToDo のタイトル、ステータス（未完了/完了）、作成日が表示される。
 新しい ToDo を追加できる。
 ToDo のステータスを切り替えできる。
 ToDo を削除できる。
詳細表示機能
 ToDo をクリックすると、右サイドバーが開き詳細が表示される。
 サイドバーで ToDo のタイトル、説明、ステータスを編集できる。
 サイドバーを閉じることができる。
ページ管理機能
 新しいページを作成できる。
 ページタブでページを切り替えできる。
 ページのタイトルを編集できる。
 ページを削除できる（最低 1 ページは残る）。
 各ページで独立したアイデアブロックと ToDo を管理できる。
その他
 アプリケーションがデプロイされており、誰でもアクセス可能である。

## タスク

着手すべきタスク（Issues）は、以下のとおりです：


## Chapter 01 Vite による React プロジェクトの作成
## Chapter 02 プロジェクトにTailwind CSS の導入
## Chapter 03 shadcn/ui の導入
## Chapter 04 ページ切り替えサイドバーの作成
## Chapter 05 アイデアブロックの実装
## Chapter 06 ToDo データベース機能の実装
## Chapter 07 GitHub Pages へのデプロイ

## 1 Vite による React プロジェクトの作成

### 1. Viteとは？

vite は、高速な開発環境とビルドツールを提供する JavaScript のビルドツールです。

従来の webpack ベースの構築ツールと比較して、開発サーバーの起動が非常に高速で、ホットモジュールリプレイスメント（HMR）も効率的に行えます。

React 開発体験を大幅に向上させることができます。

### 2. Viteの導入手順

1. はじめに、Node.js と npm がインストールされていることを確認してください！

```sh
% node -v
```

v22.18.0


2. プロジェクトディレクトリの作成

```sh
mkdir react-notionclone-app && cd react-notionclone-app
```

3. Viteを使用してReactプロジェクトを作成します。

```sh
npm create vite@latest
```

プロンプトに従い回答します

Need to install the following packages:
create-vite@8.2.0
Ok to proceed? (y) 

```
◆  Project name:
│  .█
└
```

```
◆  Select a framework:
│  ● React
```

```
◆  Select a variant:
│  ● TypeScript + SWC
```

```
◆  Select a variant:
│  ● TypeScript + SWC
```

```
◆  Use rolldown-vite (Experimental)?:
│  ● No
└
```

```
◆  Install with npm and start now?
│  ● Yes / ○ No
└
```

4. 依存関係をインストールします

```sh
npm install
```

5. 開発サーバーの起動

```sh
% npm run dev
```

### 3. git でプロジェクトを管理する

```sh
% git init
```

Initialized empty Git repository in /Users/hirotaka/work/react-notionclone-app/.git/

```sh
% git add .
```

```sh
git commit -m "Reactの導入"
```

### 4. 本章のまとめ

SWC とは？

SWC（Speedy Web Compiler）は、JavaScript と TypeScript の、コンパイルとバンドルの両方を行うことが出来ます。

## 2 プロジェクトにTailwind CSS の導入

Tailwind CSS は、ユーティリティファーストの CSS フレームワークです。

### 1. tailwindcssと、その依存関係をインストール

```sh
npm install tailwindcss @tailwindcss/vite
```

### 2. vite.config.ts ファイルにプラグインを追加します。

```ts
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react-swc'
import tailwindcss from "@tailwindcss/vite";

// https://vite.dev/config/
export default defineConfig({
  plugins: [react(), tailwindcss()],
})

```

### 3. ./src/index.cssファイルに、Tailwind CSS をインポートする

./src/index.css　既存のソースコードは削除します。

```css
@import "tailwindcss";
```

を記載します。

### 4. Tailwind CSSを試してみる

src/App.tsx ファイルをH1タグに対し、スタイルを当ててみます。

```tsx
<h1 className='text-5xl text-blue-500'>Vite + React</h1>
```
### 5. 開発サーバーを起動する

```sh
npm run dev
```

### 6. git でプロジェクトを管理する

```sh
git add .
git commit -m "Tailwind CSSのセットアップ"
```

## 3 shadcn/ui の導入
## 4 ページ切り替えサイドバーの作成
## 5 アイデアブロックの実装
## 6 ToDo データベース機能の実装
## 7 GitHub Pages へのデプロイ

 




