# ADR-0001: Adopt Phase 0 Multi-Agent Repository Governance

```yaml
adr_id: ADR-0001
status: accepted
decision_date: 2026-07-30
decision_authority: masa-san-jp
change_class: C4
related_rfc: RFC-0001
related_issue: 9
```

## Context

本リポジトリは、多数の相互依存する文書、Schema、Protocol、Template、Example、Testを複数AIエージェントによって作成することを目的としている。

既存の文書階層、AGENTS.md、CONTRIBUTING.md、Issue、ADR、ロードマップだけでは、次を強制できない。

- 同一の設計スナップショットの参照
- 上位設計の不変条件
- エージェントの役割と権限分離
- 同時編集の排他
- 停止作業の引継ぎ
- 改善提案と正式変更の分離
- 変更クラス別の独立レビュー
- 文書横断の意味的・統合検証

## Decision

Stage 0をPhase 0: Multi-Agent Repository Foundationへ置き換える。

Phase 0では次をリポジトリの恒常的な基盤として導入する。

1. G0 Repository Governance
2. Design Invariants
3. Change Classes and Approval Matrix
4. Document Registry and Traceability Graph
5. Agent Role Separation
6. Work Package and Context Bundle
7. Task Lease and Handoff
8. RFC Change Proposal Governance
9. Pull Request and Merge Gates
10. Validation Layers and Golden Scenarios
11. Agent Provenance, Security, and Tool Permissions

Issue #1〜#7の複数エージェントによる並列正式着手は、Phase 0の必須ゲート完了後とする。

## Consequences

### Positive

- 初期設計からの無自覚な乖離を検出できる
- 改善提案を止めずに、正式変更と分離できる
- 複数エージェントの同時編集と自己承認を抑制できる
- エージェント停止時に作業を引き継げる
- 仕様全体をGolden Scenarioで検証できる
- モデルや指示の変更による結果差分を追跡できる

### Negative

- Phase 0完了前に作るべき基盤文書とSchemaが増える
- 小規模変更にも一定のメタデータ管理が必要になる
- CIとRegistryの維持コストが発生する

### Mitigations

- C0〜C2には軽量な手続を適用する
- Phase 0中も調査・草案作成は許可する
- 二重管理を避けるため、依存先とDashboardは可能な限り自動生成する
- AIレビューを補助に使うが、形式的なレビュー数の増加を目的にしない

## Alternatives Rejected

- AGENTS.mdだけを詳細化する
- 単一統括エージェントだけを使用する
- GitHub IssueとPRの自由運用に任せる
- 仕様完成後に整合性を一括修正する

## Verification

- Phase 0文書とIssue #9〜#16が存在する
- Governance、Registry、Orchestration、Proposalsの入口が存在する
- PR TemplateとCODEOWNERSが存在する
- Issue #8でValidation Gateを実装する
- Phase 0完了時にP0-01〜P0-07の受入試験を実施する
