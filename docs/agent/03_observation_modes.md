# 03. Observation Modes

この文書は、HSS agentが観測対象の種類を分けるための補助仕様です。

初回テストでは、Suno APIの個人向け状態適応音楽体験案を観測した。  
この対象は、稼働中の事例ではなく設計案だったため、接続構造は分解できる一方で、実際のtrace、保存、再訪問、再聴、棄却ログなどは未観測だった。

そのため、HSS agentは、対象を観測する前に `observation_mode` を明示する。

## 1. observation_mode

HSS agentは、観測対象を次のいずれかに分類する。

```text
observed_case
design_proposal
hypothetical_case
historical_case
comparative_observation
```

### observed_case / 観測済み事例

すでに実在する対象、稼働中の制度、公開済み作品、実際のSNS反応、運用ログなどを観測する場合。

この場合、trace、routing、再接続経路は、実際に見える痕跡を優先する。

### design_proposal / 設計案

まだ実装・運用されていない設計案、プロダクト案、API利用案、ワークフロー案などを観測する場合。

この場合、接続元、接続先、媒介symbol、処理形式、想定routingは分解できても、実traceは未観測であることが多い。  
`connection_confirmed` を安易に使わず、`design_structure_decomposed` と `actual_connection_unconfirmed` を併記する。

### hypothetical_case / 仮説事例

もし〜なら、という仮定上の対象を観測する場合。

この場合は、構造仮説として分解し、実traceは `actual_trace_unconfirmed` または `pending` とする。

### historical_case / 過去事例

過去に起きた対象を観測する場合。

この場合、当時のtraceと、後から残ったtraceを分ける。

### comparative_observation / 比較観測

複数の対象を比較し、routingや接続構造の差分を見る場合。

例:

- 大量生成型API利用 vs 採択ゲート付きAPI利用
- 短期KPI routing vs 個人内フィードバック routing
- 固定化symbol循環 vs Blue residualsを残す接続

## 2. 追加 connection_status

設計案・仮説事例を扱うため、次のstatusを追加する。

```text
design_structure_decomposed
actual_connection_unconfirmed
actual_trace_unconfirmed
```

### design_structure_decomposed / 設計構造分解済み

設計案として、接続元、接続先、媒介symbol、処理形式、想定routingを分解できる状態。

これは、実際の接続が確認されたことを意味しない。

### actual_connection_unconfirmed / 実接続未確認

設計上は接続が想定されるが、実際に利用者、場、文化、組織、作品、platformなどへ接続した痕跡がまだ確認されていない状態。

### actual_trace_unconfirmed / 実trace未確認

保存、再訪問、再聴、引用、会話、ログ、棄却、再利用などの実traceがまだ確認されていない状態。

## 3. 設計案を観測する場合の原則

設計案をHSSで観測する場合は、次を分ける。

1. 設計構造として分解できる接続
2. 実際に確認された接続
3. 想定されるが未確認のtrace
4. 実装後に観測すべきrouting

設計案に対して、次のように書くことを推奨する。

```text
状態: design_structure_decomposed / 設計構造分解済み
      actual_connection_unconfirmed / 実接続未確認
      actual_trace_unconfirmed / 実trace未確認
観測強度: medium または pending
```

設計上の構造がよく分解できても、実traceがない場合は `high` にしない。  
ただし、HSS語彙による差分が明確に出ている場合は `medium` として扱える。

## 4. Suno API設計案テストから得た補足

Suno APIによる個人向け状態適応音楽体験案では、次の分離が有効だった。

- 設計上の接続: 脈拍・睡眠・時間帯などのsignal → 状態ラベル → 数案提示 → 本人採択 → full generation
- 実接続: 未確認
- 実trace: 未確認
- 想定trace: 採択、棄却、保存、再聴、スキップ、再参照
- 重要なrouting差分: L2 traceとしての採択/棄却が、L3のfull generation routingを制御する

このような対象では、単に `connection_unconfirmed` とするだけでは弱すぎる。  
`design_structure_decomposed` によって、設計構造としては分解できたが、実接続は未確認であることを分けて記録する。

## 5. 出力への追加欄

HSS agentは、通常の出力に次を追加してよい。

```markdown
## Observation Mode
- 観測モード:
- このモードにした理由:
- 設計構造として分解できる点:
- 実接続として未確認の点:
- 実traceとして未確認の点:
```

または、`Connection Status` に次を追加する。

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

## 6. Guardrail

設計案をHSSで分解できることは、その設計が実際に機能することを意味しない。  
実装後のtrace、routing、保存、再訪問、再接続、棄却ログなどを再観測する必要がある。
