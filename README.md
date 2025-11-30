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

- Node.js 環境（v20.9.0 以上）が構築されたPCが必要です。
- Git/ GitHubの環境を作成する。
- HTML/CSS/JavaScriptの基礎知識が必要です。
- Reactの基礎（Progateレベルの内容）は理解している前提の内容となっております


## 機能要件

1. アイデアブロック機能
   - ページアクセス時にアイデア入力フォームが表示される。
   - 入力したアイデアをブロック形式で縦に一覧表示する。
   - アイデアブロックを追加・削除できる。
   - アイデアブロックをドラッグ&ドロップで並び替えできる。


2. ToDo データベース機能
   - ToDoをテーブル（データベースビュー）で一覧表示する。
   - 表示項目：タイトル、ステータス（未完了／完了）、作成日。
   - 新しいToDoのステータスを切り替えできる。
   - ToDoのステータスを切り替えできる。
   - ToDoを削除できる。

3. 詳細表示機能（左サイドバー）
   - ToDoをクリックすると右側にサイドバーが開く。
   - サイドバー内で以下を編集できる：
     - ToDoタイトル
     - 説明
     - ステータス
   - サイドバーを閉じることができる。

4. ページ管理機能
   - 新しいページを作成できる。
   - ページタブでページを切り替えできる。
   - ページのタイトルを編集できる。
   - ページを削除できる（※最低 1ページは残す）。
   - ページごとに独立した「アイディアブロック」と「ToDo」を保持する。

5. その他
   - アプリケーションがデプロイされており、誰でもアクセスである。

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

ページ状態を管理する Context API を実装します。

src/contexts/page-context.tsx　ファイルを作成します。

```sh
% mkdir -p src/contexts/ && touch src/contexts/page-context.tsx
```

```
import type { ReactNode } from "react";
import { createContext, useContext, useState } from "react";
import type { Page } from "@/types";
import { INITIAL_PAGES } from "@/constants/initial-data";

interface PageContextType {
  pages: Page[];
  activePage: Page;
  addPage: (title: string, emoji: string) => void;
  setActivePage: (pageId: string) => void;
  deletePage: (pageId: string) => void;
  // UI状態（新規ページ作成ダイアログ用）
  newPageTitle: string;
  setNewPageTitle: (title: string) => void;
  newPageEmoji: string;
  setNewPageEmoji: (emoji: string) => void;
  isAddPageDialogOpen: boolean;
  setIsAddPageDialogOpen: (open: boolean) => void;
}

const PageContext = createContext<PageContextType | undefined>(undefined);

interface PageProviderProps {
  children: ReactNode;
}

export function PageProvider({ children }: PageProviderProps) {
  const [pages, setPages] = useState<Page[]>(INITIAL_PAGES);
  const [newPageTitle, setNewPageTitle] = useState("");
  const [newPageEmoji, setNewPageEmoji] = useState("");
  const [isAddPageDialogOpen, setIsAddPageDialogOpen] = useState(false);

  // 現在アクティブなページを取得
  const activePage = pages.find((page) => page.isActive) || pages[0];

  /**
   * 新しいページを作成する
   */
  const addPage = (title: string, emoji: string) => {
    if (title.trim()) {
      const newPage: Page = {
        id: Date.now().toString(),
        title: title.trim(),
        isActive: false,
        category: `page_${Date.now()}`,
        emoji: emoji.trim() || "📝",
      };
      setPages((prev) => [...prev, newPage]);
      setNewPageTitle("");
      setNewPageEmoji("");
      setIsAddPageDialogOpen(false);
    }
  };

  /**
   * アクティブページを変更する
   */
  const setActivePage = (pageId: string) => {
    setPages((prev) =>
      prev.map((page) => ({
        ...page,
        isActive: page.id === pageId,
      }))
    );
  };

  /**
   * ページを削除する
   */
  const deletePage = (pageId: string) => {
    if (pages.length > 1) {
      const updatedPages = pages.filter((page) => page.id !== pageId);

      // 削除されるページがアクティブだった場合、最初のページをアクティブに
      if (pages.find((page) => page.id === pageId)?.isActive) {
        updatedPages[0] = { ...updatedPages[0], isActive: true };
      }

      setPages(updatedPages);
    }
  };

  const value: PageContextType = {
    pages,
    activePage,
    addPage,
    setActivePage,
    deletePage,
    newPageTitle,
    setNewPageTitle,
    newPageEmoji,
    setNewPageEmoji,
    isAddPageDialogOpen,
    setIsAddPageDialogOpen,
  };

  return <PageContext.Provider value={value}>{children}</PageContext.Provider>;
}

/**
 * PageContextにアクセスするためのカスタムフック
 */
// eslint-disable-next-line react-refresh/only-export-components
export function usePageContext() {
  const context = useContext(PageContext);
  if (context === undefined) {
    throw new Error("usePageContext must be used within a PageProvider");
  }
  return context;
}

```

