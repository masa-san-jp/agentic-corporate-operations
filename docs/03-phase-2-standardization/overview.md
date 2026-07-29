# Phase 2: Standardization

```yaml
status: draft
phase_id: phase-2-standardization
parent_documents:
  - ../02-phase-1-visibility/overview.md
```

## Purpose

Phase 1で観測した業務を、共通の分類、用語、データ、状態、権限、完了条件、例外コード、SOPへ正規化する。

## Entry Conditions

- 対象業務と発生源が可視化されている
- 原入力と正規化対象を追跡できる
- 重要業務の責任主体が特定されている

## Target State

- 同一目的の業務が同一の業務種別として扱われる
- 用語、データ型、識別子、状態が統一されている
- 役割と権限が個人名ではなくロールと条件で表現される
- 完了、失敗、例外を機械判定できる
- 正常系と例外系を含むSOPがある

## Required Deliverables

- 業務分類体系
- データ辞書
- ID・参照規則
- リスク分類
- 自律度分類
- 権限モデル
- 完了条件カタログ
- 例外コード体系
- SOP標準形式
- 正規化・移行マッピング

## Exit Criteria

- 自動化対象業務の100%が標準業務種別へ分類されている
- 必須属性の意味と型が定義されている
- 状態と例外に退出条件がある
- 権限の空白・重複・職務分離違反を検出できる
- 代表業務を標準SOPで再現できる
- Phase 3のAgentとToolが利用する入出力契約を確定している
