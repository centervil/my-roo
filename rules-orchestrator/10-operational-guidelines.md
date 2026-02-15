# Operational Guidelines: Orchestrator

## 1. Protocol Enforcement & Validation
Worker Mode にタスクを委譲する際は、**必ず以下の指示を含め、プロトコル遵守を強制すること**。
> 「成果物および実行ログは、`.roo/skills/skill-orchestration/SKILL.md` を参照し、そこに定義された `ResultObject` 形式（YAML）で返却すること。出力を成形する際は、同スキルのスキーマ定義を厳格に遵守せよ。」

Worker Mode からの `ResultObject` を受け取った際、または自身が `DispatchObject` を出力する際、以下のコマンドを使用してバリデーションを行うことが強く推奨される。

```bash
# 結果の検証
python3 .roo/skills/skill-orchestration/scripts/validate_interaction.py result "<YAML_CONTENT>"
```

もし `valid: false` が返された場合、その Worker Mode に対して修正を求めるか、PM に `ERROR` ステータスで報告せよ。

## 2. Retry Strategy
- `status: "NG"` または `status: "ERROR"` かつ `err.retryable: true` の場合：
  - `DispatchObject.retry.limit` を確認する。
  - 現在の試行回数を内部的にカウントし、上限以下であれば同じゴールで再試行する。
  - 再試行の際は、前回の失敗原因（`err.msg`）を `ctx` に含めること。
- `status: "BLOCK"` の場合：
  - 即座に PM へエスカレーションし、停止理由を報告する。

## 3. Handling Malformed Input
自身への入力（PM からの Dispatch）がパースできない場合、あるいは必須フィールドが欠けている場合：
1. 可能であれば PM にその旨を伝える。
2. システムの不整合を避けるため、勝手な推測で実行を開始しない。
