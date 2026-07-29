# Phase 0: Multi-Agent Repository Foundation

```yaml
document_id: ACO-ROADMAP-PHASE-000
Title: Phase 0 Multi-Agent Repository Foundation
status: draft
version: 0.1.0
owner: human-governor
reviewers:
  - chief-architect
  - control-reviewer
created_at: 2026-07-30
updated_at: 2026-07-30
parent_documents:
  - ACO-ARCH-DOC-001
  - ACO-ROADMAP-001
dependent_documents:
  - ACO-ARCH-BOUNDARY-001
related_schemas: []
related_adrs: []
source_issue: 9
applicable_invariants:
  - INV-001
  - INV-002
  - INV-003
  - INV-004
change_class: C3
```

## 1. 目的

Phase 0は、複数のAIエージェントが、初期設計から無自覚に乖離せず、同一の設計状態を参照し、限定された権限で並列作業し、必要な改善を正式な提案経路へ分離しながら、仕様体系を継続的に完成させるためのリポジトリ基盤を構築する。

Phase 0の成果は、文書そのものではない。次を強制できる生産システムである。

- 上位設計が下位仕様の制約として機能する
- 各作業が固定されたbase commitを参照する
- エージェントごとの役割、権限、編集範囲が限定される
- 同じ対象を複数エージェントが無秩序に変更しない
- 改善提案と正式仕様変更が分離される
- 自己レビューだけで正式仕様へ昇格できない
- 依存関係、用語、Schema、Example、Testの不整合を機械検出する
- エージェント停止時に別エージェントが作業を引き継げる
- 仕様全体を領域横断シナリオで検証できる

## 2. Phase 0以前の状態

現在のリポジトリには次が存在する。

- Vision、Scope、Principles、Glossary
- 文書階層と配置規則
- AIエージェントの必読順序
- 文書のDefinition of Done
- IssueとADRによる変更管理方針
- 共通モデルとPhaseの作成順序

ただし、これらは自然言語の規則であり、複数エージェントの並列作業を機械的に統制するものではない。

## 3. Phase 0終了状態

Phase 0終了時、リポジトリは次の状態でなければならない。

```text
Issue
  ↓ Task Curator
Work Package
  ↓ Dependency Validator
Context Bundle
  ↓ Task Lease
Author Agent
  ↓ Self Validation
Independent Review
  ↓ Challenge / Control / Integration
Pull Request Gate
  ↓ Merge
Registry Update
  ↓
Released Specification State
```

改善が必要な場合は次の分岐を通る。

```text
Detected Design Defect
  ↓
RFC Draft
  ↓
Challenge and Impact Analysis
  ↓
Approval by Change Class
  ↓
ADR and Migration Plan
  ↓
Normative Specification Change
```

## 4. 対象

### 4.1 対象

- 設計不変条件
- 文書・Schema・Protocol・ADR・Issue・Example・Testのレジストリ
- エージェント役割と職務分離
- Work Package
- Context Bundle
- Task Lease
- Handoff Package
- Agent Run Provenance
- RFCと変更クラス
- 承認マトリクス
- PRとマージ統制
- CIと意味的検証
- Golden Scenario
- エージェントのツール権限と安全性
- 完成度と滞留の測定

### 4.2 非対象

- Work Object等の業務共通モデルの正式仕様
- 財務、人事、法務等の領域固有仕様
- 本番用エージェントランタイムの実装
- 事業会社内の実データ接続
- 個別SaaSやモデルの標準採用

これらはPhase 0完了後のStage 1以降で扱う。

## 5. ワークストリーム

## WS-01 Design Invariants and Change Classes

### 目的

設計原則を、変更不能な不変条件、正式手続で変更可能な原則、推奨、既定値へ分類する。

### 成果物

- `docs/01-architecture/design-invariants.md`
- `governance/invariants.yaml`
- `governance/change-classes.yaml`
- `schemas/invariant.schema.json`

### 終了条件

