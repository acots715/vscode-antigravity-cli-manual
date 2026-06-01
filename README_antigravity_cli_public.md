# VS CodeでAntigravity CLIを使う手順書

このREADMEは、VS Codeのターミナルから **Antigravity CLI** を使うための手順書です。

## 目次

- [1. Antigravity CLIとは](#1-antigravity-cliとは)
- [2. VS Codeに入れるの？PC本体に入れるの？](#2-vs-codeに入れるのpc本体に入れるの)
- [3. Gemini CLI / Gemini Code Assistとの関係](#3-gemini-cli--gemini-code-assistとの関係)
- [4. VS Codeでターミナルを開く](#4-vs-codeでターミナルを開く)
- [5. Antigravity CLIをインストールする](#5-antigravity-cliをインストールする)
- [6. インストールできたか確認する](#6-インストールできたか確認する)
- [7. VS Codeでプロジェクトを開く](#7-vs-codeでプロジェクトを開く)
- [8. Antigravity CLIを起動する](#8-antigravity-cliを起動する)
- [9. 初回起動時に聞かれること](#9-初回起動時に聞かれること)
- [10. コマンド実行の許可を聞かれた場合](#10-コマンド実行の許可を聞かれた場合)
- [11. AI coding agentsの注意文が出た場合](#11-ai-coding-agentsの注意文が出た場合)
- [12. 最初に聞くおすすめの文章](#12-最初に聞くおすすめの文章)
- [13. 毎回の使い方まとめ](#13-毎回の使い方まとめ)
- [14. 困ったとき](#14-困ったとき)

---

## 1. Antigravity CLIとは

Antigravity CLIは、AIにコードやプロジェクトの相談ができるコマンド型ツールです。

WordPressテーマのフォルダで起動すると、たとえば以下のような相談ができます。

- テーマ全体の構成を確認する
- PHP / CSS / JavaScript の役割を整理する
- エラーの原因を探す
- WordPressテーマ内のセクションを作成する
- CSS / SCSSのスタイルを修正する
- ACFやテンプレート構成に合わせた実装案を出してもらう
- ファイルを編集してもらう

---

## 2. VS Codeに入れるの？PC本体に入れるの？

Antigravity CLIは、VS Codeの拡張機能として入れるものではありません。

WindowsやMacなど、**PC本体にインストール**します。

ただし、インストール作業や起動は、VS Codeのターミナルからできます。

```text
PC本体に Antigravity CLI をインストール
↓
VS Codeでプロジェクトを開く
↓
VS Codeのターミナルを開く
↓
agy と入力して起動
↓
AIに指示・質問する
```

---

## 3. Gemini CLI / Gemini Code Assistとの関係

2026年6月時点では、Googleから **Gemini Code Assist / Gemini CLI から Antigravity / Antigravity CLI への移行** が案内されています。

これまで、Geminiは以下のような方法で使うことができました。

```text
Gemini Code Assist：VS Codeの拡張機能として使う
Gemini CLI：ターミナルで gemini コマンドを使う
```

今後は、以下のように考えるとわかりやすいです。

```text
旧：Gemini Code Assist / Gemini CLI
新：Antigravity / Antigravity CLI
```

個人利用・無料利用・Google AI Pro / Ultra などで利用している場合は、Antigravity CLIへの移行を前提にします。

### Google Workspaceアカウントの場合

Gemini Code Assist Standard / Enterprise を利用している場合は、契約内容や管理者側の設定によって利用方法が異なる可能性があります。

このREADMEでは、個人利用や無料利用でも進めやすいように、Antigravity CLIを使う手順をまとめています。

---

## 4. VS Codeでターミナルを開く

VS Codeを開き、上部メニューから以下をクリックします。

```text
ターミナル → 新しいターミナル
```

ショートカットで開く場合は以下です。

### Windowsの場合

```text
Ctrl + Shift + `
```

### Macの場合

```text
Control + Shift + `
```

### Windowsのターミナル種類について

WindowsのVS Codeでは、ターミナルの種類を選べます。

```text
PowerShell
Command Prompt / コマンドプロンプト
Git Bash
```

この手順書では、今後の制作作業も考えて **PowerShell** を基本にします。

`git`、`npm`、`node`、`wp-cli`、`Antigravity CLI` などを使って、サーバー作成・テーマインポート・制作作業まで進めたい場合は、PowerShellを標準にしておくと扱いやすそうです。

---

## 5. Antigravity CLIをインストールする

使っているPCに合わせて、以下のどちらかを実行します。

### Windowsの場合

VS Codeのターミナル右上にある `＋` や `▼` から、`PowerShell` を選択します。

以下を貼り付けてEnterを押します。

```powershell
powershell -ExecutionPolicy Bypass -Command "irm https://antigravity.google/cli/install.ps1 | iex"
```

インストールが完了したら、VS Codeのターミナルを一度閉じて、もう一度新しいターミナルを開きます。

### Macの場合

以下を貼り付けてEnterを押します。

```bash
curl -fsSL https://antigravity.google/cli/install.sh | bash
```

インストールが完了したら、VS Codeのターミナルを一度閉じて、もう一度新しいターミナルを開きます。

---

## 6. インストールできたか確認する

新しく開いたターミナルで、以下を入力します。

### Windowsの場合

```powershell
agy --version
```

または、

```powershell
where.exe agy
```

### Macの場合

```bash
agy --version
```

または、

```bash
which agy
```

バージョン番号や `agy` の場所が表示されればOKです。

### `agy not found` と出る場合

インストール直後の場合は、ターミナルにPATHが反映されていない可能性があります。

まずは以下を試してください。

```text
1. VS Codeのターミナルを閉じる
2. 新しいターミナルを開く
3. agy --version を実行する
```

それでも解決しない場合は、もう一度インストールコマンドを実行してください。

---

## 7. VS Codeでプロジェクトを開く

Antigravity CLIを使いたいプロジェクトフォルダをVS Codeで開きます。

WordPressテーマで使う場合は、使用しているローカル環境によってフォルダの場所が異なります。

目安は以下の場所です。

```text
wp-content / themes / テーマ名
```

Localを使っている場合の例：

```text
Local Sites / サイト名 / app / public / wp-content / themes / テーマ名
```

MAMP、XAMPP、Docker、手動構築環境などを使っている場合は、自分の環境の `wp-content/themes/テーマ名` フォルダを開いてください。

---

## 8. Antigravity CLIを起動する

テーマフォルダにいる状態で、以下を入力します。

```bash
agy
```

起動後、アカウント名・モデル名・作業フォルダが表示されればOKです。

```text
Antigravity CLI 1.0.3
your-account@example.com
Gemini 3.5 Flash
~/path/to/project
```

---

## 9. 初回起動時に聞かれること

初回起動時には、いくつか設定画面が表示される場合があります。

### ログイン方法

初回起動時には、ログイン方法を選ぶ画面が表示される場合があります。

```text
1. Google OAuth
2. Use a Google Cloud project
```

通常利用では、基本的に `1. Google OAuth` を選びます。

個人のGoogleアカウントや、通常のGoogle Workspaceアカウントでログインして使う場合は `1. Google OAuth` です。

`1. Google OAuth` を選んでEnterを押すと、ブラウザが開いてGoogleログイン画面が表示されます。

使用したいGoogleアカウントを選択し、ログインを完了してください。

#### 認証コードが表示された場合

ログイン後、ブラウザに認証コードが表示される場合があります。

その場合は、表示された認証コードをコピーします。

その後、VS Codeのターミナルに戻り、以下のような表示を探します。

```text
authorization code:
```

この `authorization code:` の箇所に認証コードを貼り付けて、Enterを押します。

ターミナル側でAntigravity CLIの画面が進めば、ログイン完了です。

認証コードは、Antigravity CLIにログインするための一時的なコードです。他の人には共有しないでください。


### 表示テーマ

表示テーマを選ぶ画面が出た場合は、好きなテーマを選んでEnterを押します。

```text
terminal
light
dark
tokyo night
```

### データ利用への同意

Antigravity CLIの改善のために、データ利用への同意画面が表示される場合があります。

必要がなければチェックを外してから `Done` を選択してください。

チェックが外せない場合は、そのまま `Done` で進めても大丈夫です。

あとから変更したい場合は、Antigravityの設定画面で `Enable Telemetry` を確認します。

### フォルダの信頼確認

以下のような確認が出た場合は、自分が作業するプロジェクトフォルダであれば `Yes, I trust this folder` を選びます。

```text
Do you trust the contents of this project?
```

知らないフォルダや、安全性が分からないフォルダでは `No, exit` を選びます。

---

## 10. ターミナル操作の確認が出た場合

Antigravity CLIが、ファイル確認などのためにターミナル上で操作を行おうとすると、確認画面が表示される場合があります。

```text
Do you want to proceed?
1. Yes
2. Yes, and always allow in this conversation...
3. Yes, and always allow... Persist to settings.json
4. No
```

基本は `1. Yes` を選びます。

`2` はこの会話中だけ、同じ種類のコマンドを毎回確認なしで許可します。

`3` は今後も確認なしで許可する設定が保存されるため、初心者向けにはおすすめしません。

知らないコマンドや不安なコマンドの場合は、`4. No` を選んでください。

---

## 11. AI coding agentsの注意文が出た場合

以下のような注意文が出る場合があります。

```text
AI coding agents are known to have certain security risks,
including autonomous code execution, data exfiltration,
prompt injection and supply chain risks.
Ensure that you monitor and verify all actions taken by the agent.
```

これは、AIコーディングエージェントには以下のようなリスクがあるため、AIが行った作業は必ず人間が確認してください、という注意です。

- 自動コード実行
- データ流出
- プロンプトインジェクション
- サプライチェーンリスク

Antigravity CLIに任せた作業でも、変更内容は必ず自分で確認してください。

---

## 12. 最初に聞くおすすめの文章

いきなりファイルを編集させず、まずは確認だけしてもらうのがおすすめです。

```text
このWordPressテーマの構成を確認してください。
まずはファイルを編集せず、主要なPHP、CSS、JavaScriptファイルの役割を一覧で説明してください。
```

修正したい場合は、先に方針だけ出してもらうと安全です。

```text
まず変更方針だけ提案してください。
まだファイルは編集しないでください。
```

方針を確認して問題なければ、次にこう依頼します。

```text
この方針で修正してください。
変更したファイル名と変更内容も最後にまとめてください。
```

---

## 13. 毎回の使い方まとめ

毎回使う時は、以下の流れです。

```text
1. VS Codeでプロジェクトを開く
2. ターミナルを開く
3. 必要ならプロジェクトフォルダへ移動する
4. agy を実行する
5. まずは「ファイルは編集せず確認だけ」と依頼する
```

### Windowsの場合

今いる場所を確認します。

```powershell
Get-Location
```

プロジェクトフォルダへ移動が必要な場合は以下です。

```powershell
cd "プロジェクトフォルダのパス"
agy
```

Localを使っている場合の例：

```powershell
cd "$env:USERPROFILE\Local Sites\サイト名\app\public\wp-content\themes\テーマ名"
agy
```

### Macの場合

今いる場所を確認します。

```bash
pwd
```

プロジェクトフォルダへ移動が必要な場合は以下です。

```bash
cd "プロジェクトフォルダのパス"
agy
```

Localを使っている場合の例：

```bash
cd "/Users/ユーザー名/Local Sites/サイト名/app/public/wp-content/themes/テーマ名"
agy
```

---

## 14. 困ったとき

画面が止まったように見える場合は、以下を試してください。

```text
1. Control + C で一度終了する
2. VS Codeのターミナルを閉じる
3. 新しいターミナルを開く
4. agy --version を実行する
5. agy で起動し直す
```
