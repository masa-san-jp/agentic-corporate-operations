# Schemas

AIエージェント、API、データストア、Validatorが共通利用する機械可読スキーマを配置する。

## Planned Schemas

- work-object.schema.json
- evidence.schema.json
- exception.schema.json
- policy.schema.json
- decision.schema.json
- agent.schema.json
- control.schema.json
- sop.schema.json

## Requirements

- JSON SchemaのDraftを明示する。
- `$id`、`title`、`description`、版を持つ。
- 必須属性と追加プロパティ方針を明示する。
- 識別子、日時、金額、参照、列挙値を制約する。
- 破壊的変更ではMajor Versionを更新する。
- Schema変更時にテンプレート、例、テスト、移行手順を同時更新する。
- 有効例と意図的な無効例を用意する。

Schemaは仕様本文の代替ではない。意味、責任、状態、例外の説明は対応する概念仕様へ記載する。
