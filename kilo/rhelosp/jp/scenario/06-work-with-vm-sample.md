## インスタンスVMでの作業（例）

ここでは、実際に作成したインスタンスVMを利用するシーンを体験するため、Webサーバをセットアップします。

### インスタンスVMへのSSHアクセス

sshクライアントソフトウェアを起動し、インスタンスVMのフローティングIPへ、鍵交換方式で接続します。
接続に必要な情報は、下記の通りです。
 * 接続先インスタンスVMのフローティングIP
 
    -. (インスタンスの起動[フローティングIPのインスタンスVMへの割り当て]で割り当てたもの)
 * 接続ユーザ名：cloud-user 
 * ssh秘密鍵 
 
    -. (インスタンス起動の前準備（続き）[キーペアの作成]にてダウンロードしたファイル)
    

以下は、Windowsマシンからteratermを使用した場合の操作例となります。

#### 接続先IPを指定
ホスト欄に、接続先のインスタンスVMのフローティングIPを指定します。

[![https://gyazo.com/4f166f75cb3de1a8d9745666d92d9af4](https://i.gyazo.com/4f166f75cb3de1a8d9745666d92d9af4.png)](https://gyazo.com/4f166f75cb3de1a8d9745666d92d9af4)

セキュリティ警告が表示される場合は、「続行」ボタンを押下

[![https://gyazo.com/ee10f7e5419f9b86a4289dd3a9ebee6d](https://i.gyazo.com/ee10f7e5419f9b86a4289dd3a9ebee6d.png)](https://gyazo.com/ee10f7e5419f9b86a4289dd3a9ebee6d)

#### ログインの実施

ユーザ名を入力し、RSA/DSA鍵を使う オプションのラジオボタンを有効にした上で、秘密鍵（ダウンロードしたもの）を指定します

入力が完了したら、「OKボタンを押下します。」

[![https://gyazo.com/370b0a32082aebcc45efc03bdec818d9](https://i.gyazo.com/370b0a32082aebcc45efc03bdec818d9.png)](https://gyazo.com/370b0a32082aebcc45efc03bdec818d9)


ログインが完了すると、SSHのセッションが開始されます。

[![https://gyazo.com/e14d9d9b00babede565de64eabd83c70](https://i.gyazo.com/e14d9d9b00babede565de64eabd83c70.png)](https://gyazo.com/e14d9d9b00babede565de64eabd83c70)


### 内部リポジトリの登録
※内部リポジトリではなく、直接Red Haty社のリポジトリを使用する場合は、"subscription-manager register"を実行してください。

コマンドラインにて、yum-config-mangerコマンドを実行し、内部リポジトリを追加します。
※参照先リポジトリは環境に合わせて適宜修正してください。
'''command 
$ sudo yum-config-manager --add-repo=http://192.168.50.65/Linux/rhel/7.1/os/x86_64
'''
yum repolist を実行し、リポジトリが追加されていることを確認します。

'''command
$ yum repolist
'''

署名のチェックをスキップしする必要がある場合、/etc/yum.repo.d/repofile.repo の追加したリポジトリに、"gpgcheck=0"を追加設定する必要があります。下記は、前述のyum-config-manager実行直後の状態で、ファイル名が、"192.168.50.65_Linux_rhel_7.1_os_x86_64.repo"である場合、最終行に"gpgcheck"無効化の設定を入れている例となります。

'''gpgcheck無効化の例
$ echo "gpgcheck=0" |sudo tee -a /etc/yum.repos.d/192.168.50.65_Linux_rhel_7.1_os_x86_64.repo
'''

### httpd(webサーバプログラム)のインストール
yum コマンドを使用して、httpd プログラムをインストールします。

'''command
$ sudo yum install -y httpd
'''

### シンプルなHTMLコンテンツの作成
Webページを作成します。 デフォルトのDocument Root 配下に、index.htmlをviエディタで作成しても構いませんが、より簡単に行うためには、下記のコマンドを実行します。

'''
$ hostname | sudo tee -a /var/www/html/index.html
'''

### httpdサービスの起動
Webサーバプログラムを起動します。

'''
$ sudo systemctl start httpd
'''

### 接続テスト
操作を行っているPC上で、Webブラウザを立ち上げ、フローティングIPを指定して接続します。画面にあるように、画面が応答されれば成功となります。

* URL(例): http://192.168.50.209 ※これまでの例で示してきたフローティングIPを指定しています。

[![https://gyazo.com/d84b9f807fa07450fd728fdb72fe1ece](https://i.gyazo.com/d84b9f807fa07450fd728fdb72fe1ece.png)](https://gyazo.com/d84b9f807fa07450fd728fdb72fe1ece)


OpenStack環境上に、Webサーバを構築するシナリオは、以上となります。
