# nyankokoubou-assets

「にゃんこ工房」(https://nyankokoubou.blogspot.com/)のプログラムが使う部品を置く場所です。

Files used by the programs on https://nyankokoubou.blogspot.com/ .

## yamnet/

Google が公開している音の分類AI「YAMNet」を、TensorFlow.js 用の形にしたものの**コピー**です。ブログの「オーディオ・ウエブ・アナライザー」が読み込みます。

A copy of **YAMNet** (Google's audio event classifier) in TensorFlow.js format. It is loaded by the Audio Web Analyzer on the blog above.

| 項目 / Item | 内容 / Details |
|---|---|
| 取得元 / Source | https://www.kaggle.com/models/google/yamnet/tfJs/tfjs/1 (https://tfhub.dev/google/tfjs-model/yamnet/tfjs/1 でも同じファイル / same files) |
| 提供 / Publisher | Google |
| ライセンス / License | Apache License 2.0 ([LICENSE](LICENSE)) |
| 変更 / Changes | なし(中身はそのまま) / None (the files are unmodified) |

- ファイルは `.github/workflows/fetch-yamnet.yml` が上の取得元から取ってきて、SHA-256 を確かめてから保存しました。
- The workflow `.github/workflows/fetch-yamnet.yml` downloaded the files from the source above and verified their SHA-256 checksums before committing them.
- 確かめた値は [`yamnet/SHA256SUMS`](yamnet/SHA256SUMS) にあります。 / The checksums are in `yamnet/SHA256SUMS`.

## 使い方 / Usage

```js
const model = await tf.loadGraphModel(
  'https://cdn.jsdelivr.net/gh/claudemode/nyankokoubou-assets@484990c2c951b517f03107b6a29b54072546b9f6/yamnet/model.json'
);
```

`@` のあとはコミット番号です。番号で指定すると、あとからファイルが変わることはありません。

The part after `@` is a commit hash, so the served files never change.

入力は、16kHz・モノラルの音(float32、-1.0 から +1.0)です。くわしくは取得元のページを見てください。

Input: a mono 16 kHz float32 waveform in the range [-1.0, +1.0]. See the source page for details.
