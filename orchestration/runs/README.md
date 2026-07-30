# Agent Runs

このディレクトリは、AIエージェントによる作成、検証、レビュー、統合の実行記録を保存する。

各Agent Runは最低限次を記録する。

- agent_run_id
- agent_role
- model and model version
- instruction version
- work_package_id
- context_bundle_id
- base commit
- tools used
- files read and modified
- started_at and completed_at
- validation results
- review results
- uncertainty
- known limitations
- exception and handoff references

秘密情報、token、credential、個人情報の原文は記録しない。必要な場合は安全な保存先への参照と分類だけを記録する。

Agent RunはEvidenceであり、それ自体は設計判断または承認を意味しない。
