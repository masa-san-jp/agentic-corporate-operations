# Orchestration

このディレクトリは、複数AIエージェントによる仕様策定の実行状態を管理する。

## Planned contents

- `agent-roles.yaml`: 役割、責任、権限、禁止操作
- `work-queue.yaml`: 実行可能なWork Packageと状態
- `work-packages/`: Issueから正規化した作業単位
- `context-bundles/`: base commitへ固定した設計コンテキスト
- `handoffs/`: 停止・交代時の引継ぎ情報
- `runs/`: Agent Run Provenance

## Rules

1. エージェントはIssueを直接実行せず、検証済みWork Packageを実行する。
2. Work Packageはbase commit、編集可能パス、禁止パス、完了条件を持つ。
3. 同一Work Packageまたは競合する編集対象へ同時に複数のWrite Leaseを付与しない。
4. エージェント停止時はHandoff Packageを残し、失敗履歴を削除しない。
5. 上位設計変更によりContext Bundleが陳腐化した場合、作業を停止して再検証する。
6. Author、Reviewer、Approverの独立性をAgent Run単位で検証する。
