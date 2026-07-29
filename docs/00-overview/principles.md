# Design Principles

## P01. Purpose before process
既存手順を自動化する前に、その業務が達成すべき目的と廃止可能性を確認する。

## P02. Work as data
業務をメッセージや担当者の記憶ではなく、識別子、状態、期限、入力、出力、完了条件、証跡を持つWork Objectとして扱う。

## P03. Evidence-driven state transition
時間経過、自己申告、曖昧なステータスではなく、検証可能な証拠によって状態を遷移させる。

## P04. Policy before prompt
重要な判断条件をプロンプトだけに埋め込まず、法令、規程、契約、権限、リスク許容度を機械可読なPolicyとして分離する。

## P05. Separation of duties
起案、承認、実行、検証、監査を論理的に分離する。同一エージェントの自己評価だけで高リスク業務を完了させない。

## P06. Exception-first design
正常系だけでなく、欠損、矛盾、外部待ち、権限不足、ツール障害、期限超過を有限な状態と処理規則として先に設計する。

## P07. Bounded autonomy
自律性は業務の影響、可逆性、検出可能性に応じて付与する。目的、価値、重大な権利、不可逆な判断は人間が保持する。

## P08. Idempotency and reversibility
再実行による二重処理を防止し、可能な限りロールバック、取消、補償トランザクションを用意する。

## P09. Model and vendor portability
モデル、クラウド、SaaS、エージェント実行基盤を交換できる境界を維持する。

## P10. One source, many views
同じ事実を複数箇所へ転記しない。原データと正規化データを保持し、用途別の表示や成果物を生成する。

## P11. Human attention as scarce capital
人間への通知・会議・承認要求は、価値判断または高影響な例外に限定する。AIが調査、要約、選択肢、推奨案、影響を準備する。

## P12. Failure becomes capability
反復する停止理由を放置せず、データ、ルール、ツール、権限、SOP、評価器の改善へ変換する。

## P13. Specifications must be executable
文書は説明だけでなく、入力、出力、状態、責任、例外、完了条件、スキーマ、テストを含み、実装と検証に利用可能にする。

## P14. No silent degradation
取得不能、判定不能、精度低下、外部障害を成功扱いしない。品質劣化は検知、記録、通知、代替処理の対象とする。

## P15. Delete before automate
価値を生まない報告、承認、転記、会議は、自動化する前に廃止する。
