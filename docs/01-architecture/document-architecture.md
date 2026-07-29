# Document Architecture

## 1. 目的

本書は、リポジトリ内の文書階層、依存関係、作成順序、変更規則を定義する。下位仕様が上位概念を独自に再定義し、領域間で不整合が発生することを防ぐ。

## 2. 文書階層

```text
L0 Constitution
  vision / scope / principles / glossary
        ↓
L1 Reference Architecture
  operating model / responsibility boundary / common object model
        ↓
L2 Common Schemas and Protocols
  Work Object / Policy / Evidence / Exception / Decision / Agent
        ↓
L3 Phase Specifications
  visibility / standardization / automation / control / management / learning
        ↓
L4 Functional Domain Specifications
  finance / HR / legal / risk / procurement / IT / knowledge / BCP / executive support
        ↓
L5 Implementation Specifications
  integrations / deployment / security / observability / tests / migration
        ↓
L6 Examples and Operational Records
  examples / ADR / validation results / implementation reports
```

上位文書は下位文書の制約となる。下位文書は、上位文書を変更せずに矛盾を解消できない場合、ADRと上位文書の変更PRを先に作成する。

## 3. 標準ディレクトリ

```text
docs/
├── 00-overview/
├── 01-architecture/
├── 02-phase-1-visibility/
├── 03-phase-2-standardization/
├── 04-phase-3-automation/
├── 05-phase-4-control/
├── 06-phase-5-management-integration/
├── 07-phase-6-self-improvement/
├── 08-functional-domains/
├── 09-protocols/
├── 10-templates/
├── 11-implementation/
├── 12-roadmap/
└── 99-source-materials/
schemas/
examples/
decisions/
validation/
```

## 4. Phase文書の標準セット

各Phaseは原則として次の文書を持つ。

| ファイル | 内容 |
|---|---|
| `overview.md` | 目的、開始条件、終了状態、他Phaseとの関係 |
| `requirements.md` | 機能・非機能・統制要求 |
| `architecture.md` | コンポーネント、責任、データフロー |
| `process.md` | 状態遷移と標準プロセス |
| `protocols.md` | 主体間の入出力と失敗時動作 |
| `templates.md` | 実務で使用する入力・出力テンプレート |
| `acceptance-criteria.md` | 機械判定可能な完了条件 |
| `implementation-guide.md` | 導入手順、移行、ロールバック |
| `test-plan.md` | 正常、異常、回帰、統制テスト |

文書が不要な場合は削除せず、`Not applicable`の理由を`overview.md`に記録する。

## 5. 機能領域文書の標準セット

```text
purpose.md
scope.md
processes.md
data-model.md
agent-model.md
policies.md
controls.md
exceptions.md
kpis.md
implementation.md
tests.md
```

## 6. 文書メタデータ

正式仕様書は冒頭に次を記載する。

```yaml
document_id:
title:
status: draft | review | approved | deprecated
version:
owner:
reviewers:
created_at:
updated_at:
parent_documents:
dependent_documents:
related_schemas:
related_adrs:
```

## 7. 完了基準

文書は次を満たした場合のみ`approved`とする。

- 目的と対象外が明確
- 入力と出力が明確
- 責任主体と必要権限が明確
- 状態遷移と終了条件が明確
- 正常系と例外系が定義されている
- 完了条件が検証可能
- 証跡要件が定義されている
- 依存文書と関連スキーマが明示されている
- 実装または運用例がある
- テスト方法がある
- 未決事項が本文と分離されている

## 8. 変更規則

- 仕様変更はIssueとPull Requestを使用する。
- 破壊的変更はADRを必須とする。
- スキーマ変更は影響を受ける全テンプレートと例を同時更新する。
- 用語変更は`glossary.md`を先に更新する。
- 上位文書と下位文書が矛盾する場合、上位文書を優先する。
- 初期構想資料は`99-source-materials`に保存し、正式仕様の根拠として引用するが、直接の実装規範にはしない。
