# Contributing

## 1. 基本方針

本リポジトリへの変更は、説明文の追加ではなく、実装・検証・監査に利用できる仕様の改善として行う。

複数AIエージェントによる変更は、`docs/12-roadmap/phase-0-multi-agent-repository-foundation.md`に従い、Work Package、Context Bundle、役割分離、変更クラス、独立レビュー、Validationを通じて統制する。

## 2. 作業開始前

1. `README.md`を読む。
2. `docs/00-overview/`を読む。
3. `governance/invariants.yaml`と`governance/change-classes.yaml`を読む。
4. `docs/01-architecture/document-architecture.md`を読む。
5. `docs/12-roadmap/phase-0-multi-agent-repository-foundation.md`を読む。
6. `docs/12-roadmap/document-roadmap.md`で依存順を確認する。
7. 既存Issue、PR、RFC、ADR、Registry、用語集を検索する。
8. 変更対象の親文書と影響を受ける下位文書を特定する。
9. Work PackageとContext Bundleを確認する。

## 3. IssueとWork Package

変更は原則としてIssueに紐づける。Issueには次を含める。

- 成果物のパス
- 解決する問題
- 目的
- 対象と非対象
- 親文書
- 依存IssueまたはPR
- 変更クラス
- 適用不変条件
- 担当Agent Role
- Reviewer Role
- 必須セクション
- 完了条件
- 検証方法

Phase 0完了後、IssueはTask CuratorによってWork Packageへ変換する。Work Packageには次を追加する。

- base commit
- deliverables
- required context
- editable paths
- read-only paths
- forbidden paths
- tools allowed
- acceptance tests
- lease
- timeout
- escalation
- completion authority

## 4. 変更クラス

変更クラスは`governance/change-classes.yaml`を正とする。

- C0: 誤字、リンク、書式
- C1: 規範的意味を変えない明確化
- C2: 下位仕様の非破壊追加
- C3: 共通モデル、Protocol、共有Schemaの変更
- C4: L0/L1、不変条件、責任境界の変更
- C5: 法的、倫理的、重大リスクに関する変更

Authorは変更クラスを単独で引き下げてはならない。判断が難しい場合は高いクラスを仮設定する。

## 5. 改善提案

C3以上の改善提案は、正式仕様へ直接含めずRFCとして分離する。

RFCには次を含める。

- 現行設計の問題
- 変更しない場合の影響
- 提案変更
- 代替案
- 変更しない案
- 影響する不変条件
- 影響文書、Schema、Example、Test
- 互換性
- 移行
- ロールバック
- 反証結果
- 採否権限

RFCが`ACCEPTED`となり、必要なADRが承認されるまで、規範文書を先行変更しない。

## 6. 文書作成規則

正式仕様には次を含める。

- 必須メタデータ
- 目的
- 適用範囲
- 前提条件
- 入力
- 出力
- 主体と責任
- 必要権限
- 状態遷移または処理順序
- 正常系
- 例外系
- タイムアウト、再試行、代替処理
- Evidence
- 完了条件
- テスト
- 移行とロールバック
- 未決事項

抽象的な理念だけで完了させない。逆に、上位概念を固定せず個別ツールの実装詳細から書き始めない。

## 7. 用語

- `docs/00-overview/glossary.md`の定義を使用する。
- 新しい概念は最初に用語集へ追加する。
- 同一概念の別名を増やさない。
- 「対応中」「保留」「確認中」など、退出条件のない状態を定義しない。
- 用語変更時はDocument Registryと影響文書を更新する。

## 8. Schema、Template、Example、Test

- Templateは可能な限りJSON Schemaで検証可能にする。
- Schemaには`$id`、`title`、`description`、version、必須項目、追加プロパティ方針を定義する。
- 破壊的変更は版を上げ、移行手順を追加する。
- Schema、Template、Example、Testを同一変更系列で更新する。
- 正常例だけでなく、欠損、型違反、意味矛盾、不変条件違反の例を作る。
- 関連Golden Scenarioを更新する。

## 9. Pull Request

PR本文は`.github/PULL_REQUEST_TEMPLATE.md`を使用し、最低限次を含める。

1. Work PackageとContext Bundle
2. change class
3. 変更理由と目的
4. 変更内容と編集範囲
5. 上位文書・不変条件との整合性
6. Traceabilityへの影響
7. Validation結果とEvidence
8. 必要な独立レビュー
9. 未解決事項
10. 移行とロールバック

mainへの直接pushは原則禁止する。緊急例外は期限付きで記録し、事後レビューを必須とする。

## 10. レビュー順序

1. Author Self-check
2. Structural Validation
3. Schema Validation
4. Consistency Review
5. Challenger Review
6. Control Review
7. Integration Review
8. HumanまたはSpecialist Approval（必要な変更のみ）

変更クラス別の必須ロールと検査は`governance/approval-matrix.yaml`を正とする。

## 11. レビュー基準

レビューでは文章表現より先に以下を確認する。

- 目的達成に必要な仕様か
- 既存業務を無批判に温存していないか
- 上位文書と不変条件に整合するか
- 責任と権限が一致しているか
- 人間への負荷移転になっていないか
- 例外が有限な状態として定義されているか
- 完了条件を第三者が検証できるか
- Evidenceと再現性があるか
- 特定ベンダーへ不要に依存していないか
- 高リスク操作に独立検証があるか
- Context Bundleが陳腐化していないか
- Registry、Schema、Example、Test、Golden Scenarioが更新されているか

## 12. ADRが必要な変更

- 上位アーキテクチャの変更
- Work Objectの識別・状態・責任モデルの変更
- Policy評価優先順位の変更
- 人間とAIの責任境界の変更
- 互換性を失うSchema変更
- 監査Evidenceまたは権限モデルの変更
- 特定技術を標準として採用する判断
- G0 Repository Governanceの規範変更

C3以上は原則としてRFCを先行させる。

## 13. Handoff

作業を完了できない場合、Handoff Packageを作成する。

- 完了した作業
- 未完了作業
- 変更ファイル
- 判断とEvidence
- 失敗履歴
- 競合
- 次の推奨行動
- 引継ぎに必要なRole
- 再検証項目

失敗履歴を消去して別エージェントへ最初から同じ試行をさせない。

## 14. Merge Conditions

- 変更クラス別の必須Reviewが揃っている
- 必須CIが成功している
- 未解決レビュー会話がない
- Context Bundleが陳腐化していない
- Authorが唯一のApproverではない
- 必須依存Issueが完了している
- Registryと関連成果物が更新されている
- C3以上はRFCとADRが承認済みである
- C4以上はHuman Governorが承認している
