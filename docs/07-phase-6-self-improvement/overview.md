# Phase 6: Self-Improvement

```yaml
status: draft
phase_id: phase-6-self-improvement
parent_documents:
  - ../06-phase-5-management-integration/overview.md
```

## Purpose

実行結果、品質、費用、例外、監査指摘から、SOP、Policy候補、Agent構成、Tool、評価器、業務そのものを継続的に改善する。

## Entry Conditions

- 実行ログ、Evidence、Exception、品質、費用を継続収集できる
- 変更対象を版管理し、Sandboxで試験できる
- 本番変更に承認、段階展開、ロールバックがある

## Target State

- 反復Exceptionを原因別にクラスタリングする
- 改善候補を自動生成し、効果と新規リスクを評価する
- 過去案件を用いて回帰試験する
- 改善を段階展開し、悪化時に自動撤回する
- 不要な業務、承認、報告、会議を廃止候補として提示する

## Required Deliverables

- Learning Event Model
- Root Cause Classification
- Improvement Proposal Model
- SOP・Policy・Prompt・Model変更プロトコル
- Evaluation Dataset管理
- Regression Framework
- Experiment・Canary・Rollback仕様
- Automation Portfolio Review
- Capability Registry

## Exit Criteria

- 反復例外を自動検出し改善Issueへ変換できる
- 改善前後の品質、費用、速度、統制を比較できる
- 重要変更の100%に回帰試験とロールバックがある
- 効果がない、またはリスクが増加した変更を撤回できる
- 人間が作業指示ではなく改善方針と許容リスクを管理できる
- 自動化率の上昇だけでなく不要業務の減少を測定できる
