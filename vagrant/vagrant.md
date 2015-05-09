# Vagrant Start up

## Install

仮想環境をエミュレートするツール  
[VirtualBox](https://www.virtualbox.org/)

VirtualBox などの仮想環境エミュレータをコマンドライン上から操作するツール  
[Vargrant](https://www.vagrantup.com/)

## Add box

Vagrant は仮想イメージを `box` とよばれるフォーマットで扱う。  
`box` を手っ取り早く入手するには virtualbox が公式で提供している`box` を Atlas のサイトからダウンロードする。[こちら](https://atlas.hashicorp.com/ubuntu/boxes/trusty64)  

実際には Web ブラウザからダウンロードするのではなく

`$ vagrant box add ubuntu/trusty64`

というコマンドを実行することで、ローカルの vagrant box の一覧にダウンロードされ追加される。`ubuntu/trusty64` という部分が、追加する`box`の名前を指定する部分になる。この名前を Atlas のサイトに登録されているかどうか確認し、該当するものがあれば、ローカルにダウンロードされる。

コマンド実行後は

`$ vagrant box list`

でローカルに登録された`box` のリストを確認することができる。

## Activate Linux

`box` を登録したら仮想マシンを作成し立ち上げる。仮想マシンはディレクトリ毎に管理される。  

1. 適当なディレクトリを作成し、その中に入る
- `$ vagrant init ubuntu/trusty64` で、`ubuntu/trusty64` の`box`を指定した初期化を行う
- `$ ls` で `Vagrantfile` が作成されていることを確認する。Windows なら `dir`
- `$ vagrant up` で `Vagrantfile` を元に仮想マシンを作成し起動する
- `$ vagrant ssh` で起動したマシンに login する。デフォルトではユーザ名とパスワードは`vagrant`
  - Windows の場合は TeraTerm などから、ホスト `127.0.0.1`、ポート `2222` でログインする

> Tips : Vagrantfile が box名を管理している。
>
> ```ruby
> config.vm.box = "ubuntu/trusty64"
> ```
> マシンの`box`名を設定する部分。`vagrant init <box名>` で指定したものが記載される。  
> `vagrant up` の際に、このbox名を参照し、ローカルのbox一覧にあれば、その`box`を使用する。なければ`atlas`に探しに行く。

## Control VirtualMachine

- `$ vagrant up` マシンの作成と起動
- `$ vagrant halt` マシンのシャットダウン
- `$ vagrant reload` halt と up を行う
- `$ vagrant destroy` マシンを削除する

## Configure Network 

`Vagrantfile` に仮想マシンの設定が記載されている。マシンのネットワークの設定もそこで行える。  

デフォルトの状態ではNAT接続になっており、仮想マシンから外のネットワークには接続できるが、外から仮想マシンには接続できない。

```ruby
config.vm.network "forwarded_port", guest: 80, host: 8080
```
NAT接続の状態で、特定のポートに足しいて外からの接続を受け付けたい場合には`ポートフォワード`で対応できる。`guest:` に仮想マシン(ゲストマシン) のポートを指定し、`host:` にホストマシンのポートを指定する。ホストマシンに対して指定したポートにアクセスがあると、そのままゲストマシンに指定したポートにアクセスを投げてもらう設定




```ruby
config.vm.network "private_network", ip: "192.168.33.10"
```
ホストマシン内に閉じたネットワークを形成する。仮想マシン(ゲストマシン)は一切外のネットワークに繋がらない

```ruby
config.vm.network "public_network"
```
ホストマシンと同列のLAN内に仮想マシンがあるにようする。ブリッジ接続を行う。




