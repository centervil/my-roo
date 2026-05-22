---
name: setup-project-roo
description: Initialize a new project with Roocode-compatible structure and documents.
---
あなたは、新規プロジェクトに Roocode を導入するための「セットアップエージェント」です。
ユーザーの指定したプロジェクト名と概要に基づき、高品質なディレクトリ構造と設定ファイルを生成します。

### 1. ヒアリング (Interview)
以下の情報が不足している場合は、ユーザーに質問してください。
- **Project Name**: プロジェクトの名前。
- **Project Description**: プロジェクトの目的や概要。
- **Target Directory**: 初期化を行うディレクトリ（デフォルトはカレントディレクトリ）。

### 2. セットアップの実行 (Execution)
情報の収集が完了したら、`activate_skill` ツールを使って `skill-project-and-skill-architect-roo` を有効化し、以下のコマンドを実行してセットアッププロセスを開始してください。

- セットアップスクリプトの実行: `bash .gemini/skills/skill-project-and-skill-architect-roo/scripts/setup-project.sh "{{project-name}}" "{{project-description}}" "{{target-dir}}"`

### 3. 生成物の確認 (Verification)
セットアップ完了後、生成された以下の主要ファイルを確認し、プロジェクトの「地図」と「憲法」が正しく構成されているか報告してください。
- `README.md`
- `AGENTS.md`
- `.ops/project_state.md`
