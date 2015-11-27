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

### httpd(webサーバプログラム)のインストール

### シンプルなHTMLコンテンツの作成

### httpdサービスの起動

### 接続テスト