解説：
Context API の実装パターンには重要なポイントがあります：

カスタムフック：usePageContext でコンテキストへのアクセスを簡素化
エラーハンドリング：Provider 外での使用時にエラーを投げる
TypeScript 活用：型安全なインターフェース定義
関数の分離：各操作を独立した関数として定義
このパターンにより、コンポーネント間での状態共有が簡単になります。

そして、// eslint-disable-next-line react-refresh/only-export-components は、

１時的に ESLint のルールを無視するためのコメントです。
一般的に、react の慣習として、１つのファイルからは、１つのコンポーネントを export するルールことが多いです。
しかし、Context Provider とその Hook は密接に関連しているため、同じファイルに置くのが一般的です！

### 5. サイドバーコンポーネントの作成

ページナビゲーション用のサイドバーを実装します

src/components/page-sidebar.tsx を作成します。

```sh
% touch src/components/page-sidebar.tsx
```

```sh
import { Plus, X } from "lucide-react";
import { usePageContext } from "@/contexts/page-context";

export function PageSidebar() {
  const { pages, setActivePage, deletePage, setIsAddPageDialogOpen } =
    usePageContext();

  return (
    <div className="fixed left-0 top-0 h-screen w-64 bg-[#f0edd8] backdrop-blur-sm border-r border-stone-200 flex flex-col shadow-sm z-20">
      {/* サイドバーヘッダー */}
      <div className="p-4 border-b border-stone-200">
        <h1 className="text-xl font-bold text-stone-800">My Issue Tracker</h1>
      </div>

      {/* スクロール可能なページ一覧エリア */}
      <div className="flex-1 overflow-auto">
        <div className="px-3 py-4">
          <h2 className="text-xs font-semibold text-stone-500 uppercase tracking-wider mb-3 px-2">
            ページ
          </h2>
          <div className="space-y-1">
            {pages.map((page) => (
              <div key={page.id} className="group flex items-center">
                {/* ページ選択ボタン */}
                <button
                  onClick={() => setActivePage(page.id)}
                  className={`flex-1 flex items-center px-2 py-2 text-sm rounded-md transition-colors ${
                    page.isActive
                      ? "bg-stone-400/20 text-stone-800 font-medium shadow-sm"
                      : "text-stone-700 hover:bg-stone-400/20 hover:text-stone-800"
                  }`}
                >
                  <span className="mr-3 text-base">{page.emoji}</span>
                  <span className="truncate">{page.title}</span>
                </button>

                {/* ページ削除ボタン - 最後の1ページは削除不可 */}
                {pages.length > 1 && (
                  <button
                    onClick={() => deletePage(page.id)}
                    className="opacity-0 group-hover:opacity-100 p-1 rounded-md text-stone-400 hover:text-red-600 hover:bg-red-50 transition-all"
                  >
                    <X className="w-3 h-3" />
                  </button>
                )}
              </div>
            ))}

            {/* ページ追加ボタン */}
            <button
              onClick={() => setIsAddPageDialogOpen(true)}
              className="w-full flex items-center px-2 py-2 text-sm text-stone-500 hover:text-stone-900 hover:bg-stone-400/20 rounded-md transition-colors"
            >
              <Plus className="w-4 h-4 mr-3" />
              <span>新しいページ</span>
            </button>
          </div>
        </div>
      </div>
    </div>
  );
}

```

解説：
サイドバー UI には以下の要素が含まれています：

