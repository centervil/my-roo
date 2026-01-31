# Skill Template: [Skill Name]

## Definition
- 本 Skill は「純粋な手続き」であり、推論や方針決定を行わない。
- 実行時に必要となる「判断」は、常に呼び出し元の Mode の責任に属する。

## Input Contract
- **Parameters**: (Skill 実行に必要な定量的・定性的データ)
- **Constraint**: 入力が不足している場合、Skill は即座にエラーを返し、判断を Mode にエスカレーションする。

## Procedure (Stateless)
1. Step 1: ...
2. Step 2: ...
3. Step 3: ...

## Output Contract
- **Result**: (手続きの実行結果)
- **Artifacts**: (生成されたファイル、データ等)

## Violation Conditions
- 手続き内で「独自の解釈」や「仕様の変更」を行った場合、Skill 実行は無効とみなされる。
