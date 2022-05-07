---
marp: false
theme: hiyoko
paginate: true
---

# Marp trial

---

## What's this

marp でスライドを作ってみた話を書いていく

---

### なんでそんなことを

普通に Google Slide や Power Point でいいのでは？
→既存のドキュメントをそのまま PPTX で欲しいという謎要望への対応

Google Docs で作っているドキュメントを PPTX に置換するのはそれなりに骨
→**マークダウンから Google Docs と同等のものと PPTX の双方を出力！**

---

### やることを図解するとどうなる？

こうなる。

![マークダウンを謎プロセスに打ち込んで必要なものを生成](./pics/howToGenerateDestination.drawio.png)

---

## 導入手順

1. VS Code を入れる
2. VS Code に拡張機能 `Marp for VSCode` を入れる
3. (推奨) VS Code 拡張機能 `Draw.io Integration` を入れる
4. マークダウンファイルを編集する
5. 設定を適切に変更する
6. 出力する

---

### VS Code を入れる

割愛。
[こちら](https://azure.microsoft.com/ja-jp/products/visual-studio-code/)とかから導入

---

### 拡張機能を入れる(Marp for VSCode)

左のメニューから拡張機能を導入。
![Marp for VSCode](./pics/howToInstallMarpForVSCode.png)

---

### 拡張機能を入れる(Draw.io Integration)

左のメニューから拡張機能を導入。
製図に便利なのでほしいなら。
![Draw.io Integration](./pics/howToInstallDraw.io_Integration.png)

---

### マークダウンファイルを編集する

[README.md](./README.md)みたいに編集する

---

### マークダウンファイル編集の注意点1 先頭に挿入

先頭に以下の呪文を入れる必要あり

```
---
marp: true
---
```

---

### マークダウンファイル編集の注意点2 改ページ

3つハイフンで改ページ

```
---
```

---

### Marp for VS Code の設定を変える

デフォルトだと PDF 出力なので吐かせ方を任意に変更
拡張機能の一覧から設定を開けるのでそちらから実施

![設定変更](./pics/howToConfigurateMarpForVSCode.png)

---

### ビルドする

右上のサンドイッチめいたアイコンをクリック後、
Export Slide Deck... をクリック

---

## テーマを変更する

CSS でテーマ（見た目）を指定できる。

---

### CSS を作成する

[公式のガイド](https://marpit.marp.app/theme-css)を参考に。
以下のようにテーマの名前を入れないと動かないので注意。

```
/* @theme theme-name */
```

---

### 他のテーマを読み込む

CSS 内で `@import` することで他のテーマを読み込める。

```
@import 'gaia'
```

---

### ビルドする時に CSS を読み込む

これが難しいので注意。
設定の `Markdown > Marps:Themes` に対象の CSS のパスを入れる。
ワークスペースのルートからのパスを入れる必要があるので注意。

---

### 設定例

```
/(ワークスペースのルート)
└markdownToDocuments
　└marp_trial
　　├README.md
　　└css
　　　├basic.css
　　　└hiyoko.css
```
ならば以下2行を入れる
```
./markdownToDocuments/marp_trial/css/hiyoko.css
./markdownToDocuments/marp_trial/css/basic.css
```

---

### CSS の Tips

HTML を生成した後それを元に PDF や pptx を生成しているようなので
HTML を生成してその構造を確認しながら CSS を書くのが吉っぽい。

---

### 生成された HTML のサンプル

[hiyoko.css](./css/hiyoko.css)を読み込んでこの[README.md](./README.md)をビルドした例：[OUTPUT_SAMPLE.html](./OUTPUT_SAMPLE.html)

### 課題

HTML をまず生成した後、それをプリントアウトするようにして PDF や PPTX を生成しているようだ。
そのためか、生成された PPTX はページ全体が1つの画像となっており、再編集ができない。

すなわち、最初に挙げた謎要望が「再編集不能な PDF ではなく再編集可能な PPTX で」であれば
このアプローチは上手くいかない。
