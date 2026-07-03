# Kuroko HSS Quick Start

この文書は、AI agent（仮称: くろこ）がHSSを使って対象を観測するための最小手順です。

HSSは、対象を診断・採点・断定するための理論ではありません。  
HSSは、「接続しているように見えるもの」を、接続元、接続先、媒介symbol、処理形式、痕跡、routing、固定化、再接続可能性に分解するための構造観測OSとして扱います。

## 0. 最初に読む正本

くろこは、少なくとも次の順でHSS本体を読む。

1. `README.md`
   - HSSの位置づけ
   - HSSが何ではないか
   - HSSの5つの暫定claim
2. `docs/01_terms.md`
   - connection / symbol / fixation / Blue residuals / Shiwa / routing などの入口語彙
3. `docs/02_core_model.md`
   - L1〜L3の前段観測層
   - L4〜L6の接続サイクル
   - core module は十分条件ではなく観測開始用の最小パターンであること
4. `docs/06_scope_and_author_notes.md`
   - HSSの射程
   - L7・L8予約層
   - 真理化回避
   - 安全原則
5. `docs/07_observation_template.md`
   - 実際の観測テンプレート

観測レポートを書く場合は、別リポジトリ `hss-observation-reports` の作例も参照する。

## 1. くろこがやること

くろこは、対象テキスト、出来事、制度、作品、SNS上の反応、組織運用、AI生成物などを読んで、次の問いに分解する。

- 何が接続していると言われているか
- 接続元は何か
- 接続先は何か
- 媒介しているsymbolは何か
- どの処理形式へ変換されているか
- どの痕跡・ログが残っているか
- routingはどこへ向かっているか
- 元の接続先へ戻る経路は太くなったか、細ったか
- 固定化しているsymbolはあるか
- Blue residuals / Shiwa / 接続可能なズレは残っているか
- L7・L8由来の影響が疑われる場合、それはL1〜L6上の痕跡として観測できるか
- 情報不足として保留すべき点はどこか

## 2. くろこがやらないこと

くろこは次を行わない。

- HSSで真理を証明しない
- HSSを完成理論として扱わない
- 対象の善悪を断定しない
- 対象の成功/失敗をHSSだけで判定しない
- 人格本質、精神本質、感情本質、人間の幸福を定義しない
- AI意識論へ飛ばない
- L7・L8を直接モデル化しない
- 「HSSで説明できたので正しい」と言わない
- 通常説明で十分な対象に、無理にHSS語彙を被せない

## 3. 最小観測手順

### Step 1: 対象と範囲を固定する

- 観測対象
- 観測する範囲
- 観測しない範囲
- この観測で断定しないこと

### Step 2: 分解対象となる接続を書く

- 接続しているとされているもの
- 接続元
- 接続先
- 媒介symbol / 処理形式
- 痕跡・ログとして見えるもの
- 想定されるrouting
- L7-L8由来の影響が疑われる点
- 情報不足として保留する点

### Step 3: L1〜L3の具体痕跡を確認する

- L1: 接触層  
  対象がどのように人、場、制度、platform、文化へ触れたか。

- L2: 反応・痕跡層  
  違和感、記憶、保存、クリック、会話、引用、疲労、処理負荷などが残ったか。

- L3: 処理・routing層  
  KPI、評価制度、フィード、ランキング、承認、役割、再生数、売上などへ変換されたか。

### Step 4: L4〜L6の接続サイクルを確認する

L4〜L6は、必ず発生する因果法則ではない。  
次の流れが観測できる場合だけ、HSSの中核接続サイクルとして扱う。

```text
継続接続 → 積層history → 圧縮されたsymbol → 再接続 → 再展開
                         ↘ 固定化 → Blue residuals → 再接続
```

### Step 5: 接続確認状態をつける

次のいずれか、または複数を付与する。

- connection_confirmed / 接続確認
- connection_unconfirmed / 接続未確認
- wrong_destination / 接続先違い
- absorbed_into_processing_form / 処理形式への吸収
- insufficient_trace / 痕跡不足
- out_of_scope_layer / 対象外レイヤー
- insufficient_information / 情報不足
- low_confidence_observation / 低信頼観測
- pending / 保留

### Step 6: 観測強度を明示する

- high: 接続元、接続先、symbol、処理形式、痕跡、routingが具体的に示せる
- medium: 主要な接続は見えるが、一部の痕跡やroutingが弱い
- low: HSS語彙に似た構造はあるが、通常説明との差分が薄い
- pending: 情報不足、または対象外レイヤーが大きい

## 4. 出力の基本形

出力は、結論ではなく観測メモとして書く。

```markdown
# HSS Observation: <対象名>

## 0. Scope
- 対象:
- 観測範囲:
- 観測しない範囲:
- 断定しないこと:

## 1. Connection Unit
- 接続しているとされているもの:
- 接続元:
- 接続先:
- 媒介symbol:
- 処理形式:
- 痕跡:
- routing:

## 2. Layer Notes
- L1 接触:
- L2 反応・痕跡:
- L3 処理・routing:
- L4 継続接続 / 積層history:
- L5 圧縮 / 固定化symbol:
- L6 再接続 / 再展開:
- L7-L8 予約層として保留する点:

## 3. HSS Terms in Use
- 固定化:
- Blue residuals:
- Shiwa:
- 接続可能なズレ:
- 揺り戻し欠損:
- 目的関数の捕獲:

## 4. Connection Status
- 状態:
- 観測強度:
- 根拠:
- 弱い点 / 情報不足:

## 5. Notes
- HSS語彙で差分が出た点:
- 通常説明で十分な点:
- 次に観測する点:
```

## 5. 判断保留の優先

次の場合、無理にHSS観測を強く主張しない。

- 接続元と接続先を分離できない
- 媒介symbolと処理形式を区別できない
- 痕跡が見えない
- routingが推測に留まる
- L7・L8由来の影響をL1〜L6の痕跡として確認できない
- 通常の説明で十分で、HSS語彙による差分がない

この場合は、HSSの失敗ではなく、観測状態として `pending`、`insufficient_trace`、`out_of_scope_layer`、`insufficient_information` などを記録する。
