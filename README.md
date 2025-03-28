# Vite with Biome on Devcontainer
## 環境
- Ubuntu on WSL2
  - Docker
- VSCode
  - `Dev Containers`，`Remote Development`拡張機能をインストール

**参考：[Dev Container on WSL2で開発環境構築](https://zenn.dev/ykdev/articles/14a108290e24f9)**

## プロジェクトの開発方法
### 初期設定
1. VSCodeをインストールし，上記を参考に，VSCode内で`Dev Containers`，`Remote Development`拡張機能をインストール
2. このリポジトリをクローンする（WSL上で`git clone https://github.com/yif11/Team2.git`する）
3. WSL上で`Team2`直下に移動（`cd /path/to/Team2/`）し，`code .`してVSCode上でプロジェクトを開く
4. VSCode画面右下の`Reopen In Container`をクリックし，DevContainer（仮想環境）で開く
5. `Ctrl + @`のショートカットキーでコンソールが開くので，そこで`npm init`コマンドを入力（必要なライブラリがインストールされる）

### 開発手順
[このサイト（https://zenn.dev/ynakashi/articles/1658c90cc3b673）](https://zenn.dev/ynakashi/articles/1658c90cc3b673)を参考にしてください  
**GUIでの操作をする際は，masterブランチではなく自分のブランチであることを確認してから作業するようにしてください**  
不明点があればお互い相談し合いましょう  
触るのは基本的に`src`ディレクトリ以下だと思います  

## プロジェクトの実行方法
ターミナルで`npm run dev -- --host`をするとVSCode画面の右下に`Open In Browser`が出るため，それをクリック

## ディレクトリ構造
- `index.html`: Webページのルート
- `src`: プロジェクトのコード（設定ファイル以外のコード）を格納
  - `main.tsx`: `index.html`から呼び出すページ
  - `App.tsx`: `main.tsx`から呼び出すコンポーネント
  - `index.css`: `Tailwind CSS`を使う宣言を記述

## 使っているライブラリ・フレームワーク
### Vite
- フロントエンドのビルドツール
- Reactプロジェクトのテンプレートを作成

### Biome
- **コードを整形してくれる**
  - ESLint + Prettierの代替ツール
  - リント + フォーマットツール
  - ファイルを保存したときに自動で実行されるようにしている（`.vscode/settings.json`）

### Tailwind CSS
`.css`ファイルを用意せず，HTMLのクラス要素に直接スタイルを当てるためのフレームワーク

## 設定ファイル群
### `.vscode/settings.json`
- タブサイズをスペース2個分に指定

### `.npmrc`
`npm install [library]`したときに，自動でバージョン固定オプション`--save-exact`を追加するように指定

### `.devcontainer/devcontainer.json`
- devcontainerの設定ファイル
- `Node v22`と`GitHub CLI（GitHubの便利ツール）`，`Biome`を自動でインストールするように指定

### `biome.json`
Biomeの設定ファイル

## GeminiAPIの取得と設定
このプロジェクトで Gemini API を利用するには、各自で APIキー を取得し、.env ファイルに設定する必要があります。
### Gemini APIキーの取得方法
1. Google の AI Studio にアクセス
2. Google アカウントでログイン
3. 「API キーを作成」ボタンをクリック
4. 表示された API キーをコピーする

### .env ファイルの作成と設定
プロジェクトルートに .env ファイルを作成し、以下の内容を追加してください：
VITE_GEMINI_API_KEY=ここに取得したAPIキーを貼り付ける
VITE_GEMINI_API_URL=https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-pro:generateContent


