# meet-live

TSG LIVE! 5 (フルリモート開催) にて、各自の画面を映し出すために使った Electron アプリ。
Slack の slash command による遠隔操作機能つき。

## 機能

* Jitsi に参加している人々の画面共有を表示する
* 画面共有をフルスクリーンで表示し、その他余計なものは非表示にする
* #003F00 を背景にし、グリーンバック処理を易しくする
* 誰の画面共有を表示するかを `/focus [ユーザ名]` で操作できる
* `/focus mute`, `/focus unmute` でミュート/ミュート解除できる
* `/focus` 空打ちで、現在 focus があたっている人や参加者の一覧を知ることができる

## 使い方

1. Jitsi にてミーティングを作成
1. `cp .env.example .env` → .env を適当に編集
1. `npm run start`
1. マイク、カメラを不使用にした上で、起動して10秒以内に参加。
1. 起動の10秒後に、focus コマンドを受け取るサーバーが立ち上がる。
1. ポートを開放し、Slack の slash command リクエストを受け取れるようにする。TLS 必須なのがめんどい。hideo54 は雑に ngrok でなんとかしちゃった。

ここまでできたら、OBS のウィンドウキャプチャでエイヤっとすればよいぞ。

## 課題

* 本当に Slack からのリクエストかを validate する処理を書いていなくてやべ〜
* チャンネル制限をしていないので、悪意ある TSGer が sandbox でおもちゃにし始めると放送が崩壊する