- 全不変条件に一意IDがある
- 違反例、例外可否、変更権限がある
- C0〜C5の変更クラスが定義されている
- L0/L1変更はHuman Governorなしに承認できない

### Issue

- #10

## WS-02 Registry and Traceability

### 目的

全成果物の依存関係、版、状態、根拠を機械可読なグラフへ変換する。

### 成果物

- `registry/documents.yaml`
- `registry/schemas.yaml`
- `registry/protocols.yaml`
- `registry/adrs.yaml`
- `registry/scenarios.yaml`
- `schemas/document-registry.schema.json`
- Traceability Validator

### 終了条件

- 孤立、循環、存在しない参照を検出できる
- approved成果物の必須依存がapprovedである
- 上位文書変更時に影響先候補を列挙できる
- Issue、PR、成果物、Schema、Testを追跡できる

### Issue

- #11

## WS-03 Agent Roles and Work Orchestration

### 目的

複数エージェントを同一能力の無差別な執筆者として扱わず、役割、権限、禁止操作、引継ぎを分離する。

### 必須ロール

| Role | Primary responsibility | Prohibited action |
|---|---|---|
| human-governor | L0/L1、C4/C5、価値判断の承認 | 実務詳細を無制限に都度決定する |
| chief-architect | 全体整合性と上位設計の維持 | 単独で自分のC4変更を承認する |
| task-curator | IssueをWork Packageへ変換する | 概念仕様を独自に確定する |
| domain-author | 限定された成果物を作成する | 上位概念を無断変更する |
| schema-engineer | Schema、Example、Testを作成する | 概念意味をSchema都合で変更する |
| consistency-reviewer | 用語、依存、重複を検査する | 好みだけで設計を変更する |
| challenger | 前提と失敗モードを反証する | 代替案なしに否定だけを行う |
| control-reviewer | 権限、統制、Evidenceを検査する | 実行者と同一主体で最終承認する |
| integration-agent | 領域横断の統合試験を行う | 未検証変更をmainへ統合する |
| release-manager | 版、移行、Releaseを管理する | 破壊的変更をPatchとして扱う |

### 成果物

- Agent Role Model
- Work Package Schema
- Context Bundle Schema
- Task Leasing Protocol
- Handoff Protocol
- Agent Run Schema

### Issue

- #12
- #16

## WS-04 Change Proposal Governance

### 目的

改善提案を歓迎しつつ、提案を正式仕様へ直接混入させない。

### 変更クラス

| Class | Meaning | Required path |
|---|---|---|
| C0 | 誤字、リンク、意味を変えない修正 | 通常PR |
| C1 | 非規範的な明確化 | Author + Reviewer |
| C2 | 下位仕様の非破壊追加 | Reviewer + Integration |
| C3 | 共通モデル、Protocol、Schemaの変更 | RFC + ADR + Challenge |
| C4 | L0/L1、不変条件、責任境界の変更 | RFC + Human Governor |
| C5 | 法的、倫理的、重大リスクの変更 | C4 + 指定専門レビュー |

### RFC状態

```text
DRAFT
→ CHALLENGED
→ REVISED
→ EVALUATED
→ ACCEPTED | REJECTED | DEFERRED
→ IMPLEMENTED
→ VERIFIED
```

### Issue

- #13

## WS-05 Pull Request and Merge Governance

### 目的

mainへ入る変更を、変更クラスに応じたレビューとCIで統制する。

### 必須統制

- mainへの直接push禁止
- Pull Request必須
- 必須CI成功
- 必須レビュー
- stale approvalの取消
- 未解決レビュー会話の解消
- force push禁止
- CODEOWNERS
- 緊急変更の期限付き例外と事後レビュー

### Issue

- #14

## WS-06 Validation and Semantic Gates

### 検証層

1. Syntax: Markdown、YAML、JSON、JSON Schema、Mermaid
2. Structure: 配置、命名、文書ID、必須メタデータ
3. Traceability: 親文書、依存、ADR、Schema、Test、Issue
4. Semantic: 用語重複、状態矛盾、権限不整合、不変条件違反
5. Scenario: 複数文書を組み合わせたEnd-to-End回帰試験

