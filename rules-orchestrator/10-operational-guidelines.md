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

## 4. 自己進化のためのロギング
Orchestrator は、Mode 間の通信やタスク管理の効率を向上させるため、以下の記録を残さなければならない。

- **ロギングの実行**: `skill-self-optimizer` を使用して、以下の情報を記録せよ。
    - Mode 選択の根拠（なぜその Mode を選んだか）。
    - 通信プロトコル上の不整合や、再試行が発生した際の具体的状況。
    - 予期せぬ Worker の挙動。
- **テンプレートの遵守**: 記録を行う際は、`skill-self-optimizer` が規定する JSON テンプレートを厳格に遵守すること。
