---
title: Vagrant環境構築メモ
---

参考URL
=======

- http://qiita.com/gangimo/items/115378b2fd160e52e4ce
- http://www.symmetric.co.jp/blog/archives/533
- http://knowledge.sakura.ad.jp/tech/1552/


Virtualboxインストール
======================

- インストーラを下記ページからダウロードしてインストール
  - https://www.virtualbox.org/wiki/Downloads


Vagrantインストール
===================

- インストーラを下記ページからダウロードしてインストール
  - http://www.vagrantup.com/downloads.html


Boxをダウンロード
=================

- 下記あたりのページから目的の環境(OS,バージョン,アーキテクチャ,構成管理ツール等)に合致するboxを探す
  - http://www.vagrantbox.es/
  - http://puppet-vagrant-boxes.puppetlabs.com/
  - http://opscode.github.io/bento/
- vagrant box add コマンドでboxを追加する
  - (例) centos5 という 名前、「CentOS5.10-i386, 構成管理ツールなし」という環境のBoxを追加
    ```vagrant box add centos5 http://puppet-vagrant-boxes.puppetlabs.com/centos-510-i386-virtualbox-nocm.box```


初期設定～起動まで
==================

適当なディレクトリを作成し、以下の手順を実施する

1. 初期設定
   - Vagrantfileを作成する
     - vagrant init centos5
   - 必要に応じて編集する（ひとまずそのままでもOK）
2. ゲストOSの起動
   - vagrant up
3. ゲストOSに接続
   - vagrant ssh


ゲストOSの設定
==============

Proxy設定（必要に応じて）
-------------------------

- /etc/yum.conf

  ```
  proxy=http://proxy.ex.co.jp:8080
  proxy_username=name
  proxy_password=password
  ```

- ~/.curlrc

  ```
  proxy=http://name:password@proxy.ex.co.jp:8080
  ```

- ~/.zshrc

  ```
  export HTTP_PROXY=http://name:password@proxy.ex.co.jp:8080
  export HTTPS_PROXY=http://name:password@proxy.ex.co.jp:8080
  ```

トラブルシューティング
======================

- 起動時に "Failed to mount folders in Linux guest..." というエラーがでる
  - 解決方法: http://qiita.com/osamu1203/items/10e19c74c912d303ca0b
