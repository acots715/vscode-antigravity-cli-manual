# AIコーディング支援ツール導入メモ

WordPress制作時にAIコーディング支援を使えるようにするため、VS Codeで利用するAIコーディング支援ツールの導入手順をまとめています。

このリポジトリでは、以下の2種類の手順書を用意しています。

## 手順書一覧

| ファイル                                                                 | 内容                                   | 想定用途                                                 |
| -------------------------------------------------------------------- | ------------------------------------ | ---------------------------------------------------- |
| [README_antigravity_cli_public.md](README_antigravity_cli_public.md) | Antigravity CLIの導入手順                 | Gemini CLI / Gemini Code Assist からAntigravityへ移行する場合 |
| [README_gemini_code_assist_cli.md](README_gemini_code_assist_cli.md) | Gemini Code Assist / Gemini CLIの導入手順 | Gemini Code AssistやGemini CLIを利用できる環境で使う場合           |

## 使い分け

### Antigravity CLIを使う場合

GoogleからGemini Code Assist / Gemini CLI から Antigravity / Antigravity CLI への移行案内が出ているため、個人利用・無料利用・Google AI Pro / Ultra などで利用する場合は、基本的に **Antigravity CLI** を使う前提で考えます。

VS Codeのターミナルから `agy` コマンドを実行して使います。

```bash
agy
```

詳しい手順は以下にまとめています。

[Antigravity CLIの導入手順](README_antigravity_cli_public.md)

### Gemini Code Assist / Gemini CLIを使う場合

Gemini Code Assist Standard / Enterprise などの法人向けライセンスを利用している場合や、管理者側の設定でGemini Code Assist / Gemini CLIを利用できる場合は、こちらの手順を参考にします。

Gemini Code AssistはVS Code拡張機能として使い、Gemini CLIはターミナルから `gemini` コマンドで使います。

```bash
gemini
```

詳しい手順は以下にまとめています。

[Gemini Code Assist / Gemini CLIの導入手順](README_gemini_code_assist_cli.md)

## 現時点の方針

一旦、以下の前提で確認しています。

```text
環境：ローカル
エディタ：VS Code
AIコーディング支援：Antigravity または Gemini
```

ローカル環境やサーバー環境、Git管理をどの段階から入れるかによって、実際の運用方法は変わる可能性があります。

フォルダ構成、コーディングルール、デザインルール、AIへの指示の出し方などは、実際の制作フローに合わせて試しながら調整していく想定です。

## 注意

AIコーディング支援ツールにファイル編集を任せる場合でも、変更内容は必ず確認してください。

特にWordPressテーマ制作では、PHPテンプレート、CSS / SCSS、JavaScript、ACF、管理画面入力内容などが関係するため、AIの提案をそのまま反映せず、制作ルールに合っているか確認しながら使用します。
