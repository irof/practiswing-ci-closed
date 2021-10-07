PRACSWING-CI
============================================================

## GitHub Actions (2019-10-23)

![](https://github.com/irof/practiswing-ci/workflows/Java%20CI/badge.svg)

## Circle CI (2018-09-01)

`.circleci/config.yml` に記述。


### GitHubにpush

CircleCIと連携時に自動的に登録されるSSHキーはRead Onlyになっているので、そのままだとCircleCIからGitHubにpushできない。

別の秘密鍵を作成し、GitHubとCircleCIにそれぞれ登録する。

- GitHub
  - `Settings/Deploy keys`
    - `Add deploy key` から `Arrow write access` を選択して公開鍵を登録。
    - 自動登録されたReadOnlyの鍵は削除する。
- CircleCI
  - `Permissions / SSH Permissions`
    - `Add SSH Key` からHostnameは `github.com` として秘密鍵を登録。
  - `Permissions / Checkout SSH keys`
    - 自動登録されたdeploy keyを削除する。
      - これを削除しないと登録したものが使用されない。

もしくは [`add_ssh_keys`で登録した鍵を指定する](https://github.com/irof/practiswing-ci/blob/34ec5b357b99a61c65f87a0d699a4cc8183b8992/.circleci/config.yml#L7-L9)。
自動登録された鍵を削除してしまうとCircleCIの画面に鍵登録を促すボタンが出るので削除したくないが、config.ymlにfingerprintを書くのもどうなの感がある。

### badge

[![CircleCI](https://circleci.com/gh/irof/practiswing-ci.svg?style=svg)](https://circleci.com/gh/irof/practiswing-ci)

`Notifications/Status Badges`でコードが生成できる。
必要に応じて変更するとよい。

`Build Settings/Advanced Settings/Free and Open Source`がONだったらトークンなくても表示できる。
OFFだったら`circle-token`をパラメーターに指定してあげる必要がある。

## AppVeyor (2019-05-25)

[![Build status](https://ci.appveyor.com/api/projects/status/eailckd07qhjm7q9?svg=true)](https://ci.appveyor.com/project/irof/practiswing-ci)

