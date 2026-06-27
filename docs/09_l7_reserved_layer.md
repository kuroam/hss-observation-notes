# 09. L7予約層メモ

## 0. この文書の位置づけ

この文書は、`docs/06_scope_and_author_notes.md` で予約層として扱っていた L7 について、現時点で整理できる範囲を記録するための補助メモです。

L7は、HSSの外にある層ではありません。既存の公開メモでは、誤読を避けるためにL1〜L6を中心に形式化し、L7・L8は予約層として扱っていました。

ここでいう予約層とは、存在や重要性を否定する層ではなく、現行版で明示的に形式化していなかった層を指します。

したがって、この文書はHSSを当初の射程外へ拡張するものではありません。むしろ、もともとHSSの概念射程に含まれていた予約層のうち、L7について、内部整理可能な範囲を明文化するものです。

ただし、この文書は論文草稿ではありません。L7 core model、内部例、論文候補を分けるための観測メモとして扱います。

---

## 1. L7の基本位置

L7は、感情、欲求、人格、AI意識、倫理、人間本質を直接説明する理論ではありません。

L7は、インターフェースを持つ接続単位が入力を受けたとき、どの signal / symbol が起動し、どの routing を通り、どの方向へ発露され、戻り値によって何が更新・固定化され、どの trace / Shiwa を残すかを観測する層です。

暫定定義：

> L7は、インターフェースを持つ接続単位が入力を受けたとき、signal / symbol を起動し、Shiwa / Scar / policy によって routing され、発露・行動・語り・沈黙・回避・接近として外へ出し、その trace が次回 session の Shiwa へ積層する過程を観測する層である。

英語候補：

> L7 is an interface-level observational layer for tracing how an input activates signals or symbols, is routed through policy-like structures, is emitted as expression, action, silence, avoidance, or approach, and leaves traces that may accumulate as Shiwa.

---

## 2. L7 Coreの二層構成

L7 Coreは、現時点では次の二層に分けて整理します。

1. **L7 Minimum Core**
   - 単体 session における input / activation / routing / emission / return value / trace / Shiwa を観測する。

2. **L7 Crowd / Field Core**
   - 複数の単体発露ベクトルが、共有surface、platform、場、可視性、戻り値、反復によって重ね合わされ、増幅・抑制・固定化・残差化する過程を観測する。

ここで重要なのは、Crowd / Field Core を Minimum Core の単純な合計として扱わないことです。

群衆や場で見えるパターンは、単体ベクトルを平均したものではなく、場の処理形式によって再 routing された結果として観測します。

短縮表現：

- L7 Minimum Core = vector extraction
- L7 Crowd / Field Core = vector-field routing observation

日本語：

- L7 Minimum Core：一本の発露ベクトルを取る。
- L7 Crowd / Field Core：そのベクトルが場でどう再 routing されるかを見る。

---

## 3. L7 Minimum Core

L7 Minimum Core は、単体 session の観測モデルです。

1つの入力に対して、1つの接続単位がどう起動し、routingされ、発露し、戻り値を受け、trace / Shiwa を残すかを観測します。

基本 cycle：

```text
入力
→ signal / symbol 起動
→ Shiwa / Scar / policy による routing
→ L8側状態による閾値・重みづけ
→ firewall / load balancer 的な判定
→ allow / deny / reroute / alert / drop
→ 発露・行動・語り・沈黙・回避・接近
→ 戻り値
→ 自己symbolまたはrouteの更新／固定化
→ trace化
→ 次回sessionのShiwaへ積層
```

ここでの「L8側状態」は、身体性、疲労、痛み、快・不快、衝動、脳生理などを直接推定するものではありません。L7 Minimum Core では、同じ入力でも閾値・重みづけ・routing が変化しているように見える場合に限り、L8側状態が影響している可能性を保留的に扱います。L8そのものは、この文書では直接形式化しません。

Minimum Core で見る観測単位：

- input / trigger：何が入力されたか。
- activated signal / symbol：何が起動したか。
- routing：どの policy / Shiwa route を通ったか。
- emission：発露、語り、沈黙、回避、接近、攻撃、冗談、説明など、何として外へ出たか。
- direction：発露がどこへ向かったか。
- intensity：強度、軽さ、過剰さ、持続性。
- return value：相手、場、AI、platform、制度から何が返ったか。
- update / fixation：自己symbolやrouteが更新されたか、補強されたか、遮断されたか、固定化されたか。
- trace：何が痕跡として残ったか。
- Shiwa：traceが積層し、次回以降の routing 閾値・コスト・接続先を変えたか。
- residual：分類や集約で漏れた発露があるか。

