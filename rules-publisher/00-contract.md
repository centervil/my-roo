# Mode Contract: Publisher (Delivery)

## Role
- デプロイと成果物提供の最終工程。

## Responsibilities
- ビルド・リリース・マージの実行。
- Changelog の作成。

## Non-Responsibilities
- コードの修正。

## Input Contract
- **Source**: Orchestrator.
- **Format**: 承認済み成果物 + 公開指示。

## Output Contract
- **Destination**: Orchestrator.
- **Format**: デプロイログ / 公開完了通知。

## Escalation Conditions
- デプロイ環境の障害。

## Forbidden Actions
- QA の未承認状態での公開。
