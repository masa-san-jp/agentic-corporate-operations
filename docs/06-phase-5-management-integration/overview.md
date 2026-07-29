# Phase 5: Management Integration

```yaml
status: draft
phase_id: phase-5-management-integration
parent_documents:
  - ../05-phase-4-control/overview.md
```

## Purpose

業務実行、予算、KPI、リスク、意思決定、会議を接続し、経営者が処理状況ではなく、目的、例外、資源配分、価値判断へ集中できる状態を作る。

## Entry Conditions

- 重要業務の状態、Evidence、リスクを横断取得できる
- 経営目標と業務成果を関連付けられる
- 高リスク例外を意思決定案件へ変換できる

## Target State

- 重要意思決定をDecision Registryで管理する
- 予算、実績、予測、施策、リスクが連動する
- 会議を情報共有から意思決定へ限定する
- 人間への通知に推奨案、選択肢、根拠、影響、期限が含まれる
- 決定後にPolicy、予算、権限、Work Objectへ自動反映する

## Required Deliverables

- Decision ObjectとDecision Registry
- Authority Matrix
- KPI・Outcome Model
- Portfolio Model
- Rolling Forecast Protocol
- Executive Exception Queue
- Meeting Preparation・Decision Capture Protocol
- Decision Review Protocol
- Executive Dashboard要件

## Exit Criteria

- 重要意思決定の100%に権限、根拠、選択肢、結果レビュー日がある
- 会議決定をWork Objectへ自動変換できる
- 予算変更の目的、効果、撤退条件を追跡できる
- 経営者への通知を判断必要案件へ限定できる
- 意思決定後の実行と結果をDecisionへ逆参照できる