短縮定義：

> Shiwa = 自己symbolやroutingを変質させる、圧縮された積層routing痕跡。

---

## 4. L7 Crowd / Field Core

L7 Crowd / Field Core は、複数の L7 emission vectors が、共有された場・platform・可視性・戻り値・反復によって重ね合わされ、増幅・抑制・再 routing・固定化・残差化する過程を観測するモデルです。

ここでいう群衆は、人数の多さそのものではありません。

3人でも、同じ場・同じplatform・同じ戻り値ループに入れば、Crowd / Field Core が必要になる場合があります。逆に、1000件の独立投稿でも、相互作用や共有surfaceが薄ければ、Minimum Core の集計で足りる場合があります。

暫定定義：

> L7 Crowd / Field Core observes how multiple L7 emission vectors are overlaid, amplified, suppressed, rerouted, stabilized, or left as residuals through shared fields, platforms, visibility structures, feedback loops, and return values.

日本語：

> L7 Crowd / Field Core は、複数のL7発露ベクトルが、共有された場・platform・可視性・戻り値・反復によって重ね合わされ、増幅・抑制・再 routing・固定化・残差化する過程を観測するモデルである。

---

## 5. Crowd / Field Coreで見る観測単位

Crowd / Field Core では、Minimum Core とは異なる観測単位が必要になります。

- unit vectors：単体sessionから抽出された発露ベクトル。
- shared trigger：何が共通入力になっているか。
- shared surface：どの場・platform・コミュニティで可視化されているか。
- target distribution：発露がどの対象へ向かっているか。
- emission clusters：不満、怒り、攻撃、嘲笑、防衛、遊び、沈黙などの束。
- feedback loops：いいね、引用、反論、通報、無視、称賛などの戻り値。
- amplification：増幅された発露・方向・ラベル。
- suppression：見えにくくなった発露・言いにくくなった反応。
- stabilization：ラベル、敵味方、物語、規範として固定化されたもの。
- drift：最初のtriggerから意味や対象がズレる過程。
- residuals：主パターンに吸収されなかった発露。
- burning residuals：残差が負荷・沈黙・不可視労働として燃える場合。

特に重要なのは、amplification だけでなく、suppression と residuals を見ることです。

通常の群衆分析では、可視化された大きな反応だけが「世論」「炎上」「トレンド」として読まれやすい。L7 Crowd / Field Core では、何が増幅されたかだけでなく、何が見えにくくなり、何が主パターンに吸収されず残ったかを観測します。

---

## 6. Crowd / Field Coreの分解軸

Crowd / Field Coreでは、反応全体を一発でMECEにしようとしません。

感情名は重なりやすいため、怒り、不満、攻撃、嘲笑、防衛、遊びなどをそのままMECE分類の主軸にすると崩れます。

そのため、以下のように複数の軸を分け、それぞれの軸内で primary label を1つ付けることを基本とします。

ここで示すラベル群は、感情や行動の本質分類ではありません。観測された発露ベクトルを暫定的に記録・比較するための coding aid です。MECE性は記録用の主分類に対して適用し、現象そのものがMECEであるとは仮定しません。

各軸では primary label を1つ付けます。ただし、発露の重なりや曖昧さは secondary tags と memo に残します。たとえば、PLAYでありながらSANCTIONとしても機能する皮肉、DEFENSEでありながらREPAIRとしても機能する説明は、primary label と secondary tags を分けて記録します。

### Axis A: Primary emission function

発露の主機能。感情名ではなく、その発露が場に対して何をしているかを見る。

- REPORT：事実・観測の提示。
- INQUIRY：質問・探索。
- EVALUATION：評価・不満・批判。ただし制裁までは行かない。
- SANCTION：非難・攻撃・通報・排除要求。
- DEFENSE：擁護・正当化・反論・保護。
- REPAIR：調停・説明・誤解修正・関係修復。
- PLAY：冗談・皮肉・ミーム・遊び。
- WITHDRAWAL：沈黙・回避・距離取り・離脱表明。
- META：議論そのものへの言及。
- AMBIGUOUS / RESIDUAL：主機能が判定不能、または既存分類に収まらない。

