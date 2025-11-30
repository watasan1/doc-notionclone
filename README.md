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

## Chapter 01 Vite による React プロジェクトの作成

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

## Chapter 02 プロジェクトにTailwind CSS の導入

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

## Chapter 03 shadcn/ui の導入

### 1. shadcn/ui とは？

shadcn/ui とは、アプリにコピーして貼り付けることができる美しく設計されたコンポーネント。アクセス可能。カスタマイズ可能。オープンソース。

shadcn/ui の特徴は：

コンポーネントライブラリではなく、アプリにコピーして貼り付けて使う「コンポーネントのコレクション」
「コンポーネントの設計は、構造や振る舞いと、スタイルは分離されるべき」というコンセプト基づいている
Tailwind CSS と Radix UI をベースに構築されている
（ただし、UI コンポーネントにしては、学習コストがやや高い）

### 1. shadcn/ui の導入手順

1. shadcn/ui のパスを設定する

```tsconfig.json
{
  "files": [],
  "references": [
    { "path": "./tsconfig.app.json" },
    { "path": "./tsconfig.node.json" }
  ],
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": ["./src/*"]
    }
  }
}

```

この設定によって、相対パス（例: ../../component）ではなく、
エイリアス（例: @/component）を使用した簡潔なインポートが可能になります！

2. tsconfig.app.jsonファイルに、次のコードを追加します

```
{
  "compilerOptions": {
    /* Linting */
    "strict": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "erasableSyntaxOnly": true,
    "noFallthroughCasesInSwitch": true,
    "noUncheckedSideEffectImports": true,
    "baseUrl": ".",
    "paths": {
      "@/*": ["./src/*"]
    }
  },
  "include": ["src"]
}

```

3. 次のコードを vite.config.ts に設定を追加します

```ts
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react-swc";
import tailwindcss from "@tailwindcss/vite";
import path from "path";

// https://vite.dev/config/
export default defineConfig({
  plugins: [react(), tailwindcss()],
  resolve: {
    alias: {
      "@": path.resolve(__dirname, "./src"),
    },
  },
});

```

もし、pathに関するエラーが発生したら、下記を実行します

```sh
npm i -D @types/node
```

4. shadcn/ui の初期化コマンドを実行

それでは、shadcn/ui の初期化コマンドを実行して、プロジェクトをセットアップします

```sh
npx shadcn@latest init
```

Need to install the following packages:
shadcn@3.5.1
Ok to proceed? (y) 

```
? Which color would you like to use as the base color? › - Use arrow-keys. Return to submit.
❯   Neutral
```

5. shadcn/ui のコンポーネントを追加

```sh
npx shadcn@latest add button checkbox dialog dropdown-menu input textarea separator switch table
```

6. 確認

src/App.tsxを、以下のように書き換えます。

```tsx
import { Button } from "@/components/ui/button";
import { Checkbox } from "@/components/ui/checkbox";
import { Input } from "@/components/ui/input";
import { Textarea } from "@/components/ui/textarea";
import { Separator } from "@/components/ui/separator";
import { Switch } from "@/components/ui/switch";
import {
  Dialog,
  DialogContent,
  DialogDescription,
  DialogHeader,
  DialogTitle,
  DialogTrigger,
} from "@/components/ui/dialog";
import {
  DropdownMenu,
  DropdownMenuContent,
  DropdownMenuItem,
  DropdownMenuTrigger,
} from "@/components/ui/dropdown-menu";
import {
  Table,
  TableBody,
  TableCell,
  TableHead,
  TableHeader,
  TableRow,
} from "@/components/ui/table";

function App() {
  return (
    <div className="p-8 space-y-4">
      <h1 className="text-2xl font-bold">shadcn/ui コンポーネント確認</h1>

      <Button>ボタン</Button>

      <div className="flex items-center space-x-2">
        <Checkbox id="terms" />
        <label htmlFor="terms">チェックボックス</label>
      </div>

      <Input placeholder="入力フィールド" />

      <Textarea placeholder="テキストエリア" />

      <div className="flex items-center space-x-2">
        <Switch id="airplane-mode" />
        <label htmlFor="airplane-mode">スイッチ</label>
      </div>

      <Separator />

      <Dialog>
        <DialogTrigger asChild>
          <Button variant="outline">ダイアログを開く</Button>
        </DialogTrigger>
        <DialogContent>
          <DialogHeader>
            <DialogTitle>ダイアログ</DialogTitle>
            <DialogDescription>これはダイアログの例です。</DialogDescription>
          </DialogHeader>
        </DialogContent>
      </Dialog>

      <DropdownMenu>
        <DropdownMenuTrigger asChild>
          <Button variant="outline">ドロップダウン</Button>
        </DropdownMenuTrigger>
        <DropdownMenuContent>
          <DropdownMenuItem>項目1</DropdownMenuItem>
          <DropdownMenuItem>項目2</DropdownMenuItem>
        </DropdownMenuContent>
      </DropdownMenu>

      <Table>
        <TableHeader>
          <TableRow>
            <TableHead>列1</TableHead>
            <TableHead>列2</TableHead>
          </TableRow>
        </TableHeader>
        <TableBody>
          <TableRow>
            <TableCell>データ1</TableCell>
            <TableCell>データ2</TableCell>
          </TableRow>
        </TableBody>
      </Table>
    </div>
  );
}

export default App;
```

