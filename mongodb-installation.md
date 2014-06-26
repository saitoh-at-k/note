---
title: MongoDBインストールと基本操作
---

参考URL
=======

- http://docs.mongodb.org/manual/tutorial/install-mongodb-on-red-hat-centos-or-fedora-linux/


前提
====

- Vagrant環境構築メモで構築したゲストOS上で実施


YUMリポジトリの追加
===================

/etc/yum.repos.d/mongodb.repo を作成する。内容は以下。

```
[mongodb]
name=MongoDB Repository
baseurl=http://downloads-distro.mongodb.org/repo/redhat/os/x86_64/
gpgcheck=0
enabled=1
```


インストール
============

`sudo yum install mongodb-org`


MongoDBの操作
=============

- 起動

  `sudo /sbin/service mongod start`

- 停止

  `sudo /sbin/service mongod stop`

- 再起動

  `sudo /sbin/service mongod restart`

- 自動起動

  `sudo /sbin/chkconfig mongod on`

- 接続

  `mongo`

- DB一覧を表示

  `show dbs`

- DB選択

  `use <db_name>`

- Collection一覧を表示

  `show collections`

- Collectionの全ドキュメントを表示

  `db.<collection_name>.find()`

- Collectionのドキュメント件数を表示

  `db.<collection_name>.count()`

- Collectionの全ドキュメントを削除

  `db.<collection_name>.remove({})`
