# Validation

文書、Schema、テンプレート、例、リンク、状態遷移の品質を自動検証する資材を配置する。

## Planned Structure

```text
validation/
├── document-checklist.md
├── validation-architecture.md
├── schema-tests/
├── link-tests/
└── fixtures/
```

## Validation Layers

1. Markdown構文
2. 内部リンクとファイル参照
3. 文書メタデータ
4. 用語・状態名の整合性
5. JSON Schemaの妥当性
6. YAML・JSON例のSchema適合
7. IDと参照の一意性
8. 正常・異常シナリオ
9. 破壊的変更と互換性
10. セキュリティ情報の混入

## Principles

- PRとローカルで同一の検証を実行できるようにする。
- 検証失敗はファイル、規則、修正対象を特定できる形で報告する。
- 外部AIサービスへ依存しない決定的検査を基盤とする。
- AIによる意味検査は補助層とし、決定的検査の代替にしない。
