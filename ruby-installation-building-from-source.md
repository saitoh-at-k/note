---
Rubyをソースからビルドしてインストールする
---

前提
====

- OS: CentOS5.10
- yumを使うと古いバージョンのRubyがインストールされるため、ソースからビルドして最新のRubyをインストールする
- Rubyのバージョンは手順実施時点の最新版に適宜読み替えること
- 必要に応じてProxyの設定をしておくこと
    - Vagrant環境構築メモを参照


手順
====

Rubyコンパイルに必要なパッケージをインストールする

``` shell
yum -y install gcc zlib-devel openssl-devel sqlite sqlite-devel
```

最新のソースを取得し、解凍する

``` shell
curl -O http://cache.ruby-lang.org/pub/ruby/2.1/ruby-2.1.2.tar.gz
tar zxvf ruby-2.1.2.tar.gz
cd ruby-2.1.2
```

ビルドしてインストールする

``` shell
./configure
make
make install
```

インストール確認

``` shell
which ruby
#=> /usr/local/bin/ruby
ruby -v
#=> ruby 2.1.2p95 (2014-05-08 revision 45877) [i686-linux]
```
