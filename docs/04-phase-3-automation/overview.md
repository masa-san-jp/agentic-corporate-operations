# Phase 3: Automation

```yaml
status: draft
phase_id: phase-3-automation
parent_documents:
  - ../03-phase-2-standardization/overview.md
```

## Purpose

標準化された業務を、権限とリスク上限の範囲内でAIエージェントが実行・検証・完了できる状態へ移行する。

## Entry Conditions

- 対象業務に標準SOP、入出力、完了条件がある
- リスク、自律度、必要承認が判定できる
- Toolの認証、権限、冪等性を確認できる
- Dry Runと本番を分離できる

## Target State

- 低リスク定型業務はA4で完了する
- 中高リスク業務は承認以外を自動化する
- Planner、Executor、Validatorの責任が分離される
- 全操作が冪等キーとEvidenceを持つ
- 失敗時に再試行、代替、補償、エスカレーションが機能する

## Required Deliverables

- Agent Definition
- Tool Interface
- Orchestration Protocol
- Planning Protocol
- Authorization Protocol
- Execution Protocol
- Verification Protocol
- Retry・Recovery設計
- Dry Run・Sandbox設計
- 自動化候補選定基準

## Exit Criteria

- 対象業務のEnd-to-End実行が再現可能
- 同一入力の再実行で二重処理が発生しない
- 完了条件を独立Validatorが検証する
- 人間介入理由を構造化して記録できる
- 本番操作に権限、証跡、停止、ロールバック手段がある
- 自動化前後の品質、時間、費用を比較できる
