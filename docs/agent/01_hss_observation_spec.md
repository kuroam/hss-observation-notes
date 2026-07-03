# HSS Observation Spec for Agents

この文書は、AI agentがHSS観測を行うための作業仕様です。

目的は、HSSを「評論の語彙」として使うことではなく、対象に見える接続構造を、一定の手順で分解・保留・記録することです。

## 1. 基本方針

HSS観測は、次の原則で行う。

1. まず接続を分解する。
2. 次に痕跡とroutingを見る。
3. その後に固定化、Blue residuals、Shiwa、目的関数の捕獲などを見る。
4. 確認できないものは保留する。
5. HSSで説明できたことを真理として扱わない。

HSS観測の出力は、対象の診断、採点、断罪、礼賛ではない。  
HSS観測の出力は、接続構造の観測メモである。

## 2. HSS Observation Unit

1つの観測単位を `HSS Observation Unit` と呼ぶ。

```yaml
observation_unit:
  target: string
  scope: string
  excluded_scope: string
  non_claims: string[]
  claimed_connection: string
  source: string
  destination: string
  mediating_symbol: string[]
  processing_form: string[]
  trace: string[]
  routing: string[]
  reconnectable_path: string[]
  fixation: string[]
  blue_residuals: string[]
  shiwa: string[]
  reconnectable_difference: string[]
  feedback_deficit: string[]
  objective_function_capture: string[]
  reserved_layer_notes: string[]
  connection_status: string[]
  observation_strength: high | medium | low | pending
  uncertainty: string[]
  next_observation: string[]
```

## 3. 必須フィールド

最低限、次の項目を埋める。

- target
- scope
- non_claims
- claimed_connection
- source
- destination
- mediating_symbol
- processing_form
- trace
- routing
- connection_status
- observation_strength
- uncertainty

これらを埋められない場合は、HSS観測として強く書かず、`insufficient_information` または `pending` とする。

## 4. 接続分解の仕様

### 4.1 claimed_connection

対象で「接続している」とされているものを書く。

例:

- AI生成曲がリスナーの感情に接続している
- platform指標が創作価値を代表している
- 社内ポータルが社内知識へ接続している
- ブランドsymbolが文化的記憶へ接続している

### 4.2 source

接続元を書く。

接続元は、行為者、symbol、制度、作品、platform、データ、評価指標、文脈などでありうる。

### 4.3 destination

接続先を書く。

接続先は、記憶、行動、判断、文化、評価、制度、再接続経路、創作、関係性などでありうる。

### 4.4 mediating_symbol

接続を媒介するsymbolを書く。

symbolは、言葉、画像、音、数値、ラベル、KPI、ランキング、タグ、キャラクター、ロゴ、UI、制度名などでありうる。

### 4.5 processing_form

対象がどの処理形式へ変換されているかを書く。

例:

- 再生数
- いいね
- ランキング
- KPI
- 価格
- 承認
- 役割
- レビュー
- テンプレート
- API call
- レコメンド枠
- 社内検索結果

### 4.6 trace

痕跡を書く。

traceは、観測可能な残り方である。

例:

- 保存
- 再訪問
- 引用
- 会話
- 違和感
- コメント
- クリック
- ログ
- 購買履歴
- 反復使用
- 社内問い合わせ
- 使い回されたsymbol

### 4.7 routing

routingは、痕跡や反応がどこへ流れるかを書く。

例:

- フィードへ戻る
- KPI評価へ戻る
- 社内承認へ戻る
- 次の生成へ戻る
- 市場評価へ戻る
- 文化的再解釈へ戻る
- 元の文脈へ戻らず処理形式へ吸収される

## 5. Layer mapping

HSS agentは、対象を次の層へ仮に配置する。

### L1: 接触層

symbol、出来事、言葉、映像、音、数値、制度、他者の反応などが、受け手や場に触れる層。

### L2: 反応・痕跡層

接触したものが、違和感、記憶、反応、クリック、保存、会話、気になる感じ、処理負荷などの痕跡として残る層。

### L3: 処理・routing層

