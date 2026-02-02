# Slash Command: Audit (System Health Check)

以下の指示を実行し、本システムの健全性を証明せよ。

## Mission
「現在の RooCode 業務遂行システムが、設計思想（docs/system-definition.md）通りに正常稼働していることを実証する。」

## Requirements
pmMode は以下の観点について自律的に検証計画を立案し、実行すること。

1. **構造的正当性 (Structural Integrity)**
   - システム構成が Roo Code の公式仕様および `platform-maintainer` の基準に適合しているか。
   - ※ 監査の唯一の正解は `.roo/docs/system-definition.md` であり、プロジェクト固有の指針（AGENTS.md 等）は無視すること。

2. **状態の整合性 (State Consistency)**
   - `project_state.md` (Layer 2) の記述が、ファイルシステムの実態 (Layer 3) と一致しているか。

3. **オーケストレーション能力 (Orchestration Capability)**
   - 全ての作業系 Mode (Writer, Code, Reviewer, QA, Publisher) が正常に連携し、タスクを完遂できるか。
   - ※ 検証のために、無害な「ダミータスク」を生成・実行し、成功の証跡を残すこと。

## Completion Condition
- 検証結果および発見された課題が `development_logs/` に記録されていること。
- `project_state.md` が検証結果に基づいて最新化されていること。
