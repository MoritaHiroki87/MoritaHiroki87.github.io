+++
title = 'My First Post!'
date = 2023-09-14T08:17:30+09:00
draft = false
+++

# これはなに
えー、技術ブログをそろそろ作るか〜〜って思ってたところ、hugoとgithub.ioで簡単にできると知ったためやってみたよという記事です。

# やってみた手順
基本的に以下のページを参考に進めた。やり方はリンク先見てくれればそれでOK、詰まった箇所だけ記載する。
https://dampgblog.hinohikari291.com/hugo-github-mac/

## ちょっとつまづいた箇所
### テーマの取得
テーマのサイトが紹介されてるんですが、サイトのどこからgithubページに移動できるのかわかんなくてちょっと詰まった
結論としては個別のテーマのページからdownloadボタンでいけた。

### git submodule add コマンド
初めて使ったのでめっちゃ打ち間違えた

### config.toml
デフォルトだとなくて、hugo.tomlがあるのみ。
とりあえずそこかな〜〜と思ってhugo.tomlに設定を書いてたんだけど、その後ビルドしようとしたところで設定ファイルないから新しくサイト作り直せや！　みたいな過激派エラーに遭遇した。
```
Error: Unable to locate config file or config directory. Perhaps you need to create a new site.
Run `hugo help new` for details.
```

対策は以下のページを参考にしようかな？　と思ったんだけど、hugo.tomlが何かに使われてたらいやだし、まあ一旦別のconfファイル作るかってなった
https://zenn.dev/shotakaha/scraps/1075f3199aa570

で、今度は以下のエラー
```
Error: error building site: render: failed to render pages: render of "section" failed: "/Users/hirokimorita/work/MoritaHiroki87.github.io/themes/resume/layouts/_default/section.html:9:11": execute of template failed: template: _default/section.html:9:11: executing "main" at <partial (printf "%s%s" .Type "Summary") .>: error calling partial: partial "postSummary" not found
```

調べてみると、以下のページがヒットした。
https://github.com/eddiewebb/hugo-resume/issues/30

どうやら使ってるtheme固有のエラーで、記事を突っ込んでるフォルダの名前が間違っているらしい。なるほどね。

# テーマ設定
どうやら、このresumeってテーマはサクッと立ち上げができないっぽい。ReadMe読んでもquick startみたいなのはないから、サンプルプロジェクトを見ながらどこが違うのかを確かめていく。。もしくはもう別のテーマにしちゃうかだなあ。
→テーマ切り替えてとりあえず使えるようにしよう。

### テーマ切り替え
他のテーマを落としてきてビルドをしてみても、テーマが切り替わらない
これはconfig.tomlだけ変更してもダメみたい。hugo.tomlも一緒に変えたら反映できた。
→どうもhugo.tomlを見てるっぽい。。どういうことだ。。

### Githubのトークン設定
古い古いリポジトリだったのでトークン設定をしてなかった。のでした。

### githubpages上では別のテーマになる
なぜかうまく行ってなかったresumeのテーマになっちゃってた。configはpaperModなんだけど。。
→hugoコマンドでビルドし直したらうまく行った。どのタイミングでthemeが変わってるのかちょっとわかんないなあ。これエンジニア以外だとまじで辛いだろうな。。


# 感想
とりあえず公開できたのでGood
使ってるgithubアカウント、昔から持ってる変なやつなので、これを機に新しく取り直してもいいかもなと思うなど。
以上！

## 課題
とりあえず、課題がいくつかあるな〜〜と思うのでメモ

- mdのなんだ？　ローカルバージョンみたいなのがおそらく違ってて、改行してほしいところで改行してない
- ローカル開発環境整備
    - VSCでブログ書いてサクッとデプロイ、としたいんだけど、VSCのgitプラグインを入れてないのでそこら辺がスムーズにいかない
    - あとgithubのなんだ？　あの〜〜認証まわりがぐだぐだになってるので整備したほうがいい
    - VSCでもそこらへんのを環境変数に設定していい感じにしたほうがいい
- hugo自体
    - config.tomlとhugo.tomlの違いを理解する
    - 他のテーマを使えるようにしたい、今のやつはちょっとなんかもうちょいな感じがある
        - 具体的には行間がつまり過ぎているとか
        - あとまあ最終的にはポートフォリオ的なものにもなっててほしいし、一旦はあの諦めたresumeテーマを使えるようにしようかな
- ブログの投稿ルーチン
    - 投稿の流れとして、普段はNotionでまとめてそれをコピペして技術ブログとして公開する予定
    - ここ、多分APIとか叩いたら自動化できるんじゃないかなあ
        - もしくは、GithubActions押すとNotionに取りに行ってくれて更新されるとか。。
        - こういう改善点を思いついてやろうと思えるの、現職での経験がだいぶでかいので本当にマジでマジで現職には感謝しております

## 今後の予定
- ローカル環境整備
    - VSCの整備
    - git関連のプラグインを入れて、スムーズにpushできるようにする
- hugo
    - 設定ファイルの謎をとく
    - resumeテーマを使えるようにする
- ブログ投稿の簡易化
    - Github Actionsとかで簡単に投稿できるようにする

よっしがんばります！