### Axis B: Target direction

発露がどこへ向かっているかを見る。

- OUTPUT：AI曲、画像、文章など生成物そのもの。
- TOOL / COMPANY：AIツール、AI企業、モデル。
- USER / CREATOR：AI利用者、AI作曲者、無名制作者。
- PLATFORM：Spotify、YouTube、SNS、配信平台。
- INSTITUTION：法律、著作権、規制、業界制度。
- AUDIENCE / COMMUNITY：リスナー、ファン、界隈、コミュニティ。
- SELF：自分の創作、自分の不安、自分の立場。
- FIELD / NORM：文化、音楽、創作倫理、場の規範。
- UNCLEAR：対象不明。

### Axis C: Routing / return loop

その発露が場の中でどう処理されたかを見る。

- AMPLIFIED：いいね、RT、引用、メディア化で増幅。
- CONTESTED：反論、議論、分岐。
- POLICED：通報、規約、モデレーション、規制要求へ。
- MEMEFIED：ネタ化、ミーム化、嘲笑化。
- NORMALIZED：当たり前の意見として定着。
- SILENCED：言いにくくなる、見えなくなる。
- IGNORED：戻り値がない、未完了化。
- REPAIRED：説明・対話で緩和。
- REDIRECTED：別対象へ矛先が移る。
- UNROUTED / RESIDUAL：処理されず残る。

### Axis D: Temporal state

時間的な変化を見る。

- ONE-SHOT：単発。
- REPEATED：反復。
- ESCALATING：不満→怒り→攻撃など増幅。
- COOLING：鎮静化。
- DRIFTING：論点・対象がズレる。
- FIXATING：ラベル・敵味方・規範として固定。
- SPLITTING：複数派閥・複数解釈へ分岐。
- RESIDUALIZING：主流から漏れて残差化。

### Axis E: Residual status

主パターンに吸収されなかったものを見る。

- BLUE_RESIDUAL：後で再接続可能な未固定痕跡。
- BURNING_RESIDUAL：負荷・沈黙・非承認・不可視労働として燃える。
- AMBIVALENT：興味と嫌悪、遊びと攻撃などが混ざる。
- SUPPRESSED：場の空気で出にくい。
- UNREADABLE：痕跡不足。
- OUTLIER：少数だが構造的に重要。
- NO_RESIDUAL_NOTED：特に残差なし。

---

## 7. 計測とラベリング

Crowd / Field Coreは、厳密な世論推定ではなく、観測された場における発露ベクトルの見え方を整理するための方法です。

そのため、数は少なくとも以下を分けて扱います。

- raw count：発露ベクトル数。
- actor count：ユニーク発話者数。
- visibility count：いいね、RT、引用、表示、メディア化などによる可視性。

visibility count は支持を意味しません。可視性は可視性であり、支持、同意、正しさとは分けて扱います。

### Count share label

観測場内での比率を、暫定的に次のようにラベル化します。

- DOMINANT：50%以上。
- MAJOR：25〜50%。
- SIGNIFICANT：10〜25%。
- MINOR：3〜10%。
- TRACE：1〜3%。
- SINGLETON：単発または1件。
- ABSENT / UNOBSERVED：観測なし。

サンプルが小さい場合は、割合よりも件数を優先します。

- SINGLETON：1件。
- SMALL_CLUSTER：2〜4件。
- CLUSTER：5〜9件。
- LARGE_CLUSTER：10件以上。

### Intensity label

- LOW：軽い言及、冗談、弱い不満。
- MID：明確な評価・不満・反論。
- HIGH：強い怒り、攻撃、排除要求。
- EXTREME：粘着、通報扇動、人格攻撃、炎上中心。

### Visibility label

- LOW_VIS：ほぼ広がらない。
- MID_VIS：ある程度反応がある。
- HIGH_VIS：引用・RT・議論化。
- PLATFORM_AMPLIFIED：platformやメディアに拾われた。

### Pattern label example

```text
MAJOR / HIGH intensity / USER-targeted SANCTION / AMPLIFIED / residual: AMBIVALENT
```

日本語例：

