# md2googleslides trial

## 導入

### 導入ガイド

[https://github.com/googleworkspace/md2googleslides](https://github.com/googleworkspace/md2googleslides)
こちらにインストールガイドがあります。

なお、Node.js 16.14.2 で試しています。

### 重要な情報へのアクセスと言われてアクセスがブロックされた

[issue95](https://github.com/googleworkspace/md2googleslides/issues/95) を参考に対応を試みている。

#### clientId と clientSecret を書き換える？

[issue95](https://github.com/googleworkspace/md2googleslides/issues/95#issuecomment-858729913)にはそのような手順が提案されている。
これを試した所 "このアプリは、アプリの保護に関して Google の OAuth 2.0 ポリシーを遵守していないため、ログインできません。" と言われて不可。

![得られた警告](./pics/unobeied_to_oauth20policy.png)

ただ、これってアプリ側なのか API 周りの設定が悪いのかはまだ良くわかってない。

### ソースコードが古いのでは

[issue95](https://github.com/googleworkspace/md2googleslides/issues/95#issuecomment-924181932)にソースコードが古い旨が書かれている。
ソースコードを clone した上で `npm run compile` してみた。`npm run compile` するにはいくらかのものをインストールする必要があるのでそれは注意が必要。

必要そうなものをインストールした上で実行した所
`Argument of type '() => Chai.Assertion' is not assignable to parameter of type 'ProvidesCallback | undefined'.` および
`Argument of type '() => Chai.PromisedAssertion' is not assignable to parameter of type 'ProvidesCallback | undefined'.` が大量に出て失敗する。

ないし、master ブランチの最新版を手動で適用するでも良いとのことだが、それだと上述の OAuth 2.0 ポリシーのアラートが発生して上手くいかなかった。

## 懸念点

### メンテされてなくね？


はい（はい）