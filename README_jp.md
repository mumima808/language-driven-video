# Language-Driven Video（日本語版）

> 動画は編集するものではない。言語からコンパイルされるものだ。

---

## 概要

Language-Driven Videoは、動画制作の新しいパラダイムです。

従来のようにタイムラインを手動で編集するのではなく、
動画を**構造化された言語（JSON）で記述し、コードとして実行し、最終的に動画として出力**します。

このアプローチにより、動画は「成果物」ではなく、**決定論的な実行結果**になります。

---

## クイックスタート（1コマンド）

```bash
npm install
npm run render -- --props=./episode.json
```

このコマンドは以下を実行します：

* `episode.json` を読み込む
* Reactコンポーネントに渡す
* フレームごとに実行する
* `out/video.mp4` を出力する

---

## 最小サンプル

### episode.json

```json
{
  "message": "こんにちは Language-Driven Video",
  "tone": "calm",
  "speed": 12
}
```

---

### Reactコンポーネント

```tsx
import { useCurrentFrame } from "remotion";

export const Scene = ({ message, speed }) => {
  const frame = useCurrentFrame();

  return (
    <div
      style={{
        fontSize: 64,
        textAlign: "center",
        marginTop: 200,
        opacity: Math.sin(frame / speed),
      }}
    >
      {message}
    </div>
  );
};
```

---

## 固定JSONスキーマ（v1）

最小限に保つことが重要です。ロジックは含めません。

```json
{
  "message": "string",
  "tone": "calm | energetic | serious",
  "speed": "number（アニメーション速度）"
}
```

### 設計ルール

* JSON = 意味（What）
* React = 挙動（How）

---

## コアコンセプト

```text
Language（JSON）
→ React（ロジック）
→ Time（フレーム実行）
→ Video（MP4）
```

動画とは：

> 時間を入力として実行される関数の結果である

---

## Text-to-Videoとの違い

| 種類                    | 説明            |
| --------------------- | ------------- |
| Text-to-Video         | AIがピクセルを生成する  |
| Language-Driven Video | コードがフレームを実行する |

> AIは「想像」する
> この仕組みは「実行」する

---

## アーキテクチャ

### 1. 言語レイヤー

意味を定義（episode.json）

### 2. レンダリングレイヤー

挙動を定義（React）

### 3. 実行レイヤー

フレーム単位で評価

```text
t = 0 → UI  
t = 1 → UI  
t = 2 → UI  
```

### 4. 出力レイヤー

MP4として書き出し

---

## 何が可能になるか

* テンプレートベースの動画生成
* 大量生成（1本 → 1万本）
* Gitによるバージョン管理
* n8nなどとの自動化連携

---

## ポジショニング

Language-Driven Videoは以下の中間に位置します：

* 従来の動画編集ツール
* AIによる動画生成

そして新しいカテゴリを定義します：

> **プログラマブル動画生成**

---

## 今後の方向性

* 動画専用DSL（ドメイン固有言語）の設計
* AIによるJSON生成
* リアルタイムレンダリング
* 分散型動画生成システム

---

## まとめ

従来の動画編集：

* 手作業
* 再現性が低い
* スケールしない

Language-Driven Video：

* 決定論的
* スケーラブル
* プログラム可能

---

## 最後に

もし動画制作が「職人技」だったとするならば、

AI動画は「想像力」であり、
Language-Driven Videoは：

> **実行である。**