開発サーバーを起動して確認してみましょう。

shadcn/ui のセットアップは完了です.

7. git でプロジェクトを管理する

```sh
git add .
git commit -m "shadcn/ui のセットアップ"
```

8. 本章のまとめ

shadcn/ui は、コピー&ペーストして使用するコンポーネントのコレクション
Tailwind CSS と Radix UI をベースに、高度にカスタマイズ可能な UI コンポーネントを提供している
npx shadcn@latest initコマンドで、プロジェクト全体の設定を簡単に行える
デザインスタイル、ベースカラー、CSS 変数の使用などを初期設定時に選択可能
これにより、強力なデザインシステムと柔軟な拡張性を搭載した状態から、開発をスタートできます！

## Chapter 04 ページ切り替えサイドバーの作成

### 1. React の状態管理の基本

React における状態管理は、アプリケーションの動的なデータを効率的に管理するための仕組みです。

React の状態管理の基本概念：

仮想 DOM（Virtual DOM）：実際の DOM の軽量なコピーを作成し、差分のみを更新することで高速化
不変性（Immutability）：状態を直接変更せず、更新用関数を使用して新しい状態を作成する間接的な更新
単方向データフロー：親 → 子コンポーネントへ、データが一方向に流れることで、バグを減らし、デバッグを容易にする

### 2. データ型の定義

ページとアプリケーション全体で使用するデータ構造を定義します。

src/types/index.ts　ファイルを作成します。

```sh
% mkdir -p src/types && touch src/types/index.ts
```

```ts
/**
 * アプリケーション共通型定義
 *
 * このモジュールはアプリケーション全体で使用される
 * データ構造とUI状態の型定義を提供します。
 */

// ページ（カテゴリ）情報を表す型
// サイドバーでのページ表示とコンテンツフィルタリングに使用
export interface Page {
  id: string;
  title: string;
  isActive: boolean; // 現在選択中のページかどうか
  category: string; // フィルタリング用のカテゴリ識別子
  emoji: string;
}

// アイデア情報を表す型
// 簡易的なメモ機能として使用
export interface Idea {
  id: string;
  text: string;
  createdAt: Date;
  category: string; // 所属ページのカテゴリ
}

// TODO情報を表す型
// タスク管理機能のメインデータ構造
export interface Todo {
  id: string;
  title: string;
  description: string;
  completed: boolean;
  createdAt: Date;
  updatedAt: Date;
  category: string; // 所属ページのカテゴリ
}

// UI状態の型定義
export interface UIState {
  sidebarOpen: boolean;
  selectedTodo: Todo | null;
  editingTodo: Todo | null;
  draggedIdea: string | null;
}
```

### 3. 初期データの記載

アプリケーション起動時に表示するサンプルデータを定義します。

src/constants/initial-data.ts　ファイルを作成します。

