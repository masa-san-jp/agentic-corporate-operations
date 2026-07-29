# Implementation Specifications

参照アーキテクチャと業務仕様を、交換可能な技術コンポーネントとして実装するための仕様を配置する。

## Planned Documents

- technical-reference-architecture.md
- integration-patterns.md
- identity-and-access.md
- secrets-management.md
- data-storage-and-lineage.md
- model-gateway.md
- agent-runtime.md
- orchestration-runtime.md
- observability.md
- security-model.md
- testing-strategy.md
- deployment-strategy.md
- migration-playbook.md
- rollback-and-recovery.md

## Rules

- 特定ベンダーの採用はADRで決定する。
- 業務仕様と技術実装を分離する。
- API、イベント、ファイル、RPAの選択条件を明示する。
- 認証情報を文書、プロンプト、サンプルへ埋め込まない。
- 本番実行には権限、冪等性、Evidence、停止、復旧を必須とする。
- モデル変更、Prompt変更、Tool変更を独立して版管理・回帰試験できる構造にする。
