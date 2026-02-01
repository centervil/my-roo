# Project State: スキャフォールド構築フェーズ

## 現在の目標
- Roocode 上で pmMode が各専門 Mode/Skill を指揮して動作する最小構成（MVP）の完成。

## 完了したタスク
- [x] ディレクトリ構造の決定（.roo/ 準拠）
- [x] custom_modes.json による Mode 定義
- [x] 各 Mode (pm, code, writer, reviewer, qa, publisher, platform-maintainer) の初期契約定義
- [x] Skill テンプレートと初期 Skill (research, design, review, test) の作成
- [x] 統合 Reference (docs/system-definition.md) の作成

## 進行中のタスク
- [ ] 動作ログ記録（Logging Skill）の実装
- [ ] コンテキスト管理（Layer 2: project_state）の運用開始

## 残された課題（後で詰める箇所）
- [ ] 各 Mode 間の詳細な Rejection 基準の自動判定（現在は PM の主観に依存）
- [ ] quality.yaml / metrics.yaml の具体的な閾値設定と自動計測の繋ぎ込み
- [ ] Publisher の具体的なデプロイ・通知先設定

## 既知のバグ・不具合
- (なし)
