# Agentic Corporate Operations

AIエージェントによって事業会社のノンプロフィット領域を極限まで自動化するための、参照アーキテクチャ、要求仕様、Protocol、Schema、実装手順を管理するリポジトリです。

## 目的

人間の役割を、反復的な処理から次の責任へ移行させます。

- 目的と成果の定義
- 価値基準とリスク許容度の設定
- 不可逆・高影響な意思決定
- 新規例外の規範化
- AIエージェント群の独立保証

AIエージェントは、業務の発見、構造化、計画、実行、検証、証跡化、例外収束、継続改善を担当します。

## 対象領域

- 経営ガバナンス・意思決定
- 戦略・予算・ポートフォリオ
- 財務・会計・税務・資金
- 法務・契約・コンプライアンス
- リスク・内部統制・内部監査
- 人事・労務・組織
- 調達・購買・ベンダー・資産
- IT・データ・AI・情報セキュリティ
- ナレッジ・文書・記録管理
- 総務・施設・BCP・インシデント
- 経営秘書・社内コミュニケーション

## 設計原則

1. すべての業務を検証可能なWork Objectとして扱う。
2. 通常処理ではなく例外処理を中心に組織を設計する。
3. 起案、承認、実行、検証を論理的に分離する。
4. 時間経過ではなくEvidenceによって業務状態を遷移させる。
5. 人間への照会を判断可能な選択肢へ変換する。
6. 同じ停止理由を再実行可能な能力へ変換する。
7. 文書は実装、検証、監査に利用できる構造で記述する。
8. 改善提案を歓迎するが、上位設計変更はRFC、反証、承認を経る。
9. AIエージェントは固定されたContext Bundleと限定された権限で作業する。
10. 自己レビューだけで正式仕様へ昇格しない。

## 文書構成

- `docs/00-overview/`: 目的、対象、原則、用語
- `docs/01-architecture/`: 全体構造、責任境界、共通モデル
- `docs/02-phase-1-visibility/`〜`docs/07-phase-6-self-improvement/`: Phase別仕様
- `docs/08-functional-domains/`: 業務領域別仕様
- `docs/09-protocols/`: 共通Protocol
- `docs/10-templates/`: 文書・データ・Work Package・Handoffテンプレート
- `docs/11-implementation/`: 実装、統合、試験、運用
- `docs/12-roadmap/`: 文書作成・実装ロードマップ
- `docs/99-source-materials/`: 初期構想資料
- `governance/`: 不変条件、変更クラス、承認、権限
- `registry/`: 文書、Schema、Protocol、ADR、Source、Scenarioの台帳
- `orchestration/`: Agent Role、Work Package、Context Bundle、Handoff、Run
- `proposals/`: 採用前のRFCと改善提案
- `schemas/`: 機械可読Schema
- `examples/`: 正常・異常例とGolden Scenario
- `decisions/`: Architecture Decision Records
- `validation/`: 文書・Schema・意味・統合検証

## 現在の段階

現在は**Phase 0: Multi-Agent Repository Foundation**です。

複数AIエージェントを並列稼働させる前に、次を構築します。

- Design Invariants
- Change Classes and Approval Matrix
- Document Registry and Traceability Graph
- Agent Roles and Work Orchestration
- Work Package and Context Bundle
- Task Lease and Handoff
- RFC and Change Proposal Governance
- Pull Request and Merge Gates
- Validation and Golden Scenarios
- Agent Provenance and Security

詳細:

- [`docs/12-roadmap/phase-0-multi-agent-repository-foundation.md`](docs/12-roadmap/phase-0-multi-agent-repository-foundation.md)
- [Issue #9: Phase 0 umbrella](https://github.com/masa-san-jp/agentic-corporate-operations/issues/9)

Phase 0の必須ゲートが完了するまで、共通モデルのIssue #1〜#7を複数エージェントへ無秩序に並列割当しません。
