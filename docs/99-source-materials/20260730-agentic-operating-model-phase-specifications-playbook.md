# Phase別詳細仕様設計・手順書・テンプレート

作成日: 2026-07-30

## Phase1 可視化
### 目的
全業務をWork Object化する。

### 手順
1. 業務発生源一覧化
2. システム台帳作成
3. データ台帳作成
4. Work Object生成
5. 状態管理開始

### Work Objectテンプレート
```yaml
work_id:
title:
purpose:
status:
owner:
deadline:
risk:
inputs:
outputs:
dependencies:
acceptance_criteria:
```

---

## Phase2 正規化
### 手順
1. 業務分類
2. リスク分類
3. 権限体系
4. 完了基準
5. データ辞書
6. 例外コード体系

テンプレート
```yaml
process:
category:
required_input:
required_output:
validation:
```

---

## Phase3 自動化
### 手順
1. SOP分解
2. Agent設計
3. API接続
4. DryRun
5. 本番

Agentテンプレート
```yaml
agent:
purpose:
tools:
constraints:
validator:
retry:
```

---

## Phase4 統制
### 手順
1. Policy Engine
2. Audit Engine
3. Evidence Engine
4. Exception Engine

統制テンプレート
```yaml
control:
risk:
preventive:
detective:
corrective:
evidence:
```

---

## Phase5 経営統合

Decisionテンプレート
```yaml
decision:
purpose:
alternatives:
recommended:
approved_by:
review_date:
```

---

## Phase6 自己改善

改善テンプレート
```yaml
problem:
root_cause:
solution:
expected_effect:
rollback:
```

---

## 共通テンプレート

### SOP
```yaml
name:
trigger:
steps:
validation:
exceptions:
owner:
version:
```

### Policy
```yaml
policy:
scope:
rule:
authority:
version:
```

### Evidence
```yaml
evidence:
source:
timestamp:
hash:
linked_work:
```

### KPI
```yaml
name:
formula:
target:
frequency:
owner:
```

## Phase完了基準

- Phase1: 業務・データ・システム可視化
- Phase2: 業務標準化
- Phase3: 定型業務自律化
- Phase4: 全証跡・監査対応
- Phase5: 経営意思決定統合
- Phase6: 継続的自己改善
