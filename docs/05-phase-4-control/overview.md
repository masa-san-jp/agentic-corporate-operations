# Phase 4: Control

```yaml
status: draft
phase_id: phase-4-control
parent_documents:
  - ../04-phase-3-automation/overview.md
```

## Purpose

自動実行される業務に、Policy判定、権限統制、独立検証、監査証跡、継続的統制監視、インシデント対応を組み込む。

## Entry Conditions

- 自動化対象のAgent、Tool、データフローが特定されている
- 対象業務のリスクと必要統制が定義されている
- Evidenceを改ざん防止領域へ保存できる

## Target State

- 重要なPolicy違反を実行前に防止する
- 実行後の逸脱を継続的に検出する
- 起案、承認、実行、検証、監査を分離する
- 高リスク処理を全件追跡・再構成できる
- 統制失敗をExceptionおよび改善Issueへ変換する

## Required Deliverables

- Policy Engine仕様
- Authority・Separation of Duties仕様
- Evidence Engine仕様
- Control Library
- Continuous Control Monitoring仕様
- Audit Agent仕様
- Security・Privacy統制
- Incident Response Protocol
- 緊急権限と事後レビュー

## Exit Criteria

- 高リスク操作の100%に権限確認と独立検証がある
- 重要統制の実施証拠を自動取得できる
- 実行Agentが監査記録を変更できない
- Policy、モデル、プロンプト、Toolの変更を追跡できる
- 統制異常が期限と収束条件を持つExceptionになる
- 監査人がEvidenceから処理を再構成できる
