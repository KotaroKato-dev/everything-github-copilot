# Everything GitHub Copilot

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
![VS Code](https://img.shields.io/badge/-VS%20Code-007ACC?logo=visual-studio-code&logoColor=white)
![GitHub Copilot](https://img.shields.io/badge/-GitHub%20Copilot-000000?logo=github&logoColor=white)
![TypeScript](https://img.shields.io/badge/-TypeScript-3178C6?logo=typescript&logoColor=white)
![Python](https://img.shields.io/badge/-Python-3776AB?logo=python&logoColor=white)
![Go](https://img.shields.io/badge/-Go-00ADD8?logo=go&logoColor=white)
![Rust](https://img.shields.io/badge/-Rust-000000?logo=rust&logoColor=white)

GitHub Copilot専用のカスタムエージェント、プロンプト、インストラクションコレクション。

VS Code + GitHub Copilotで使用できる **28の特化エージェント**（+6のオーケストレーター）、**13のプロンプトコマンド**、**12のインストラクション**を提供します。

---

## 概要

このリポジトリは、VS CodeのGitHub Copilotを最大限に活用するための設定・エージェント・プロンプトをまとめたコレクションです。cloneするだけで、すぐに本番レベルのAIコーディング環境が整います。

**主な特徴:**

- 言語別・ドメイン別に特化した28のカスタムエージェント
- TDD・セキュリティレビュー・ドキュメント更新などの自動化ワークフロー
- C++・Go・Java・Kotlin・Python・Rust・TypeScriptなど11言語のコーディングインストラクション
- 再利用可能な13のプロンプトコマンド

---

## セットアップ

```bash
git clone https://github.com/your-org/everything-github-copilot.git
cd everything-github-copilot
```

このリポジトリをVS Codeで開くだけで、GitHub Copilotが `.github/` 以下の全設定を自動的に読み込みます。追加のインストールは不要です。

---

## ディレクトリ構造

```
.github/
├── agents/               # 28の特化エージェント + 6のオーケストレーター
├── prompts/              # 13のプロンプトコマンド
├── instructions/         # 共通 + 11言語固有のインストラクション
└── copilot-instructions.md  # グローバルインストラクション
```

---

## エージェント一覧

### オーケストレーター（ワークフロー制御）

| エージェント | 説明 |
|------------|------|
| `impl` | 実行計画に従ってTDDで実装を行う |
| `issue` | GitHubイシューの分析・対応計画を作成する |
| `orchestrator` | 複数エージェントの並列実行を調整する |
| `plan` | 機能実装の計画を立案する |
| `pr` | プルリクエストのサマリーと説明を生成する |
| `review` | コードレビューを実施する |

### 特化エージェント

| エージェント | 説明 |
|------------|------|
| `architect` | システム設計・アーキテクチャの意思決定 |
| `build-error-resolver` | ビルドエラーの診断・修正 |
| `chief-of-staff` | マルチチャンネルのコミュニケーション管理 |
| `code-reviewer` | コードレビューとベストプラクティスの適用 |
| `cpp-build-resolver` | C++ビルドエラーの診断・修正 |
| `cpp-reviewer` | C++コードレビュー |
| `database-reviewer` | PostgreSQLスキーマ設計・クエリ最適化 |
| `doc-updater` | ドキュメントの更新・維持 |
| `docs-lookup` | ライブラリ・フレームワークのドキュメント参照 |
| `e2e-runner` | E2Eテストの実行・管理（Playwright） |
| `flutter-reviewer` | Flutter/Dartコードレビュー |
| `go-build-resolver` | Goビルドエラーの診断・修正 |
| `go-reviewer` | Goコードレビュー |
| `harness-optimizer` | エージェントハーネスの設定最適化 |
| `java-build-resolver` | Java/Maven/Gradleビルドエラーの診断・修正 |
| `java-reviewer` | Java/Spring Bootコードレビュー |
| `kotlin-build-resolver` | Kotlin/Gradleビルドエラーの診断・修正 |
| `kotlin-reviewer` | Kotlin/Android/KMPコードレビュー |
| `loop-operator` | 自律ループ実行の安全な監視 |
| `planner` | 複雑な機能の実装計画立案 |
| `python-reviewer` | Pythonコードレビュー |
| `pytorch-build-resolver` | PyTorchビルド・学習エラーの診断・修正 |
| `refactor-cleaner` | デッドコード削除・リファクタリング |
| `rust-build-resolver` | Rustビルドエラーの診断・修正 |
| `rust-reviewer` | Rustコードレビュー |
| `security-reviewer` | セキュリティ脆弱性の分析・修正 |
| `tdd-guide` | テスト駆動開発のガイド |
| `typescript-reviewer` | TypeScript/JavaScriptコードレビュー |

---

## プロンプト一覧

`.github/prompts/` 内の13のプロンプトコマンド:

| プロンプト | 説明 |
|-----------|------|
| `build-fix` | ビルドエラーを自動診断・修正する |
| `code-review` | コードレビューチェックリストを実行する |
| `doc-update` | ドキュメントを最新状態に更新する |
| `docs` | ドキュメントを生成・整備する |
| `e2e` | E2Eテストを作成・実行する |
| `learn` | コードベースを分析して学習メモを作成する |
| `plan` | 機能実装の詳細計画を立案する |
| `quality-gate` | 品質チェックゲートを実行する |
| `refactor` | コードをリファクタリングする |
| `security-review` | セキュリティレビューを実施する |
| `tdd` | TDDサイクル（Red→Green→Refactor）を実行する |
| `test-coverage` | テストカバレッジを分析・改善する |
| `verify` | 実装の検証・確認を行う |

---

## インストラクション一覧

`.github/instructions/` 内の12のインストラクション:

| ファイル | 対象 |
|---------|------|
| `common.instructions.md` | 全ファイル共通のコーディング規約 |
| `cpp.instructions.md` | C++ (`*.cpp`, `*.hpp`, `*.h` など) |
| `csharp.instructions.md` | C# (`*.cs`, `*.csx`) |
| `go.instructions.md` | Go (`*.go`, `go.mod`) |
| `java.instructions.md` | Java (`*.java`) |
| `kotlin.instructions.md` | Kotlin (`*.kt`, `*.kts`) |
| `perl.instructions.md` | Perl (`*.pl`, `*.pm`, `*.t`) |
| `php.instructions.md` | PHP (`*.php`, `composer.json`) |
| `python.instructions.md` | Python (`*.py`, `*.pyi`) |
| `rust.instructions.md` | Rust (`*.rs`) |
| `swift.instructions.md` | Swift (`*.swift`, `Package.swift`) |
| `typescript.instructions.md` | TypeScript/JavaScript (`*.ts`, `*.tsx`, `*.js`, `*.jsx`) |

---

## 使用方法

### カスタムエージェントの呼び出し

VS Codeのチャットパネルで `@` を使ってエージェントを呼び出します:

```
@architect データベース設計についてアドバイスしてください
@code-reviewer このコードをレビューしてください
@security-reviewer 認証ロジックを検査してください
@tdd-guide このクラスのテストを書いてください
@planner 新機能Xの実装計画を立てて
```

### プロンプトの実行

チャットパネルで `/` を入力するとプロンプト一覧が表示されます:

```
/tdd          # TDDサイクルを開始する
/code-review  # コードレビューを実施する
/security-review  # セキュリティレビューを実施する
/plan         # 実装計画を立案する
/refactor     # リファクタリングを実行する
```

---

## コア原則

このコレクションは以下の原則に基づいて設計されています:

1. **イミュータビリティ** — 既存オブジェクトを変更せず、常に新しいオブジェクトを生成する
2. **TDD** — テストを先に書いてから実装する（カバレッジ80%以上）
3. **セキュリティ優先** — 全入力を検証し、機密情報をハードコードしない
4. **小さなファイル** — 1ファイル200〜400行、最大800行
5. **明示的なエラー処理** — エラーを黙って飲み込まない

詳細は [`.github/copilot-instructions.md`](.github/copilot-instructions.md) を参照してください。

---

## ライセンス

[MIT](LICENSE)
