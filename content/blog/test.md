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

# 感想
めっちゃ簡単で嬉しい、あとやっぱ文章書くならmdなのでね、そこも嬉しいすね

