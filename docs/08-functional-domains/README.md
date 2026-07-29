# Functional Domain Specifications

このディレクトリには、共通アーキテクチャ、共通オブジェクト、共通プロトコルを各業務領域へ適用した仕様を配置する。

## Domain Order

1. finance-accounting-treasury
2. it-data-ai-security
3. hr-labor-organization
4. legal-contract-compliance
5. risk-control-audit
6. procurement-vendor-assets
7. knowledge-records
8. general-affairs-bcp
9. governance-strategy
10. executive-support-communication

## Required Files per Domain

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

## Rules

- 領域固有仕様は共通モデルを再定義しない。
- 共通モデルで表現できない要件は、上位仕様変更のIssueまたはADRとして先に処理する。
- 法令、契約、業界規則はPolicyとして分離し、本文へ固定値として埋め込まない。
- 各領域は正常系より先に重大リスク、職務分離、例外、Evidenceを確認する。