> 主要パターン：AI利用者向けの制裁・攻撃ベクトル。件数はMAJOR、強度はHIGH、platform上で増幅。残差として、興味・不安・遊びがAMBIVALENTに残る。

---

## 8. Crowd / Field Coreで検出しうるパターン

- Convergent pattern：複数ベクトルが同じ対象へ集まる。
- Target-drift pattern：発露対象がズレる。
- Escalation pattern：評価や不満が制裁・攻撃へ増幅する。
- Meme-conversion pattern：怒りや不満がPLAYへ変換される。
- Suppression pattern：特定の発露が出にくくなる。
- Residual cloud pattern：主パターン以外の小さな発露が残る。
- Fixation pattern：ラベルや敵味方が固定化する。

---

## 9. 非主張と注意

L7 Crowd / Field Core は、群衆の本心を読むモデルではありません。

次のような言い方は避けます。

- 群衆の本心はこれだ。
- 反AI感情の正体はこれだ。
- この界隈はこういう心理だ。
- この集団は怒りに支配されている。

L7 Crowd / Field Coreで言えるのは、次の範囲に限ります。

> 観測可能な発露ベクトルを重ねると、この場ではこの routing が優勢に見える。ただし、この優勢パターンはplatform可視性、増幅、沈黙、抑制、残差の影響を受けている。主パターンに吸収されない residual がある。

一文要約：

> L7 Crowd / Field Core は、群衆の本心を読むモデルではなく、単体発露ベクトルが場でどう再 routing され、どの可視パターンと残差を生むかを読むモデルである。

---

## 10. AI slopでの例示

この節は、L7 Minimum Core と Crowd / Field Core の読み方を示すための例示です。AI slop言説全体についての結論ではありません。

Minimum Coreでは、たとえば次のように見る。

```text
ある人が「AI slop」という語に触れる
→ 低品質・大量生成・盗用・不正・platform汚染などのsymbolが起動する
→ 不満・怒り・攻撃・嘲笑として発露する
→ AI企業、AI利用者、platform、制度へ向かう
→ いいね・反論・無視などの戻り値を受ける
→ routeが更新／固定化される
→ trace / Shiwa が残る
```

Crowd / Field Coreでは、たとえば次のように見る。

```text
複数の発露ベクトルがSNSやコミュニティ上で重なる
→ 「AI slop」というラベルが群衆的symbolとして固定化する
→ 怒り・嘲笑・攻撃が増幅される
→ 攻撃対象がAI企業からAI利用者、無名制作者、platformへズレる場合がある
→ 一方で、興味はあるが言えない人、遊びとして叩く人、ただ疲れている人、無名AI制作者側の困難などは主パターンから漏れる
→ それらを residual observation として別保持する
```

これは群衆心理の本質論ではなく、観測された発露ベクトルの routing である。

---

## 11. Internal examples と Paper candidates

HSSメモ内には、恋愛、信仰、カリスマ、欲求、動物、道具、創作キャラなどの例が出てくる場合があります。

これらは、L7 core の見え方を内部で確認するための例示素材です。論文材料ではありません。

扱い：

- INTERNAL_EXAMPLE：HSSメモ内に残す。論文輸出禁止または要審査。
- PAPER_CANDIDATE：観測可能なtrace、倫理、匿名化、HSS語彙が効く観測点テストを通過した場合のみ論文候補。
- CREATIVE_ONLY：創作側に置く。HSS論文には出さない。

論文候補としては、自己ログ、AI共同制作ログ、公開されたSNS反応の匿名化分析、査読コメントとresponse letterの差分などが比較的扱いやすい可能性があります。

---

## 12. 現時点での扱い

この文書は、L7予約層のうち、まずL7 Coreを整理するための補助メモです。

L8は引き続き予約層として扱います。L8は、身体性、欲求、快・不快、痛み、疲労、脳生理、衝動などの原動力側に近く、現時点では直接形式化しません。

L7についても、この文書は完成理論ではありません。観測可能な発露、routing、戻り値、trace、Shiwaとして扱える範囲に限定します。

最短整理：

> L7 Minimum Core は、一本の発露ベクトルを取る。
>
> L7 Crowd / Field Core は、そのベクトルが場でどう再 routing されるかを見る。
>
> L7は内面を当てる理論ではなく、入力・発露・戻り値・trace・Shiwaを観測する予約層の形式化メモである。
