# Governance

このディレクトリは、リポジトリ内の全エージェント、文書、Schema、Protocol、Pull Requestに適用する規範を管理する。

## Normative files

- `invariants.yaml`: 設計不変条件
- `change-classes.yaml`: 変更の影響区分と必要手続
- `approval-matrix.yaml`: 変更クラス別のレビュー・承認要件
- `tool-permissions.yaml`: エージェントロール別のツール権限（Issue #16で作成）

## Rules

1. このディレクトリの内容は、通常の下位仕様より優先する。
2. C3以上の変更はRFCとADRを必要とする。
3. C4以上の変更はHuman Governorの承認なしに成立しない。
4. エージェントは、割り当てられたWork Packageの変更クラスを自己判断で引き下げてはならない。
5. 不変条件への例外は暗黙に認めない。例外可能な不変条件に限り、期限、対象、承認者、補償統制を記録する。
