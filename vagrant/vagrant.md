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

`$ vagrant list`

でローカルに登録された`box` のリストを確認することができる。


