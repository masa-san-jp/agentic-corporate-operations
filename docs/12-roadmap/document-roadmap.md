# Document Roadmap

```yaml
document_id: ACO-ROADMAP-001
title: Document Roadmap
status: draft
version: 0.2.0
owner: chief-architect
reviewers:
  - human-governor
created_at: 2026-07-30
updated_at: 2026-07-30
parent_documents:
  - ACO-ARCH-DOC-001
dependent_documents:
  - ACO-ROADMAP-PHASE-000
related_schemas: []
related_adrs: []
source_issue: 9
applicable_invariants:
  - INV-001
  - INV-005
change_class: C3
```

## 1. 目的

文書を依存関係順に作成し、領域ごとの独自解釈、設計乖離、重複、手戻りを防止する。各Stageは、完了条件と検証Evidenceを満たすまで次へ進まない。

## Stage 0: Multi-Agent Repository Foundation

Stage 0は、単なるリポジトリ初期化ではない。複数AIエージェントが同一の設計状態を参照し、限定された権限で並列作業し、改善提案と正式仕様変更を分離し、独立レビューと機械検証を通じて成果物を統合するための基盤を作る。

詳細仕様:

- [`phase-0-multi-agent-repository-foundation.md`](phase-0-multi-agent-repository-foundation.md)

### Workstreams

1. Design Invariants and Change Classes
2. Document Registry and Traceability Graph
3. Agent Roles and Work Orchestration
4. RFC and Change Proposal Governance
5. Pull Request and Merge Governance
6. Validation and Semantic Gates
7. Golden Scenarios
8. Agent Provenance and Security

### 必須成果物

- `governance/invariants.yaml`
- `governance/change-classes.yaml`
- `governance/approval-matrix.yaml`
- `registry/documents.yaml`
- Agent Role Model
- Work Package、Context Bundle、Task Lease、Handoff
- RFCテンプレートとProposal Protocol
- `.github/PULL_REQUEST_TEMPLATE.md`
- `.github/CODEOWNERS`
- Validation Workflow
- Golden Scenario Framework
- Agent Run Provenance
- Tool PermissionとSecurity Model

### 完了条件

- 上位設計の不変条件が一意IDで機械可読化されている
- 全正式文書がDocument Registryに登録されている
- 文書・Schema・Protocol・ADR・Issue・Example・Testの依存関係を検査できる
- エージェントの役割、権限、禁止操作が定義されている
- Issueをbase commit固定のWork Packageへ変換できる
- 同時編集を防ぐTask Leaseと停止時のHandoffがある
- 改善提案をRFCへ分離できる
- C0〜C5の変更クラス別にレビュー・承認条件がある
- mainへの未検証変更を防ぐPR・CI統制がある
- 最低2件のGolden Scenarioが機械検証できる
- Agent Runのモデル、指示、Context、Tool、結果を追跡できる
- 外部命令混入、過剰権限、機密情報混入の統制がある

### Issues

1. Phase 0統括: #9
2. Design Invariantsと変更クラス: #10
3. Document RegistryとTraceability: #11
4. Agent Role、Work Package、Context、Handoff: #12
5. RFCと承認統治: #13
6. Pull Request Governance: #14
7. Validation Architecture: #8
8. Golden Scenario Framework: #15
9. Agent ProvenanceとSecurity: #16

### 並列作業の制限

Stage 0の必須ゲートが完了するまで、Issue #1〜#7を複数エージェントへ同時割当しない。単一エージェントによる調査・草案作成は可能だが、正式仕様への昇格はPhase 0のレビュー・Validation規則に従う。

## Stage 1: Constitution

### 作成物

- Vision
- Scope
- Principles
- Glossary
- Human-Agent Responsibility Boundary

### 完了条件

- 目的、対象、非対象、設計原則が確定
- 基本用語の曖昧性が除去
- 人間専管、AI自律、承認必須の境界が定義
- L0文書の不変条件との対応が登録されている
- Golden Scenarioで責任境界の代表例を検証できる

## Stage 2: Common Object Model

### 作成順

1. Work Object
2. State Machine
3. Evidence
4. Exception
5. Policy
6. Decision
7. Agent Definition
8. Control
9. SOP

### 成果物

各項目について以下を作る。

