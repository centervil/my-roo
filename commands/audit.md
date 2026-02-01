# Slash Command: Audit
このコマンドは、現在のスキャフォールドが Roo Code の公式仕様に適合しているかを監査し、結果をログに記録する標準プロセスを実行します。

## 実行手順

1. **現状把握**:
   - `project_state.md` を読み、現在のフェーズと完了したタスクを確認してください。

2. **監査実行 (Audit)**:
   - `platform-maintainer` モードに切り替え（または呼び出し）、以下の観点で監査を行わせてください。
     - ディレクトリ構造は `.roo/` の仕様に合っているか？
     - `custom_modes.json` の定義は正しいか？
     - 各 Mode の契約ファイル（`rules-*/00-contract.md`）は存在し、正しい書式か？
     - Skill の定義（`skills/*/SKILL.md`）は正しい書式か？

3. **記録 (Logging)**:
   - 監査結果（PASS/FAIL/WARN）に基づき、`skill-logging` を使用して `development_logs/session_logs.md` に結果を記録してください。
   - ログには「期待値（Roo Code 仕様への完全準拠）」と「乖離（監査で見つかった問題）」を明確に記述してください。

4. **更新**:
   - 監査の結果、修正が必要な場合は `project_state.md` の「残された課題」または「進行中のタスク」を更新してください。
