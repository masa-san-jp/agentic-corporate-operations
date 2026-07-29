# Phase 1: Visibility

```yaml
status: draft
phase_id: phase-1-visibility
parent_documents:
  - ../00-overview/vision.md
  - ../01-architecture/document-architecture.md
```

## Purpose

業務、システム、データ、主体、イベント、期限、停止を発見し、Work Objectとして観測可能にする。

## Entry Conditions

- 経営対象となる法人・部門の範囲が定義されている
- データ取得に必要な権限と利用目的が承認されている
- 原データを変更せず保存できる領域がある

## Target State

- 業務発生源が台帳化されている
- 実行対象業務がWork Objectとして追跡できる
- システム、データ、権限、担当、依存関係が関連付けられている
- 次の行動、期限、完了条件、停止理由の欠損を検出できる
- 現行業務を廃止・統合・標準化・自動化へ分類できる

## Required Deliverables

- 業務発生源台帳
- 業務イベントモデル
- 業務台帳
- システム台帳
- データ台帳
- 主体・権限台帳
- Work Object初期仕様
- 可視化対象範囲と捕捉率
- 現行業務の観測ダッシュボード

## Exit Criteria

- 対象業務発生源の95%以上を捕捉している
- 重要業務の100%に目的、責任主体、期限、状態がある
- 未捕捉、所有者不明、次行動不明、期限超過を検出できる
- 原入力と正規化データを区別して保存している
- Phase 2で正規化すべき分類・用語・例外候補を抽出している

## Prohibited Shortcuts

- 既存の担当者一覧を業務台帳の代用にする
- 会議資料やタスクリストだけから全業務を推定する
- 原データを上書きして正規化する
- 観測不能な領域を問題なしとして扱う
