# HSS Output Schema

この文書は、HSS観測結果を安定して出力するためのMarkdown形式のschemaです。  
機械処理用のJSON Schemaは `schema/hss_observation.schema.json` を参照してください。

## 1. 基本出力

```markdown
# HSS Observation: <target>

## 0. Scope
- 対象:
- 観測範囲:
- 観測しない範囲:
- この観測で断定しないこと:

## 1. Claimed Connection
- 接続しているとされているもの:
- 接続元:
- 接続先:
- 媒介symbol:
- 処理形式:
- 痕跡:
- routing:
- 再接続経路:

## 2. Layer Mapping
| Layer | 観測内容 | 根拠 | 保留点 |
| --- | --- | --- | --- |
| L1 接触 |  |  |  |
| L2 反応・痕跡 |  |  |  |
| L3 処理・routing |  |  |  |
| L4 継続接続 / 積層history |  |  |  |
| L5 圧縮 / 固定化symbol |  |  |  |
| L6 再接続 / 再展開 |  |  |  |
| L7-L8 予約層 | 直接モデル化しない。L1-L6上の痕跡として確認できる場合のみ記録する。 |  |  |

## 3. HSS Terms
- 固定化:
- Blue residuals:
- Shiwa:
- 接続可能なズレ:
- 揺り戻し欠損:
- 目的関数の捕獲:
- 積層ルーティング:

## 4. Connection Status
- 状態:
- 観測強度:
- 根拠:
- 弱い点:
- 情報不足:

## 5. Observation Notes
- 太くなっている接続:
- 細くなっている接続:
- 処理形式へ吸収されている接続:
- 残っているBlue residuals / Shiwa:
- 再接続できそうな経路:
- HSS語彙で差分が出た点:
- 通常説明で十分な点:
- 次に観測すること:

## 6. Non-Claims
- この観測で証明していないこと:
- この観測で断定していないこと:
- L7-L8として保留すること:
```

## 2. Compact Output

短い回答では、次の最小形式を使う。

```markdown
## HSS mini observation

- 対象:
- 接続元:
- 接続先:
- 媒介symbol:
- 処理形式:
- 痕跡:
- routing:
- 接続状態:
- 観測強度:
- 保留点:
```

## 3. Status values

出力で使うstatusは次のいずれか。

```text
connection_confirmed
connection_unconfirmed
wrong_destination
absorbed_into_processing_form
insufficient_trace
out_of_scope_layer
insufficient_information
low_confidence_observation
pending
```

日本語併記する場合:

```text
connection_confirmed / 接続確認
connection_unconfirmed / 接続未確認
wrong_destination / 接続先違い
absorbed_into_processing_form / 処理形式への吸収
insufficient_trace / 痕跡不足
out_of_scope_layer / 対象外レイヤー
insufficient_information / 情報不足
low_confidence_observation / 低信頼観測
pending / 保留
```

## 4. Observation strength values

```text
high
medium
low
pending
```

## 5. Field rules

### target

観測対象を書く。

### scope

どこまでを見るかを書く。

### excluded_scope

見ない範囲を書く。  
感情本質、AI意識、人格本質、善悪判定などは必要に応じてここに入れる。

### non_claims

この観測で断定しないことを書く。

### claimed_connection

対象内で「接続している」とされているものを書く。

### source / destination

接続元と接続先を分離する。  
分離できない場合は `insufficient_information` または `low_confidence_observation` とする。

### mediating_symbol

接続を媒介するsymbolを書く。  
symbolは意味そのものではなく、接続や処理形式への入口として扱う。

### processing_form

対象がどの処理形式へ変換されるかを書く。

### trace

観測可能な痕跡を書く。  
痕跡が弱い場合は `insufficient_trace` とする。

### routing

接続や痕跡がどこへ流れるかを書く。

### reserved_layer_notes

L7-L8由来の影響が疑われる場合にだけ書く。  
ただし、現行HSSでは直接モデル化しない。

### uncertainty

弱い点、情報不足、推測に留まる点を書く。

## 6. Example mini output

```markdown
## HSS mini observation

- 対象: 生成AIによる短尺BGM量産アプリ
- 接続元: 生成API、テンプレート化されたプロンプト、ユーザーの短期需要
- 接続先: 個別の音楽体験ではなく、SNS/広告/動画流通枠
- 媒介symbol: AI music、instant song、background music
- 処理形式: 生成数、再生数、CTR、投稿本数
- 痕跡: 大量投稿、似た曲の反復、短期反応ログ
- routing: 作品文脈ではなくフィード最適化へ戻る
- 接続状態: absorbed_into_processing_form / 処理形式への吸収
- 観測強度: medium
- 保留点: 個別ユーザー内での保存、再訪問、再接続があるかは未確認
```

## 7. Output guardrail phrase

必要に応じて、出力末尾に次のような断りを置く。

```markdown
この観測はHSS語彙による接続構造の仮分解であり、対象の善悪、成功失敗、真理性を断定するものではない。
```
