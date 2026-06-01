# VS CodeでGemini Code Assist / Gemini CLIを使う手順書

このREADMEは、VS Codeで **Gemini Code Assist**、またはVS Codeのターミナルから **Gemini CLI** を使うための手順書です。

> 注意：2026年6月時点では、個人利用・無料利用・Google AI Pro / Ultra などの利用形態では、Gemini Code Assist / Gemini CLI から Antigravity / Antigravity CLI への移行案内が出ています。
>
> Gemini Code Assist Standard / Enterprise などの法人向けライセンスを利用している場合は、契約内容や管理者側の設定によって扱いが異なる可能性があります。

## 目次

- [1. この手順書の目的](#1-この手順書の目的)
- [2. Gemini Code Assist と Gemini CLI の違い](#2-gemini-code-assist-と-gemini-cli-の違い)
- [3. VS CodeにGemini Code Assistを入れる](#3-vs-codeにgemini-code-assistを入れる)
- [4. Gemini Code Assistにログインする](#4-gemini-code-assistにログインする)
- [5. Gemini CLIをインストールする](#5-gemini-cliをインストールする)
- [6. Gemini CLIを起動する](#6-gemini-cliを起動する)
- [7. WordPressテーマフォルダで使う](#7-wordpressテーマフォルダで使う)
- [8. 最初に聞くおすすめの文章](#8-最初に聞くおすすめの文章)
- [9. コマンド実行や編集を許可する場合](#9-コマンド実行や編集を許可する場合)
- [10. 困ったとき](#10-困ったとき)

---

## 1. この手順書の目的

WordPress制作時にAIコーディング支援を使えるようにするため、以下の2つの使い方をまとめています。

- VS Code拡張機能として使う **Gemini Code Assist**
- VS Codeのターミナルから使う **Gemini CLI**

WordPressテーマフォルダで使うと、たとえば以下のような相談ができます。

- テーマ全体の構成を確認する
- PHP / CSS / JavaScript の役割を整理する
- エラーの原因を探す
- 変更方針を提案してもらう
- セクション作成やスタイル修正を補助してもらう
- 未使用CSS候補を探す

---

## 2. Gemini Code Assist と Gemini CLI の違い

| 種類 | 使い方 | 主な用途 |
| --- | --- | --- |
| Gemini Code Assist | VS Codeの拡張機能として使う | エディタ内でのチャット、コード補完、コード説明 |
| Gemini CLI | ターミナルで `gemini` コマンドを使う | プロジェクトフォルダ内での構成確認、ファイル操作、修正補助 |

### ざっくりした考え方

```text
Gemini Code Assist：VS Codeの中で使うAI補助
Gemini CLI：ターミナルから使うAIコーディングエージェント
```

どちらもGoogleアカウントでのログインが必要になる場合があります。

---

## 3. VS CodeにGemini Code Assistを入れる

VS Codeを開きます。

左側の拡張機能アイコンをクリックします。

またはショートカットで開きます。

### Windowsの場合

```text
Ctrl + Shift + X
```

### Macの場合

```text
Command + Shift + X
```

検索欄に以下を入力します。

```text
Gemini Code Assist
```

Google公式の **Gemini Code Assist** を選び、`Install` をクリックします。

インストール後、必要に応じてVS Codeを再起動します。

---

## 4. Gemini Code Assistにログインする

インストール後、VS Code上にGemini Code Assistのアイコンやチャット欄が表示されます。

`Sign in with Google` や `Login` が表示された場合はクリックし、使用したいGoogleアカウントでログインします。

Google Workspaceアカウントを使う場合は、管理者側の設定やライセンスによって利用できる範囲が変わる場合があります。

---

## 5. Gemini CLIをインストールする

Gemini CLIは、VS Codeに入れる拡張機能ではなく、PC本体にインストールして使うコマンドです。

### Windowsの場合

VS Codeのターミナルを開きます。

Windowsでは、今後の制作作業も考えて **PowerShell** を基本にします。

以下を貼り付けてEnterを押します。

```powershell
npm install -g @google/gemini-cli
```

### Macの場合

VS Codeのターミナルを開き、以下を貼り付けてEnterを押します。

```bash
npm install -g @google/gemini-cli
```

Homebrewを使う場合は、以下でもインストールできます。

```bash
brew install gemini-cli
```

---

## 6. Gemini CLIを起動する

インストール後、新しいターミナルを開いて確認します。

```bash
gemini --version
```

バージョンが表示されればOKです。

起動する場合は、以下を入力します。

```bash
gemini
```

初回起動時にGoogleログインを求められる場合があります。

画面の案内に従って、使用したいGoogleアカウントでログインします。

---

## 7. WordPressテーマフォルダで使う

Gemini CLIを使いたいプロジェクトフォルダをVS Codeで開きます。

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

テーマフォルダでターミナルを開き、以下を入力します。

```bash
gemini
```

---

## 8. 最初に聞くおすすめの文章

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

## 9. コマンド実行や編集を許可する場合

Gemini CLIが、ファイル確認や修正のためにターミナル操作やファイル編集の許可を求める場合があります。

これは、

```text
この操作を実行してもよいですか？
```

という確認です。

内容が分かる・問題なさそうな場合だけ許可します。

知らないコマンドや不安な操作の場合は、許可せずに内容を確認してください。

AIにファイル編集を任せた場合も、変更内容は必ず自分で確認してください。

---

## 10. 困ったとき

### `gemini: command not found` と出る場合

Gemini CLIが見つからない状態です。

以下を確認します。

### Windowsの場合

```powershell
where.exe gemini
```

### Macの場合

```bash
which gemini
```

何も表示されない場合は、インストールが完了していないか、PATHが反映されていない可能性があります。

ターミナルを閉じて開き直すか、もう一度インストールコマンドを実行してください。

### npmで権限エラーが出る場合

Macで以下のようなエラーが出る場合があります。

```text
npm error code EACCES
permission denied
```

この場合は、npmのグローバルインストール先に書き込み権限がない可能性があります。

Macの場合は、Homebrewでのインストールも検討してください。

```bash
brew install gemini-cli
```

### Gemini Code Assistのチャット欄が表示されない場合

VS Codeの拡張機能画面で、`Gemini Code Assist` がインストール済みか確認します。

```text
@installed Gemini
```

表示されない場合は、再インストールまたはVS Codeの再起動を試します。
