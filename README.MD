# Moodle 学習用環境

Docker on Vagrant(VirtualBox)

## 開発環境の構築方法
for Mac

### Homebrew のインストール
[Homebrew 公式](https://brew.sh/)

### VirtualBox のインストール
```sh
brew cask install virtualbox
```

### Vagrant のインストール
```sh
brew cask install vagrant
```

### プラグインのインストール
```sh
vagrant plugin install vagrant-disksize vagrant-vbguest vagrant-env vagrant-docker-compose
```


### Vagrant 用の環境変数の設定
`.env.example` をもとに `.env` ファイルを作成する。

全ての項目が必須。
基本的に変更しなくても良い。

#### VM_IP
ゲストのローカルIPアドレス。

既に使用済みの場合は別なものに変更する。

#### VM_CPUS
ゲストのCPUの数。

必要に応じて増減させる。

#### VM_MEMORY
ゲストのメモリサイズ。単位はMバイト。

必要に応じて増減させる。

#### VM_DISKSIZE
ゲストのディスクサイズ。

必要に応じて増やす。
(ゲスト作成済みの場合は減らすことはできない)


#### HTTP_PORT
ブラウザでのアクセス用ポート。

基本変更不要。

#### HTTPS_PORT
ブラウザでのSSL化されたアクセス用ポート。

基本変更不要。


#### DB_USERNAME
サーバー内部で使用するデータベースのmoodle用ユーザー名。

基本変更不要。

#### DB_PASSWORD
サーバー内部で使用するデータベースのmoodle用パスワード。

基本変更不要。

#### DB_DATABASE
サーバー内部で使用するデータベースのデータベース名。

基本変更不要。

#### DB_ROOT_PASSWORD
サーバー内部で使用するデータベースのrootのパスワード。

基本変更不要。