固定レイアウト：fixed positioning で画面左端に固定
アクティブ状態：現在選択中のページの視覚的フィードバック
ホバー効果：削除ボタンは hover 時のみ表示（UX 改善）
レスポンシブ対応：スクロール可能なコンテンツエリア
アクセシビリティ：適切な color contrast と focus 状態
ロジックは、コンテキストで管理しているので、マークアップが中心ですね！



### 6. ページ追加ダイアログの作成

新しいページを作成するためのモーダルダイアログコンポーネントを実装します

src/components/add-page-dialog.tsx ファイルを作成します。

```sh
% touch src/components/add-page-dialog.tsx
```

```sh
import React from "react";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import {
  Dialog,
  DialogContent,
  DialogHeader,
  DialogTitle,
} from "@/components/ui/dialog";
import { usePageContext } from "@/contexts/page-context";

export function AddPageDialog() {
  const {
    newPageTitle,
    setNewPageTitle,
    newPageEmoji,
    setNewPageEmoji,
    isAddPageDialogOpen,
    setIsAddPageDialogOpen,
    addPage,
  } = usePageContext();

  const handleAddPage = () => {
    addPage(newPageTitle, newPageEmoji);
  };

  /**
   * Enterキーでのページ作成を可能にする
   */
  const handleKeyDown = (e: React.KeyboardEvent) => {
    if (e.key === "Enter") {
      handleAddPage();
    }
  };

  return (
    <Dialog open={isAddPageDialogOpen} onOpenChange={setIsAddPageDialogOpen}>
      <DialogContent className="sm:max-w-md bg-white/95 border-stone-200">
        <DialogHeader>
          <DialogTitle className="text-stone-800">
            新しいページを作成
          </DialogTitle>
        </DialogHeader>
        <div className="space-y-4">
          <div>
            <label className="block text-sm font-medium text-stone-700 mb-2">
              ページタイトル
            </label>
            <Input
              placeholder="ページタイトル"
              value={newPageTitle}
              onChange={(e) => setNewPageTitle(e.target.value)}
              onKeyDown={handleKeyDown}
              className="border-stone-200 focus:border-stone-500 focus:ring-stone-500"
            />
          </div>
          <div>
            <label className="block text-sm font-medium text-stone-700 mb-2">
              絵文字
            </label>
            <Input
              placeholder="📝"
              value={newPageEmoji}
              onChange={(e) => setNewPageEmoji(e.target.value)}
              onKeyDown={handleKeyDown}
              className="border-stone-200 focus:border-stone-500 focus:ring-stone-500 text-2xl text-center"
              maxLength={2}
            />
            <p className="text-xs text-stone-500 mt-1">
              ページを表す絵文字を入力してください。空白の場合、📝が使用されます。
            </p>
          </div>
          <div className="flex justify-end space-x-2">
            <Button
              variant="outline"
              onClick={() => setIsAddPageDialogOpen(false)}
              className="border-stone-200 text-stone-700 hover:bg-stone-100"
            >
              キャンセル
            </Button>
            <Button
              onClick={handleAddPage}
              disabled={!newPageTitle.trim()}
              className="bg-stone-600 hover:bg-stone-700 text-white"
            >
              ページを作成
            </Button>
          </div>
        </div>
      </DialogContent>
    </Dialog>
  );
}

```

解説：
今回も、コンテキストのフックを呼び出して、コンポーネントを実装しています！

ダイアログコンポーネントの UX としては、：

キーボードサポート：Enter キーでの送信対応
バリデーション：タイトルが空の場合はボタンを無効化
フォーカス管理：ダイアログ開閉時の適切なフォーカス制御
アクセシビリティ：shadcn/ui の Dialog コンポーネントは ARIA 属性を自動で提供
レスポンシブ対応：異なる画面サイズでの表示最適化
shadcn/ui を使用することで、アクセシビリティが自動的に担保される利点があります！


### 7. アプリケーションの統合


アプリケーションの統合
最後に、全てのコンポーネントを統合してメインアプリケーションを完成させます：

src/app.tsx ファイルを編集します。

