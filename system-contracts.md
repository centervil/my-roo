# System Contracts: 運用ガイド

## 概要
本リポジトリの `/modes`, `/skills`, `/policies` は、システムの「静的契約（Static Contracts）」を定義する。

## 運用ルール
1. **Mode は契約を遵守する**: 各 Mode は自身の `.md` に定義された `Input/Output Contract` を厳守し、`Forbidden Actions` を行わない。
2. **Skill は手順に徹する**: Skill は判断を持たない。判断が必要な入力が与えられた場合、Skill は停止し Mode に判断を委ねる。
3. **品質は定量評価する**: `policies/metrics.yaml` の閾値を満たさない成果物は、`quality.yaml` の定義に従い自動的に Rejection（差し戻し）の対象となる。

## 拡張方法
新しい Mode や Skill を追加する場合、必ず本リポジトリのテンプレートに従い、入出力契約を定義すること。
