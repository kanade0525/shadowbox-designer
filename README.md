# シャドーボックス設計図メーカー

カードやイラストの画像から、シャドーボックス（重ね切り絵）の層ごとの切り出しガイドと、3D の完成イメージを作るブラウザアプリです。

**公開ページ：** https://kanade0525.github.io/shadowbox-designer/

## できること

- 画像を自動でパーツに分解し、タップで「この部分は2枚目」「ここは3枚目」と層に振り分け
- 囲み選択・ブラシ・輪郭吸着（OpenCV.js の GrabCut、未読込時は簡易モードに自動フォールバック）での細かい調整
- 層ごとの切り出しガイドを表示・画像で保存
- 層の間隔を変えながら 3D で完成イメージを確認

## 使い方

公開ページを開いて画像を選ぶだけです。手元で動かす場合は、クローンして `index.html` をブラウザで開くか、簡易サーバーを立ててください。

```
git clone https://github.com/kanade0525/shadowbox-designer.git
cd shadowbox-designer
python3 -m http.server 8000   # → http://localhost:8000
```

## 画像の扱い

選んだ画像はブラウザの中だけで処理され、サーバーには送信されません。アップロード先もログもありません。

## 構成

単一の `index.html`（ビルド不要）。外部から読み込むのは以下だけです。

| 読み込み先 | 用途 |
| --- | --- |
| cdnjs.cloudflare.com | three.js r128（3D プレビュー） |
| cdn.jsdelivr.net | OpenCV.js 4.12（輪郭吸着・任意） |
| fonts.googleapis.com / fonts.gstatic.com | Dela Gothic One, Zen Kaku Gothic New |

## 状態

試作版です。仕様・設計資料は社内で別管理しています。
