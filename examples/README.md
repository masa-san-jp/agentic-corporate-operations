# Examples

仕様とSchemaを具体的な業務データへ適用した例を配置する。

## Directory Policy

```text
examples/
├── common/
├── finance/
├── hr/
├── legal/
├── procurement/
├── it-security/
└── governance/
```

## Required Example Types

- 最小有効例
- 完全有効例
- 必須項目欠損例
- 型違反例
- 意味的矛盾例
- 高リスク業務例
- 例外と再試行例
- 人間エスカレーション例
- 完了Evidence付き例

## Rules

- 実在する個人情報、認証情報、口座、契約情報を使用しない。
- 例がどのSchema版と仕様版に対応するか明記する。
- 無効例は、期待するエラー理由を併記する。
- 説明のためにSchema制約を回避しない。
