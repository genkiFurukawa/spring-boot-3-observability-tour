# オブザーバビリティツアーガイド ミドルウェアセットアップ

## 概要

- [Spring Boot 3.0 オブザーバビリティツアーガイド](ttps://www.youtube.com/live/yjJ1jyvEaOI?feature=share)の勉強用のリポジトリ
- オブサーバビリティもロギングツールやトレーシングツールやメトリクスツールを使ったことない人間が勉強するためのリポジトリ
- `Spring Boot 3.0 オブザーバビリティツアーガイド`ではミドルウェア部分のセットアップができている前提でのデモだったので、ミドルウェアのセットアップの備忘録

### 関連リンク

- [GitHub](https://github.com/hainet50b/jsug-seminar-2023-02)
- [アーカイブ動画](https://www.youtube.com/live/yjJ1jyvEaOI?feature=share)
- [SpeakerDeck](https://speakerdeck.com/hainet50b/spring-boot-3-dot-0-obuzababiriteituagaido)

## 動かし方

### アプリ側

1. [GitHub](https://github.com/hainet50b/jsug-seminar-2023-02)をクローンし、フォルダごとに（`payment-gateway`・`qr-service`・`credit-service`・`log-ingester`の 4 つ） InteliJ で開き、アプリを起動する
1. ログの出力場所をメモしておく（ミドルウェア側を動かす時に使う）

### ミドルウェア側

1. `docker-compose.yml`の`filebeat`の`volumes`のパスをメモした場所に書き換える
1. 下記のコマンドを実行する

```sh
# 起動
$ docker-compose up -d
# ステータス
$ docker-compose status
# 停止
$ docker-compose stop
```

## メモ

- Kibana 8.8 系だとデモ動画と見た目が異なり、ログファイルの出力の確認方法が分からなかったので、7.10 系を採用

## 参考

- [《滅びの呪文》Docker Compose で作ったコンテナ、イメージ、ボリューム、ネットワークを一括完全消去する便利コマンド](https://qiita.com/suin/items/19d65e191b96a0079417)
  - Elastic Stack の 8 系から 7 系にするときにボリュームのファイルの影響かミドルウェアが起動しなくなったので、ここを参考に一括削除した