```tsx
import { PageProvider, usePageContext } from "@/contexts/page-context";
import { PageSidebar } from "@/components/page-sidebar";
import { AddPageDialog } from "@/components/add-page-dialog";

function NotionTodoAppInner() {
  const { activePage } = usePageContext();

  return (
    <div className="min-h-screen bg-[#f0edd8] flex">
      {/* 左サイドバー - ページナビゲーション */}
      <PageSidebar />

      {/* メインコンテンツエリア */}
      <div className="flex-1 flex flex-col ml-64 transition-all duration-300 pr-6">
        {/* トップヘッダー */}
        <div className="backdrop-blur-sm px-6 pt-12 pb-6 space-y-6">
          <div className="text-7xl text-stone-500">{activePage.emoji}</div>
          <h1 className="text-4xl font-bold text-stone-800">
            {activePage.title}
          </h1>
        </div>

        {/* スクロール可能なコンテンツエリア */}
        <div className="flex-1 overflow-auto">この後のタスクで実装！</div>
      </div>

      {/* モーダルダイアログ群 */}
      <AddPageDialog />
    </div>
  );
}

/**
 * アプリケーションのエントリーポイント
 */
export default function NotionTodoApp() {
  return (
    <PageProvider>
      <NotionTodoAppInner />
    </PageProvider>
  );
}
```


解説：
アプリケーション構造の設計において、
Provider パターンで、Context を最上位で提供し、子コンポーネントでアクセスしています！

### 8. 確認

開発サーバーを起動して　以下のようにサイドバーが表示され、
ページの切り替えや追加・削除ができていたら、このタスクは完了です

### 9. git でプロジェクトを管理する

```sh
git add .
git commit -m "サイドバーの実装"
```

### 10. 本章のまとめ

Context とは？
Context は React が提供する、グローバル状態管理の仕組みです。

利点としては、：

Props のバケツリレー（プロップドリリング）問題の解決
React 標準機能（追加ライブラリ不要）で、コンポーネント間でのデータ共有が可能

Context の基本的な使い方は？
Context の基本的な実装パターンは以下の 3 ステップです：

Context の作成：createContext() でコンテキストを作成
Provider でラップ：データを共有したいコンポーネントツリーを Provider でラップ
useContext で使用：子コンポーネントで useContext() を使用してデータにアクセス

// 1. Context作成
const MyContext = createContext();

// 2. Provider でラップ
<MyContext.Provider value={data}>
  <ChildComponent />
</MyContext.Provider>;

// 3. 子コンポーネントで使用
const data = useContext(MyContext);
Context の注意点は？

Context にはパフォーマンス上の注意点があります：

再レンダリング問題：Context の値が変更されると、Provider 内の全ての子コンポーネントが再レンダリングされる
Provider タワー：複数の Context を使用すると、Provider の入れ子が深くなり依存関係が複雑化する
最適化の難しさ：手動での memo 化や複数 Provider による最適化は煩雑になりがち
2025 年現在の推奨事項：

Context API の代替として、以下のライブラリが人気：

Zustand：軽量で使いやすい状態管理
Jotai：原子的な状態管理
Context API は React の基本的な状態管理手法として理解しておくべきですが、
2025 年現在では、より高性能で使いやすい代替ライブラリが多数存在します！


このセクションで学んだこと：

Context API を使用したグローバル状態管理の実装
カスタムフック による Context アクセスの簡素化
TypeScript による型安全な状態管理
Notion 風 UI のサイドバー実装
コンポーネント分離 による保守性の向上

## Chapter 05 アイデアブロックの実装

アイデアを自由にメモして、ドラッグ&ドロップで整理できる機能を実装しましょう！

### immer とは？

Immer は「イミュータブル（不変）な状態更新を、ミュータブル（可変）な記法で書ける」ライブラリです。

React で不変性が重要な理由：

- 仮想 DOM の差分検知：React は前回と今回の状態を比較して効率的に更新を行う
- 参照の比較：オブジェクトの参照が変わることで変更を検知
- 予測可能な状態管理：意図しない副作用を防ぎ、バグを減らす
- タイムトラベルデバッグ：状態の履歴を追跡可能

従来の不変更新の問題点：

```
// 従来の方法：複雑で読みづらい
const newState = {
  ...state,
  ideas: state.ideas.map((idea, index) =>
    index === dragIndex ? { ...idea, position: newPosition } : idea
  ),
};
```


## Chapter 06 ToDo データベース機能の実装
## Chapter 07 GitHub Pages へのデプロイ

 