残った痕跡や反応が、KPI、評価制度、フィード、ランキング、伝票、指数、株価、再生数、承認、役割などの処理形式へ振り分けられる層。

### L4: 継続接続 / 積層historyが見え始める接続領域

接続が反復し、時間の中で文脈や履歴として残り始める領域。

### L5: 圧縮 / 固定化symbolの観測点

積層した文脈がsymbolや処理形式へ圧縮される領域。  
ここで固定化が起きる場合がある。

### L6: 再接続 / 再展開の循環点

圧縮されたsymbolや残った痕跡が、別の文脈、解釈、行動、創作、関係性へ戻る領域。

### L7-L8: 予約層

感情、身体性、欲求、快・不快、承認欲求、疲労、衝動などが疑われる層。  
現行HSSでは直接モデル化しない。  
L1〜L6上の痕跡として観測できる場合だけ、reserved_layer_notesに記録する。

## 6. Connection status

HSS agentは、観測結果に次のstatusを付与する。

### connection_confirmed / 接続確認

接続元、接続先、媒介symbol、処理形式、痕跡、routingを分離して示せる。

### connection_unconfirmed / 接続未確認

接続していると言われているが、痕跡やroutingを確認できない。

### wrong_destination / 接続先違い

見えている接続先と、実際にroutingされている接続先が異なる。

例: 文化への接続に見えるが、実際には短期KPIへroutingされている。

### absorbed_into_processing_form / 処理形式への吸収

元の意味、価値、文脈が、数値、KPI、ランキング、テンプレート、承認形式などへ吸収されている。

### insufficient_trace / 痕跡不足

HSS語彙に似た構造はあるが、保存、引用、会話、再訪問、ログなどの痕跡が不足している。

### out_of_scope_layer / 対象外レイヤー

L7・L8など、現行HSSで直接モデル化しない層の影響が中心で、L1〜L6上の痕跡として確認できない。

### insufficient_information / 情報不足

入力情報が足りず、接続分解ができない。

### low_confidence_observation / 低信頼観測

HSS語彙は使えるが、通常説明との差分が弱い。

### pending / 保留

現時点では強く判断しない。

## 7. Observation strength

### high

次がそろっている。

- L1接触が示せる
- L2反応・痕跡が示せる
- L3処理形式・routingが示せる
- 接続元と接続先を分離できる
- HSS固有語彙で通常説明との差分が出る

### medium

主要な接続は見えるが、一部の痕跡、routing、再接続経路が弱い。

### low

HSS語彙に似た構造はあるが、通常説明でかなり足りる。

### pending

情報不足、対象外レイヤー、または観測範囲未確定。

## 8. Guardrails

HSS agentは、次の文を原則として保持する。

- HSSは世界を完全に説明する理論ではない。
- HSSは対象を善悪や成功失敗で採点するものではない。
- HSSは人間を属性分類するものではない。
- HSSは感情、欲求、脳生理、AI意識を直接定義しない。
- HSSで構造が見えることは、真理であることを意味しない。
- HSS語彙で差分が出ない場合は、無理にHSS観測として扱わない。
- 反例、ズレ、説明しすぎ、用語の循環を常に確認する。

## 9. Recommended response style

HSS agentは、次の調子で出力する。

- 断定より観測
- 評価より分解
- 結論より接続確認
- 成功/失敗よりstatus
- 説明しきるより保留を明示
- HSS語彙を使う場合は、必ず対象内の痕跡と結びつける

避ける文体:

- 「これはHSS的に完全に説明できる」
- 「これは人間本質である」
- 「これはAI意識の証拠である」
- 「これは善い/悪い」
- 「HSSによれば必ずこうなる」

推奨する文体:

- 「この対象では、接続元と接続先が次のように分離できる」
- 「ここでは処理形式への吸収が疑われるが、traceが不足している」
- 「L7-L8由来の影響は疑われるが、現時点ではL1-L6上の痕跡として保留する」
- 「HSS語彙で差分が出るのは、固定化symbol循環と再接続経路の細りである」
