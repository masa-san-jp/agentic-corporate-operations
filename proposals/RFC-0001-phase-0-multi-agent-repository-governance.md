# RFC-0001: Phase 0 Multi-Agent Repository Governance

```yaml
rfc_id: RFC-0001
title: Phase 0 Multi-Agent Repository Governance
status: ACCEPTED
change_class: C4
proposer_role: chief-architect
proposer_agent_run_id: bootstrap-chat-20260730
created_at: 2026-07-30
updated_at: 2026-07-30
base_commit: 3c9a70891eae8a80a497dbf8d7cdd5c78148e18f
affected_invariants:
  - INV-001
  - INV-003
  - INV-004
  - INV-005
  - INV-008
affected_documents:
  - docs/01-architecture/document-architecture.md
  - docs/12-roadmap/document-roadmap.md
  - AGENTS.md
  - CONTRIBUTING.md
affected_schemas: []
affected_protocols:
  - document-production-governance
related_issues:
  - 9
  - 10
  - 11
  - 12
  - 13
  - 14
  - 8
  - 15
  - 16
related_adrs:
  - ADR-0001
reviewers:
  - human-governor
decision_authority: human-governor
```

## 1. Problem

既存リポジトリには、文書階層、AI向け必読順序、Definition of Done、Issue、ADR、ロードマップがある。一方、複数AIエージェントを並列稼働させるための設計不変条件、機械可読な依存関係、役割分離、作業リース、引継ぎ、改善提案の分離、独立レビュー、意味的Validationが不足している。

この状態でエージェント数を増やすと、局所的には妥当な文書が増えても、用語分岐、上位設計の無断変更、競合、自己承認、依存更新漏れが増加する。

## 2. Impact of No Change

- 初期設計からの無自覚な乖離
- 同一概念の重複定義
- 同じファイル・概念への並列競合
- 異なるbase commitに基づく成果物の混在
- 改善提案の正式仕様への直接混入
- Authorの自己レビューによる誤仕様の固定
- エージェント停止時の調査・作業の喪失
- 文書単体は正しいが全体として実行不能な状態

## 3. Proposed Change

Stage 0をPhase 0: Multi-Agent Repository Foundationへ改修し、次を導入する。

- G0 Repository Governance
- Design Invariants
- C0〜C5 Change Classes
- Approval Matrix
- Document Registry and Traceability Graph
- Agent Roles
- Work Package and Context Bundle
- Task Lease and Handoff
- RFC Proposal Governance
- Pull Request and Merge Gates
- Validation Layers
- Golden Scenarios
- Agent Provenance and Tool Permissions

Issue #1〜#7の並列正式着手はPhase 0ゲート後とする。

## 4. Alternatives

### Alternative A: AGENTS.mdだけを詳細化する

実装は容易だが、規則を機械検証できず、エージェントの善意と読解能力へ依存するため不採用。

### Alternative B: 単一の統括エージェントだけを使う

競合は減るが、独立レビューと並列性を失い、単一障害点になるため不採用。

### No-change option

文書数の増加に伴い整合性管理が破綻する可能性が高いため不採用。

## 5. Invariant Analysis

| Invariant | Impact |
|---|---|
| INV-001 | 上位制約を機械可読化し強化する |
| INV-003 | AuthorとApprovalの分離を追加する |
| INV-004 | 改善をRFCへ分離する |
| INV-005 | base commitとContext Bundleを固定する |
| INV-008 | mainへのReview・Validation Gateを定義する |

## 6. Traceability Impact

- `docs/01-architecture/document-architecture.md`をG0対応へ変更
- `docs/12-roadmap/document-roadmap.md`のStage 0を置換
- `AGENTS.md`と`CONTRIBUTING.md`へWork Package規則を追加
- `governance/`、`registry/`、`orchestration/`、`proposals/`を追加
- Issue #9〜#16をPhase 0 Workstreamとして追加

## 7. Compatibility and Migration

既存Issue #1〜#8は削除しない。Phase 0との依存を追記し、成果物パスと目的を維持する。

既存文書は直ちにapproved扱いにせず、Document Registryへdraftとして段階移行する。

## 8. Risks and Controls

| Risk | Control |
|---|---|
| 初期基盤が過剰に複雑になる | Phase 0を最小ゲートと後続拡張に分ける |
| Registryの二重管理 | dependent情報を可能な限り自動生成する |
| 形式だけ整い内容が弱くなる | Golden ScenarioとChallenger Reviewを要求する |
| AI Roleが名目だけになる | Agent Run IDと独立性規則を検証する |
| 開発が停止する | Phase 0中も単一エージェントの調査・草案を許可する |

## 9. Rollback

Phase 0の追加ファイルを廃止し、Document Roadmap、Document Architecture、AGENTS.md、CONTRIBUTING.mdをbase commitの状態へ戻す。ただし、作成済みRFC、ADR、Issueは履歴として保持する。

## 10. Challenge Record

### Counterarguments

- 仕様書作成だけに過剰なガバナンスではないか。
- GitHub IssueとPRだけで十分ではないか。
- 複数エージェントの能力向上で自然に解消されるのではないか。

### Response

対象は数十〜数百の相互依存文書、Schema、Protocolであり、能力向上だけでは同時編集、版、権限、承認、Traceabilityの問題を解消できない。Phase 0は文書量を増やす制度ではなく、必要な検証を自動化して人間の管理負担を下げる基盤である。

## 11. Decision

```yaml
decision: ACCEPTED
decided_by: masa-san-jp
decided_at: 2026-07-30
conditions:
  - Phase 0を既存ロードマップへ統合する
  - 改善提案経路を正式仕様変更から分離する
  - Phase 0完了前の並列正式着手を制限する
reason: 複数AIエージェントが設計整合性を維持しながら自律的に仕様体系を完成させるため
```

## 12. Implementation and Verification

- implementation branch: `phase-0-multi-agent-governance`
- related ADR: `decisions/ADR-0001-adopt-phase-0-multi-agent-repository-governance.md`
- validation: Pull Request diff review
- remaining automated validation: Issue #8
