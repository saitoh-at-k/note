---
title: fluentd環境構築メモ
---

参考URL
=======

- http://docs.fluentd.org/ja/articles/architecture
- http://qiita.com/michiomochi@github/items/1a3cd07497550bc4d5c2


前提
====

- Vagrant環境構築メモで構築したゲストOS上で実施


インストール事前準備
====================

- 公式ドキュメントにしたがい、ひと通り設定する
  - http://docs.fluentd.org/ja/articles/before-install

<!--
  - （補足）NTPの設定
    - http://qiita.com/michiomochi@github/items/1a3cd07497550bc4d5c2
    - インストール
 	 - yum install -y ntp
    - /etc/ntp.conf
    - cp -p /usr/share/zoneinfo/Japan /etc/localtime
    - ntpdate ntp.nict.jp → 失敗
    - /etc/rc.d/init.d/ntpd start
    - chkconfig ntpd on
-->

- （必要に応じて）Vagrantfileにネットワーク遅延対策の設定を追記する
  - Vagrantfile

    ```
    config.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--natdnsproxy1", "off"]
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "off"]
    end
    ```
- （必要に応じて）ネームサーバの設定を追記する
  - /etc/resolv.conf

    ```
    nameserver 8.8.8.8
    ```


インストール
============

- 下記ページから適切なインストール方法を選択する
  - http://docs.fluentd.org/ja/categories/installation
- 今回は Ruby Gem からインストールする方法を実施
  - http://docs.fluentd.org/ja/articles/install-by-gem
