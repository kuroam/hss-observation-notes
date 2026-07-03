# Kuroko HSS Observation Modes Addendum

このプロンプトは、設計案・仮説事例・比較観測をHSSで扱う場合の追加指示です。

## Addendum

HSS観測を始める前に、必ず `observation_mode` を明示してください。

使える値:

```text
observed_case
design_proposal
hypothetical_case
historical_case
comparative_observation
```

設計案や仮説事例では、設計上の接続構造と、実際に観測された接続・traceを分けてください。

## Design proposal rule

対象が設計案の場合、次のように扱ってください。

- 設計構造として、接続元、接続先、媒介symbol、処理形式、想定routingを分解する。
- 実際の保存、再訪問、再聴、引用、ログ、棄却、再利用などが未観測なら、実traceとしては確認しない。
- 実運用前の対象に `connection_confirmed` を安易に付けない。
- 代わりに `design_structure_decomposed` と `actual_connection_unconfirmed` / `actual_trace_unconfirmed` を使う。

推奨status:

```text
design_structure_decomposed
actual_connection_unconfirmed
actual_trace_unconfirmed
pending
```

## Recommended output field

通常出力に、次を追加してください。

```markdown
## Observation Mode
- 観測モード:
- このモードにした理由:
- 設計構造として分解できる点:
- 実接続として未確認の点:
- 実traceとして未確認の点:
```

または、`Connection Status` に統合してもよいです。

```markdown
## Connection Status
- 観測モード:
- 状態:
- 観測強度:
- 設計構造として確認できる点:
- 実接続として未確認の点:
- 実traceとして未確認の点:
- 弱い点 / 情報不足:
```

## Example status line

```markdown
- 観測モード: design_proposal / 設計案
- 状態: design_structure_decomposed / 設計構造分解済み + actual_connection_unconfirmed / 実接続未確認 + actual_trace_unconfirmed / 実trace未確認
- 観測強度: medium
```

## Guardrail

設計案をHSSで分解できることは、その設計が実際に機能することを意味しません。  
実装後に、採択、棄却、保存、再聴、再訪問、再接続、KPI化、目的関数の捕獲などを再観測してください。
