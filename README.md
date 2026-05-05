# Language-Driven Video

> Video is no longer edited. It is compiled from language.

---

## Overview

Language-Driven Video is a new paradigm for creating video.

Instead of editing timelines manually, videos are **described as structured language**, executed as code, and compiled into final outputs.

---

## Quick Start (1 Command)

### 1. Install

```bash
npm install
```

### 2. Generate video (one command)

```bash
npm run render -- --props=./episode.json
```

👉 This command:

* loads `episode.json`
* injects it into React components
* renders all frames
* outputs `out/video.mp4`

---

## Minimal Example

### episode.json

```json
{
  "message": "Hello Language-Driven Video",
  "tone": "calm",
  "speed": 12
}
```

---

### React Component

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

## Fixed JSON Schema (v1)

Keep it minimal. No logic inside.

```json
{
  "message": "string",
  "tone": "calm | energetic | serious",
  "speed": "number (animation speed)"
}
```

### Design Rule

* JSON = meaning only
* React = behavior only

---

## Core Concept

```text
Language (JSON)
→ React (Logic)
→ Time (Frame execution)
→ Video (MP4)
```

A video is:

> A function executed over time.

---

## Not Text-to-Video

| Type                  | Description         |
| --------------------- | ------------------- |
| Text-to-Video         | AI generates pixels |
| Language-Driven Video | Code renders frames |

> AI imagines.
> This system executes.

---

## Architecture

### 1. Language Layer

Defines meaning (episode.json)

### 2. Rendering Layer

Defines behavior (React)

### 3. Execution Layer

Frame-by-frame evaluation

```text
t = 0 → UI  
t = 1 → UI  
t = 2 → UI  
```

### 4. Output Layer

MP4 export

---

## What This Enables

* Template-based video generation
* Batch generation (1 → 10,000 videos)
* Git-based version control
* Automation pipelines (n8n etc.)

---

## Positioning

> Programmable Video Generation

Between:

* Video editing tools
* AI video generation

---

## Future

* DSL for video
* AI-generated JSON
* Real-time rendering
* Scalable pipelines

---

## ---- 日本語版 ----

# Language-Driven Video（日本語）

> 動画は編集するものではない。言語からコンパイルされるものだ。

---

## 概要

Language-Driven Videoは、動画制作の新しい考え方です。

動画をタイムラインで編集するのではなく、
**構造化された言語（JSON）で記述し、コードとして実行し、動画として出力します。**

---

## クイックスタート（1コマンド）

```bash
npm run render -- --props=./episode.json
```

この1行で：

* JSONを読み込み
* Reactに渡し
* フレームごとに実行し
* MP4を書き出します

---

## 最小サンプル

### episode.json

```json
{
  "message": "こんにちは",
  "tone": "calm",
  "speed": 12
}
```

---

### コンポーネント

```tsx
const frame = useCurrentFrame();

<div style={{ opacity: Math.sin(frame / speed) }}>
  {message}
</div>
```

---

## 固定スキーマ（v1）

```json
{
  "message": "文字列",
  "tone": "calm | energetic | serious",
  "speed": "数値"
}
```

---

## 設計思想

* JSON = 意味
* React = 挙動
* 動画 = 時間実行の結果

---

## 本質

```text
JSON → React → 時間 → 動画
```

👉 動画とは「時間で実行される関数」

---

## 何が変わるのか

従来：

* 手動編集
* 再現性が低い
* スケールしない

これから：

* 決定論的
* 大量生成可能
* Git管理可能

---

## ポジション

これはAI動画ではありません。

👉 **プログラマブル動画生成**

---

## まとめ

編集から実行へ。
動画は成果物ではなく、**計算結果**になる。
