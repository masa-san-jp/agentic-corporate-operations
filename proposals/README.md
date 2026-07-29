# Proposals

このディレクトリは、採用前の改善提案、設計変更案、反証、却下案、保留案を管理する。

## Difference from ADR

- RFC: 採否を決める前の提案と議論
- ADR: 採用された重要設計判断の記録

RFCを作成しただけでは、正式仕様は変更されない。RFCが`ACCEPTED`となり、必要なADR、移行計画、承認が揃った後に、別の実装PRで正式仕様を変更する。

## RFC states

```text
DRAFT
→ CHALLENGED
→ REVISED
→ EVALUATED
→ ACCEPTED | REJECTED | DEFERRED
→ IMPLEMENTED
→ VERIFIED
```

## Required for C3 or higher

- 現行設計の問題
- 変更しない場合の影響
- 提案案
- 代替案
- 変更しない案
- 影響する不変条件
- 影響文書、Schema、Example、Test
- 互換性
- 移行
- ロールバック
- 反証結果
- 採否権限

## Naming

`RFC-NNNN-kebab-case-title.md`
