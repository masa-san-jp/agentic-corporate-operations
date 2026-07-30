# Golden Scenarios

Golden Scenarioは、個別文書の局所的な妥当性ではなく、複数の共通モデル、Protocol、Phase、機能領域を組み合わせたEnd-to-End整合性を検証する。

## Initial scenarios

1. `invoice-to-payment-and-evidence/`
2. `hire-to-access-and-onboarding/`
3. `api-failure-to-recovery-and-escalation/`

## Required fields

- scenario_id
- purpose
- initial state
- actors
- inputs
- applicable policies
- expected Work Objects
- expected state transitions
- expected Evidence
- expected Exceptions
- expected Decisions
- prohibited outcomes
- acceptance criteria

各Scenarioは正常例と少なくとも1つの異常例を持つ。Issue #15でSchema、Registry、Validationを実装する。
