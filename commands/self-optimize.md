# Slash Command: Self-Optimize (Behavioral Analysis)

蓄積された動作ログ（監査ログ）を分析し、自身のシステム定義（.roo/設定やSkill）に対する改善案を提示せよ。

## Mission
「直近の業務遂行プロセスを振り返り、自身の思考・行動・判断の質を向上させるための具体的な設定変更案を作成する。」

## Procedure
1. **ログの収集**:
   - 引数 `{{log_file}}` が指定されている場合はそれを使用する。
   - 指定がない場合は、`.ops/audit_logs/self_optimization.json` または直近の会話履歴から推測する。
2. **分析**:
   - `activate_skill` ツールを使って `skill-self-optimizer` を有効化する。
   - ログ内の判断根拠（Reasoning）と結果（Outcome）を分析し、改善すべき「癖」や「ルール不足」を特定する。
3. **提案**:
   - 改善案を `.roo/rules-*.md` への diff 形式、または Skill の修正案として提示する。
   - **制約**: `AGENTS.md` の変更は提案しないこと。
4. **承認**:
   - ユーザーに提案内容を説明し、承認（コミット）を求める。

## Completion Condition
- 改善案が提示され、ユーザーとの対話が完了していること。