```sh
% mkdir -p src/constants && touch src/constants/initial-data.ts
```

```
/**
 * アプリケーション初期データ定義
 *
 * このモジュールはアプリケーション起動時に使用される
 * ページ、アイデア、TODOの初期データを提供します。
 */
import type { Page, Idea, Todo } from "@/types";

// サイドバーに表示されるページの初期データ
// 各ページはカテゴリ別にコンテンツをフィルタリングする役割を持つ
export const INITIAL_PAGES: Page[] = [
  {
    id: "1",
    title: "全般",
    isActive: true,
    category: "general",
    emoji: "✅",
  },
  {
    id: "2",
    title: "メインプロジェクト",
    isActive: false,
    category: "work",
    emoji: "💼",
  },
  {
    id: "3",
    title: "学習",
    isActive: false,
    category: "learning",
    emoji: "🎓",
  },
  {
    id: "4",
    title: "生活面（プライベート）",
    isActive: false,
    category: "personal",
    emoji: "🏠",
  },
];

// デモ用のアイデア初期データ
// 実際の運用では空配列または外部データソースから読み込む
export const INITIAL_IDEAS: Idea[] = [
  {
    id: "1",
    text: "個人ポートフォリオサイトを構築する",
    createdAt: new Date("2025-05-15"),
    category: "general",
  },
  {
    id: "2",
    text: "React の状態管理についての記事を読む",
    createdAt: new Date("2025-05-16"),
    category: "work",
  },
  {
    id: "3",
    text: "個人開発の開発計画を立てる",
    createdAt: new Date("2025-05-17"),
    category: "work",
  },
  {
    id: "4",
    text: "週末旅行を計画する",
    createdAt: new Date("2025-05-18"),
    category: "personal",
  },
];

// デモ用のTODO初期データ
// 様々なステータスとカテゴリのサンプルを含む
export const INITIAL_TODOS: Todo[] = [
  {
    id: "1",
    title: "デザインシステムの調査",
    description:
      "## 概要\n現代的なデザインシステムとコンポーネントライブラリを調査\n\n## 目的\nデザインシステムとコンポーネントライブラリを調査し、最適なものを選定する\n\n## 方法\n- 現代的なデザインシステムとコンポーネントライブラリを調査\n- 調査結果をまとめる",
    completed: false,
    createdAt: new Date("2025-05-15"),
    updatedAt: new Date("2025-05-15"),
    category: "work",
  },
  {
    id: "2",
    title: "開発環境のセットアップ",
    description: "必要なツールをインストールし、ワークスペースを設定",
    completed: true,
    createdAt: new Date("2025-05-14"),
    updatedAt: new Date("2025-05-16"),
    category: "work",
  },
  {
    id: "3",
    title: "ワイヤーフレームの作成",
    description: "アプリケーションの初期ワイヤーフレームを設計",
    completed: false,
    createdAt: new Date("2025-05-16"),
    updatedAt: new Date("2025-05-16"),
    category: "work",
  },
  {
    id: "4",
    title: "1週間の食事の計画",
    description: "1週間の食事の計画を立てる",
    completed: false,
    createdAt: new Date("2025-05-17"),
    updatedAt: new Date("2025-05-17"),
    category: "personal",
  },
  {
    id: "5",
    title: "React Hooksの記事を書く",
    description: "React Hooksの学習をまとめる記事を書く",
    completed: true,
    createdAt: new Date("2025-05-12"),
    updatedAt: new Date("2025-05-15"),
    category: "learning",
  },
  {
    id: "6",
    title: "プロジェクト提案書のレビュー",
    description: "新しいクライアントの提案書をチェック",
    completed: false,
    createdAt: new Date("2025-05-18"),
    updatedAt: new Date("2025-05-18"),
    category: "general",
  },
];

```



### 4. コンテキストの定義
### 5. サイドバーコンポーネントの作成
### 6. ページ追加ダイアログの作成
### 7. アプリケーションの統合




## Chapter 05 アイデアブロックの実装
## Chapter 06 ToDo データベース機能の実装
## Chapter 07 GitHub Pages へのデプロイ

 




