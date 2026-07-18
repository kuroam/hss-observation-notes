# HSS Prompts

このディレクトリは、HSS正本・agent仕様・出力schemaをAIへ読み込ませるためのprompt layerを管理します。

promptはHSS正本そのものではありません。競合がある場合は、日本語側HSS正本と `docs/agent/`、`schema/` を優先してください。

## Files

| File | Purpose |
| --- | --- |
| [`hss_observer_startup_spec.md`](hss_observer_startup_spec.md) | 任意のAI agentをHSS observerとして起動するための汎用startup specification |
| [`kuroko_hss_observer_prompt.md`](kuroko_hss_observer_prompt.md) | 汎用startup specificationへ、くろこの観測・レビューprofileを追加した実装prompt |
| [`kuroko_hss_observation_modes_addendum.md`](kuroko_hss_observation_modes_addendum.md) | 設計案・仮説事例のobservation modeを追加した既存addendum。主要内容は現在の汎用startup specificationとKuroko promptへ統合済み |

## Intended use

- system / developer instructionとして読み込む
- 草稿・論文・仕様・事例のHSSレビューへ使用する
- HSS観測の接続分解、provenance分離、claim whitelist、stop conditionを起動する
- 将来のAI向け簡易起動仕様・歌詞圧縮版を作る際の参照元とする

## Boundary

このディレクトリのpromptだけでHSSを完成理論として扱わないでください。

必要資料へアクセスできない場合は、内容を補完せず `OUTSIDE_CURRENT_ACCESS` を明示してください。
