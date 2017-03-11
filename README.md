PRACSWING-CI
============================================================

## Circle CI

[![CircleCI](https://circleci.com/gh/irof/practiswing-ci.svg?style=shield)](https://circleci.com/gh/irof/practiswing-ci)

### ビルド結果の収集

[ドキュメントに記載されている](https://circleci.com/docs/1.0/test-metadata/#gradle-junit-results)のをコピペ。

・・・するだけだと、テスト結果の収集に失敗する。（The following errors were encountered parsing test results:）
CircleCIが持っているgradleの出力するXMLを自分でパースできてない模様。
Gradle Wrapperを追加したらいけた（出力されるXMLが若干変わる）。

`test.override` はテストの実行が以下のように、`gradlew`があれば使用されるようになっているので不要。
```
if [ -e ./gradlew ]; then ./gradlew test;else gradle test;fi
```

これで *Test Summary* タブにテストの件数と落ちたテストの`testsuite.testcase.failure`が出力されるようになる。
あくまでサマリ表示用。

### 成果物の収集

`general.artifacts`に`/home/ubuntu/{base_dir}`以下の相対パスを記述すると、ディレクトリそのまま持っていってくれる。
GradleのテストレポートはCSSとかもまとめて欲しいので。

