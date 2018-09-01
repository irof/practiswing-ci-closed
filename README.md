PRACSWING-CI
============================================================

## Circle CI (2018-09-01)

`.circleci/config.yml` に記述。


### badge

`Notifications/Status Badges`でコードが生成できる。
必要に応じて変更するとよい。

`Build Settings/Advanced Settings/Free and Open Source`がONだったらトークンなくても表示できる。
OFFだったら`circle-token`をパラメーターに指定してあげる必要がある。

Free and Open Sourceはコンテナ3つ追加で使える（合計4つ）。
OFFにしたらひとつになる。


## Travis CI (2017-04-06)

[![Build Status](https://travis-ci.org/irof/practiswing-ci.svg?branch=master)](https://travis-ci.org/irof/practiswing-ci)

設定は`.travis.yml`に書く。
[Travis CI](https://travis-ci.org/)のリポジトリで登録するだけだと何も起こらず、`.travis.yml`をpushするとビルドが始まった。
登録前から`.travis.yml`を置いてたら登録した瞬間にビルドするかも。知らんけど。

WebUI上の設定はCircle CIに比べると少なめな印象。
BETAで[Cron Jobs](https://docs.travis-ci.com/user/cron-jobs/)がある。面白そう。

Gradleプロジェクトだとデフォルトで`./gradlew assemble`と`./gradlew check`が叩かれる。
`check`はあまり使わないけれど、ようするに`test`タスクにプラスアルファしたもの。
詳細は[Gradleのドキュメント](https://docs.gradle.org/current/userguide/java_plugin.html#sec:java_tasks)を見よう。
ちなみに`assemble`と`check`を組み合わせるタスクが`build`なので、手元で`./gradlew build`とするのと同等のことが実行されると思ってよさげ。

