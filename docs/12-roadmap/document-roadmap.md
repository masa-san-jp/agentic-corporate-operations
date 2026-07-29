# Document Roadmap

## 1. 目的

文書を依存関係順に作成し、領域ごとの独自解釈や手戻りを防止する。各ステージは、完了条件を満たすまで次へ進まない。

## Stage 0: Repository Foundation

### 作成物
- `README.md`
- `CONTRIBUTING.md`
- `AGENTS.md`
- `CLAUDE.md`
- Issueテンプレート
- 文書体系
- 文書ロードマップ

### 完了条件
- 文書の配置規則と完了基準が定義されている
- AIエージェントが作業開始前に読む文書が明示されている
- 仕様追加をIssue単位で管理できる

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

### 完了条件
- 全オブジェクトが一意識別、版、責任、関連付けを持つ
- 循環参照と責任の空白がない
- サンプルデータがスキーマ検証を通過する

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
- 各プロトコルに開始条件、終了条件、状態遷移、タイムアウトがある
- 通信障害、入力欠損、権限不足、外部待ちの処理がある
- 人間への照会が選択可能なDecision Objectになる

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

## Stage 7: Pilot and Feedback

### パイロット候補
- 請求書・証憑取得と会計照合
- 入退社イベントからのアカウント・端末処理
- 契約期限・義務管理
- 会議決定からWork Object生成
- 反復例外から改善Issue生成

### 完了条件
- 実案件でEnd-to-End実行できる
- 重大な未検出誤りがない
- 人間介入理由を分類できる
- 実装結果を上位仕様へフィードバックできる

## 2. Issue作成原則

Issueは1つの検証可能な成果物に限定する。複数文書を同時作成する場合も、同一の概念または同一の変更理由に限る。

必須項目:
- 成果物パス
- 目的
- 親文書
- 依存Issue
- 必須セクション
- 完了条件
- 非対象
- 検証方法

## 3. 最初のIssue群

1. Human-Agent Responsibility Boundaryを定義する
2. Work Object概念仕様を作成する
3. Work Object JSON Schemaを作成する
4. Work Object状態遷移を定義する
5. Evidence Modelを定義する
6. Exception Modelを定義する
7. Policy Modelを定義する
8. 文書LintとSchema Validationを設計する
