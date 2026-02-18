# 合同会社ELI コーポレートサイト

https://eli-co.jp 用の1ページ完結コーポレートサイトです。GitHub Pages でホスティングし、お名前.com のドメイン `eli-co.jp` を紐づけて公開します。

## 公開前の作業

1. **会社情報の記入**  
   `会社情報_記入用.md` を参照し、`index.html` 内の「【要入力】」を検索して、所在地・設立・代表・お問い合わせ先に置き換えてください。

2. **リンクの確認**  
   Footer の YouTube / X のURLを必要に応じて変更してください。

## GitHub Pages で公開する手順

### 1. リポジトリの作成とアップロード

1. GitHub で新規リポジトリを作成する（例: `eli-co-website`）。Public、README なしでOK。
2. このフォルダ（`index.html` と `main.css` があるディレクトリ）で以下を実行する:

   ```bash
   cd /path/to/eli-co-website
   git init
   git add index.html main.css
   git commit -m "Initial commit: ELI corporate site"
   git branch -M main
   git remote add origin https://github.com/あなたのユーザー名/eli-co-website.git
   git push -u origin main
   ```

   （`/path/to/eli-co-website` と `あなたのユーザー名` は実際の値に置き換える）

### 2. GitHub Pages の有効化

1. リポジトリの **Settings** → **Pages**
2. **Source**: Deploy from a branch
3. **Branch**: `main`、フォルダは `/ (root)` を選択して Save
4. 数分後、`https://あなたのユーザー名.github.io/eli-co-website/` で表示されればOK

### 3. カスタムドメイン eli-co.jp の設定

#### GitHub 側

1. 同じ **Settings** → **Pages** の **Custom domain** に `eli-co.jp` を入力して Save
2. **Enforce HTTPS** にチェックを入れる（DNS 反映後に行う）

#### お名前.com 側（DNS）

1. お名前.com Navi にログイン → **ドメイン** → **eli-co.jp** を選択
2. **DNS設定/転送設定** を開く
3. 次のいずれかで設定する:

   **方法A: CNAME でサブドメインを使う場合（例: www.eli-co.jp）**

   - ホスト名: `www`（または空欄でルートの場合は別設定）
   -  TYPE: CNAME
   - VALUE: `あなたのユーザー名.github.io.`（末尾のドットを忘れずに）

   **方法B: ルートドメイン（eli-co.jp）を使う場合**

   - お名前.comのDNSで **Aレコード** を追加:
     - ホスト名: 空（または `@`）
     - TYPE: A
     - VALUE: 
       - `185.199.108.153`
       - `185.199.109.153`
       - `185.199.110.153`
       - `185.199.111.153`
   - あわせて **CNAME**（ホスト名 `www` → `あなたのユーザー名.github.io.`）を設定すると、`www.eli-co.jp` も同じサイトになります。

4. 変更を保存し、最大48時間（多くの場合は数分〜1時間）で反映を待つ

#### 最終確認

- ブラウザで `https://eli-co.jp` を開き、サイトが表示され、鍵マークで HTTPS になっていれば完了
- Apple Developer Program の登録画面の「Webサイト」欄に `https://eli-co.jp` を入力する

## ファイル構成

```
eli-co-website/
├── index.html      # トップページ
├── main.css        # スタイル
├── 会社情報_記入用.md
└── README.md       # 本ファイル
```

## 技術

- 静的 HTML/CSS のみ（JavaScript はスムーズスクロール用の標準機能のみ）
- レスポンシブ対応
- GitHub Pages は Jekyll を使わず静的ファイルのまま公開
