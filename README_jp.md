Language-Driven Video（日本語）

動画は編集するものではない。言語からコンパイルされるものだ。

概要

Language-Driven Videoは、動画制作の新しい考え方です。

動画をタイムラインで編集するのではなく、
構造化された言語（JSON）で記述し、コードとして実行し、動画として出力します。

クイックスタート（1コマンド）
npm run render -- --props=./episode.json

この1行で：

JSONを読み込み
Reactに渡し
フレームごとに実行し
MP4を書き出します
最小サンプル
episode.json
{
  "message": "こんにちは",
  "tone": "calm",
  "speed": 12
}
コンポーネント
const frame = useCurrentFrame();

<div style={{ opacity: Math.sin(frame / speed) }}>
  {message}
</div>
固定スキーマ（v1）
{
  "message": "文字列",
  "tone": "calm | energetic | serious",
  "speed": "数値"
}
設計思想
JSON = 意味
React = 挙動
動画 = 時間実行の結果
本質
JSON → React → 時間 → 動画

👉 動画とは「時間で実行される関数」

何が変わるのか

従来：

手動編集
再現性が低い
スケールしない

これから：

決定論的
大量生成可能
Git管理可能
ポジション

これはAI動画ではありません。

👉 プログラマブル動画生成

まとめ

編集から実行へ。
動画は成果物ではなく、計算結果になる。