- 概念仕様
- YAMLテンプレート
- JSON Schema
- 正常・異常例
- 検証テスト
- Registry Entry
- 関連Golden Scenario

### 完了条件

- 全オブジェクトが一意識別、版、責任、関連付けを持つ
- 循環参照と責任の空白がない
- サンプルデータがSchema Validationを通過する
- 不変条件と上位仕様へのTraceabilityがある
- 独立レビューとIntegration Reviewが完了している

## Stage 3: Common Protocols

### 作成順

1. Intake
2. Task Curation
3. Planning
4. Authorization
5. Execution
6. Verification
7. Exception Handling
8. Human Escalation
9. Evidence Capture
10. Change Management
11. Learning

### 完了条件

- 各Protocolに開始条件、終了条件、状態遷移、タイムアウトがある
- 通信障害、入力欠損、権限不足、外部待ちの処理がある
- 人間への照会が選択可能なDecision Objectになる
- Protocol間の入出力がSchemaで検証できる
- 代表的なGolden Scenarioを通過する

## Stage 4: Phase Specifications

### 作成順

1. Phase 1 Visibility
2. Phase 2 Standardization
3. Phase 3 Automation
4. Phase 4 Control
5. Phase 5 Management Integration
6. Phase 6 Self-Improvement

### 各Phaseの成果物

- Overview
- Requirements
- Architecture
- Process
- Protocols
- Templates
- Acceptance Criteria
- Implementation Guide
- Test Plan

### 完了条件

- 開始条件と終了条件が測定可能
- 前Phase成果物への依存が明示
- 移行、並行稼働、ロールバックが定義
- Document RegistryとGolden Scenarioが更新されている

## Stage 5: Functional Domains

### 初期対象順

1. 財務・会計・資金
2. IT・データ・AI・情報セキュリティ
3. 人事・労務
4. 法務・契約・コンプライアンス
5. リスク・内部統制・監査
6. 調達・購買・資産
7. ナレッジ・文書
8. 総務・BCP
9. 経営ガバナンス・戦略
10. 経営秘書・コミュニケーション

初期対象順は、共通基盤の検証可能性、データ取得性、統制重要性を基準とする。

各領域は、上位仕様を再定義せず、共通モデルとProtocolへの適用差分だけを記載する。

## Stage 6: Implementation Reference

### 作成物

- 技術参照アーキテクチャ
- API・イベント統合パターン
- 認証・認可
- 秘密管理
- 監査ログ
- Observability
- Model Gateway
- Evaluation Framework
- Deployment and Rollback
- Migration Playbook
- Agent Security and Tool Permission
- Release and Compatibility Management

## Stage 7: Pilot and Feedback

### パイロット候補

- 請求書・証憑取得と会計照合
- 入退社イベントからのアカウント・端末処理
- 契約期限・義務管理
- 会議決定からWork Object生成
- 反復例外から改善RFC生成

### 完了条件

- 実案件でEnd-to-End実行できる
- 重大な未検出誤りがない
- 人間介入理由を分類できる
- Agent RunとEvidenceから実行を再構成できる
- 実装結果をRFCとして上位仕様へフィードバックできる

## 2. Issue作成原則

Issueは1つの検証可能な成果物または同一概念の成果物集合に限定する。

必須項目:

- 成果物パス
- 解決する問題
- 目的
- 対象と非対象
- 親文書
- 依存Issue
- 変更クラス
- 適用不変条件
- 担当Agent Role
- Reviewer Role
- 必須セクション
- 完了条件
- 検証方法
- base commitまたはContext Bundle生成条件

Issueは直接実行せず、Phase 0完了後はTask CuratorがWork Packageへ変換する。

## 3. 現在の作業順

### Phase 0

1. #9 Phase 0統括
2. #10 Design Invariantsと変更クラス
3. #11 Document RegistryとTraceability
4. #12 Agent Role、Work Package、Context Bundle、Handoff
5. #13 RFCと承認統治
6. #14 Pull Request Governance
7. #8 Validation Architecture
8. #15 Golden Scenario Framework
9. #16 Agent ProvenanceとSecurity

### Phase 0ゲート後

1. #1 Human-Agent Responsibility Boundary
2. #2 Work Object概念仕様
3. #3 Work Object JSON Schema
4. #4 Work Object状態遷移
5. #5 Evidence Model
6. #6 Exception Model
7. #7 Policy Model
