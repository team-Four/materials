# Vagrant Plugin

vagrant には様々な plugin が存在している。

- `vagrant plugin install <plugin name>` で install できる。
- `vagrant plugin list` で install 済みの plugin が表示できる  
- `vagrant plugin -h` で他の comannd も確認できる

## sahara

sahara は vagrant の plugin.  
vagrant の状態を管理できる。  
sandbox mode に移行できて、その間に仮想環境に加えた変更を取り消す(rollback) するか、適応(commit) するか選べる。

- `vagrant plugin install sahara` で install
- `vagrant sandbox on` で sandbox mode になる
- `vagrant ssh` し作業をする
- `vagrant sandbox rollback` で気に入らない場合にロールバックする
- `vagrant sandbox commit` で現在の状態をコミットする
- `vagrant sandbox off` で sandbox mode を終了する

## 使いどころ

環境構築時に、sahara を利用して確かめながら進めるといいと思う。  
僕の場合にはトライアンドエラーで環境構築の手順をまとめて、キレイのその手順を確かめるために、一からやり直すために sahara を使った。