### 必須原則

AIレビューは補助検出器として使えるが、唯一の必須ゲートにはしない。

### Issue

- #8

## WS-07 Golden Scenarios

### 目的

個別文書の局所的な正しさではなく、仕様体系全体の実行可能性を検査する。

### 初期シナリオ

- 請求書から支払、仕訳、Evidence保存
- 入社決定からID、端末、研修、権限付与
- API障害から再試行、代替、人間エスカレーション

### Issue

- #15

## WS-08 Provenance and Security

### 目的

成果物がどのモデル、指示、設計状態、権限で生成されたかを再現可能にし、外部入力による命令混入と過剰権限を防ぐ。

### 必須統制

- agent_run_id
- agent_role
- modelとversion
- instruction version
- base commit
- Context Bundle
- 使用ツール
- 変更ファイル
- レビュー結果
- 不確実性と既知の限界
- 読取・書込・外部送信の最小権限
- secretsと機密情報の検査
- `99-source-materials`を非規範資料として区別

### Issue

- #16

## 6. 標準作業プロセス

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

各状態は、必要なEvidenceと退出条件を持たなければならない。

## 7. Phase 0ゲート

Issue #1〜#7を複数エージェントへ並列割当する前に、最低限次を満たす。

- [ ] `governance/invariants.yaml`が存在し、主要不変条件が登録されている
- [ ] `governance/change-classes.yaml`が存在する
- [ ] 正式文書がDocument Registryへ登録されている
- [ ] 依存関係の循環と欠損を検査できる
- [ ] Agent Role Modelが定義されている
- [ ] Work Packageにbase commit、編集可能範囲、完了条件がある
- [ ] Context Bundleを生成できる
- [ ] Task LeaseとHandoffが定義されている
- [ ] RFCテンプレートと採否プロセスがある
- [ ] 変更クラス別のApproval Matrixがある
- [ ] PRテンプレートとCODEOWNERSがある
- [ ] main保護設定の手順と検証方法がある
- [ ] CIがMarkdown、リンク、メタデータ、Schema、Registryを検査する
- [ ] 最低2件のGolden Scenarioがある
- [ ] Agent Run Provenanceを記録できる
- [ ] 過剰権限、外部命令混入、機密情報混入の統制がある

## 8. 完了基準

Phase 0は、次の試験をすべて通過した場合のみ完了する。

### Test P0-01 Parallel Authoring

異なる2つのWork Packageを2エージェントへ割り当て、同一base commitから競合なく成果物を作成できる。

### Test P0-02 Conflicting Edit

同一概念または同一パスを変更する2つの作業を検出し、後続作業をCONFLICTEDまたはBLOCKED_DEPENDENCYへ遷移できる。

### Test P0-03 Design Drift

不変条件に違反する下位仕様変更を、PRマージ前に検出できる。

### Test P0-04 Improvement Proposal

上位設計の欠陥を発見したエージェントが、本文へ直接混入させずRFCを生成し、反証と承認へ送れる。

### Test P0-05 Agent Failure and Handoff

作業途中でエージェントが停止しても、別エージェントがHandoff Packageから再調査を最小化して再開できる。

### Test P0-06 Stale Context

作業中に上位仕様が変更された場合、古いContext Bundleを使用するPRを停止または再同期できる。

### Test P0-07 End-to-End Validation

最低2つのGolden Scenarioが、関連文書とSchemaの組合せを検査し、正常例は成功、意図的異常例は失敗する。

## 9. Phase 0完了後の作業順

```text
Phase 0 Foundation
→ Stage 1 Constitution Completion
→ Stage 2 Common Object Model
→ Stage 3 Common Protocols
→ Stage 4 Phase Specifications
→ Stage 5 Functional Domains
→ Stage 6 Implementation Reference
→ Stage 7 Pilot and Feedback
```

Phase 0完了後も、Phase 0の統制基盤は全Stageへ継続適用する。