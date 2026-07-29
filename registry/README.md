# Registry

このディレクトリは、文書、Schema、Protocol、ADR、Source、Scenario、Releaseの正規台帳を管理する。

## Planned registries

- `documents.yaml`: 正式文書と依存関係
- `schemas.yaml`: JSON Schemaと互換性
- `protocols.yaml`: Protocolと入出力
- `adrs.yaml`: ADRと影響範囲
- `sources.yaml`: 外部根拠の権威性、鮮度、適用範囲
- `scenarios.yaml`: Golden Scenarioと回帰対象
- `compatibility.yaml`: Release、Schema、Protocolの互換性
- `status.yaml`: 完成度、滞留、未解決事項

## Rules

1. 正式仕様は、ファイルを作成するだけでは登録されたことにならない。
2. `approved`にできるのは、必須依存が存在し、所定の検証を通過した成果物だけである。
3. レジストリ上の依存関係はDAGでなければならない。
4. `deprecated`成果物への新規依存は禁止する。
5. `dependent_documents`は可能な限り依存グラフから生成し、手作業の二重管理を避ける。
6. Issue、PR、ADR、Schema、Example、Testへの参照を追跡可能にする。
