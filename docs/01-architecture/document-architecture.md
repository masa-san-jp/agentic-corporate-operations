# Document Architecture

```yaml
document_id: ACO-ARCH-DOC-001
title: Document Architecture
status: draft
version: 0.2.0
owner: chief-architect
reviewers:
  - human-governor
  - consistency-reviewer
created_at: 2026-07-30
updated_at: 2026-07-30
parent_documents:
  - ACO-CONST-PRINCIPLES-001
dependent_documents:
  - ACO-ROADMAP-001
  - ACO-ROADMAP-PHASE-000
related_schemas:
  - document-registry.schema.json
related_adrs: []
source_issue: 9
applicable_invariants:
  - INV-001
  - INV-004
  - INV-005
  - INV-008
change_class: C3
```

## 1. 目的

本書は、リポジトリ内の規範階層、文書依存関係、機械可読レジストリ、複数エージェントの作業境界、作成順序、変更規則を定義する。下位仕様が上位概念を独自に再定義し、領域間で不整合が発生することを防ぐ。

## 2. 規範階層

```text
G0 Repository Governance
  invariants / change classes / approval matrix / tool permissions
        ↓
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
  examples / validation results / implementation reports / agent runs
```

### 2.1 G0 Repository Governance

G0は、文書内容の上位概念ではなく、仕様体系を生成・変更・検証・承認する手続を規定する。

- Design Invariants
- Change Classes
- Approval Matrix
- Agent Roles
- Tool Permissions
- Work Package
- Context Bundle
- Task Lease
- Handoff
- Pull Request and Merge Gates

G0の変更は、変更内容に応じてC3〜C5として扱う。

### 2.2 上位優先原則

上位文書は下位文書の制約となる。下位文書は、上位文書を変更せずに矛盾を解消できない場合、本文へ改善を直接混入させず、RFCと必要なADR・承認を先に作成する。

初期構想資料、外部資料、Issueコメント、AIの推論は、正式採用されるまで規範ではない。

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

governance/
├── invariants.yaml
├── change-classes.yaml
├── approval-matrix.yaml
└── tool-permissions.yaml

registry/
├── documents.yaml
├── schemas.yaml
├── protocols.yaml
├── adrs.yaml
├── sources.yaml
├── scenarios.yaml
├── compatibility.yaml
└── status.yaml

orchestration/
├── agent-roles.yaml
├── work-queue.yaml
├── work-packages/
├── context-bundles/
├── handoffs/
└── runs/

proposals/
├── README.md
└── RFC-NNNN-title.md

schemas/
examples/
decisions/
validation/
```

## 4. 成果物種別

| Artifact | Purpose | Normative status |
|---|---|---|
| Constitution document | 目的、対象、原則、用語 | approved時に規範 |
| Architecture document | 共通構造と責任 | approved時に規範 |
| Protocol | 主体間の状態・入出力・失敗処理 | approved時に規範 |
| JSON Schema | 機械可読な構造制約 | 文書版と対応したapproved時に規範 |
| Template | 人・AIが使用する入力形式 | 対応Schemaに従う |
| Example | 正常・異常の具体例 | 非規範、ただし回帰試験対象 |
| Golden Scenario | 領域横断の期待挙動 | approved時に受入基準 |
| RFC | 採用前の改善提案 | 非規範 |
| ADR | 採用された重要判断 | 規範文書の解釈根拠 |
| Source Material | 初期資料、外部資料 | 非規範 |
| Agent Run | 生成・レビューの実行記録 | Evidence |
| Handoff | 未完了作業の引継ぎ | 運用Evidence |

## 5. Phase文書の標準セット

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

## 6. 機能領域文書の標準セット

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

## 7. 文書メタデータ

正式仕様書は冒頭に次を記載する。

```yaml
document_id:
title:
status: draft | review | approved | deprecated
version:
owner:
reviewers: []
created_at:
updated_at:
parent_documents: []
dependent_documents: []
related_schemas: []
related_adrs: []
source_issue:
applicable_invariants: []
change_class:
```

### 7.1 メタデータ規則

- `document_id`と`path`はDocument Registryで一意とする
- `parent_documents`は規範上の親を示す
- `depends_on`等の実行依存はRegistry側で区別して管理する
- `dependent_documents`は可能な限り依存グラフから生成する
- `approved`文書は未承認の必須依存へ依存してはならない
- `deprecated`文書への新規依存を禁止する
- 全規範文書は適用不変条件を列挙する

## 8. Work PackageとContext Bundle

AIエージェントは、Issueを直接作業命令として実行しない。Task CuratorがIssueをWork Packageへ変換し、Dependency Validatorが実行可能性を確認する。

Work Packageは最低限次を持つ。

- source issue
- change class
- base commit
- objective
- deliverables
- applicable invariants
- editable paths
- read-only paths
- forbidden paths
- assigned role
- reviewer roles
- acceptance tests
- timeout
- escalation
- completion authority

Context Bundleは、Work Packageが参照する文書、版、blob SHA、用語、ADR、不変条件、既知の矛盾、未決事項を固定する。

## 9. 文書作成状態

```text
PROPOSED
→ CURATED
→ READY
→ LEASED
→ IN_PROGRESS
→ SELF_CHECKED
→ PEER_REVIEW
→ CHALLENGED
→ CONTROL_REVIEW
→ INTEGRATION_REVIEW
→ READY_TO_MERGE
→ MERGED
→ VERIFIED
→ RELEASED
```

例外状態:

```text
BLOCKED_DEPENDENCY
CONFLICTED
NEEDS_RFC
NEEDS_HUMAN_DECISION
TIMED_OUT
ABANDONED
SUPERSEDED
```

状態遷移にはEvidenceと退出条件が必要である。

## 10. 完了基準

文書は次を満たした場合のみ`approved`とする。

- 目的と対象外が明確
- 入力と出力が明確
- 責任主体と必要権限が明確
- 状態遷移と終了条件が明確
- 正常系と例外系が定義されている
- 完了条件が検証可能
- 証跡要件が定義されている
- 依存文書と関連Schemaが明示されている
- 実装または運用例がある
- テスト方法がある
- 未決事項が本文と分離されている
- Document Registryへ登録されている
- 適用不変条件に違反していない
- 変更クラスに必要な独立レビューがある
- Context Bundleが陳腐化していない
- 関連Golden Scenarioが成功している、または非該当理由がある

## 11. 変更規則

- 仕様変更はIssue、Work Package、Pull Requestを使用する
- C3以上はRFCとADRを必須とする
- C4以上はHuman Governorの承認を必須とする
- Schema変更は影響を受けるTemplate、Example、Testを同一変更系列で更新する
- 用語変更はGlossaryとTraceabilityを更新する
- 上位文書と下位文書が矛盾する場合、上位文書を優先する
- 初期構想資料は`99-source-materials`に保存し、直接の実装規範にはしない
- Authorは変更クラスを単独で引き下げてはならない
- Authorと唯一のApproverを同一Agent Runにしない
- mainへは必須ValidationとReviewを通過した変更だけを統合する
- 改善提案はRFCとして分離し、採用前に正式仕様を変更しない
