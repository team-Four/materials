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

## Control VirtualMachine

- `$ vagrant up` マシンの作成と起動
- `$ vagrant halt` マシンのシャットダウン
- `$ vagrant reload` halt と up を行う
- `$ vagrant destroy` マシンを削除する



