## インスタンス起動の前準備（続き）

セキュリティグループの作成に続いて、インスタンスVMの接続時にしようするSSLキーペアの作成と、フローティングIPの確保操作を行います。

### キーペアの作成

アクセスとセキュリティー画面にて、「キーペア」タブを押下します。キーペア一覧画面に遷移します。

[![https://gyazo.com/ccf042c0a335370fbbdb3a6cd8bbf918](https://i.gyazo.com/ccf042c0a335370fbbdb3a6cd8bbf918.gif)](https://gyazo.com/ccf042c0a335370fbbdb3a6cd8bbf918)

一覧右上部分の「＋キーペアの作成」ボタンを押下します。「キーペアの作成」ウィザードが開きます。

[![https://gyazo.com/3c31be316ae06eb6f9e77a3836d248b4](https://i.gyazo.com/3c31be316ae06eb6f9e77a3836d248b4.gif)](https://gyazo.com/3c31be316ae06eb6f9e77a3836d248b4)

キーペア作成ウィザードにて、必要項目を下表のように入力します。

| 項目 | 設定値 | 補足 |
|:-----------|:------------|:------------|
| キーペア名  | mykey | 任意のキーペアの名前。 |

[![https://gyazo.com/e0479b4bced2ad99ca038be92f9cefe2](https://i.gyazo.com/e0479b4bced2ad99ca038be92f9cefe2.png)](https://gyazo.com/e0479b4bced2ad99ca038be92f9cefe2)

入力内容を確認し、「キーペアの作成」ボタンを押下します。自動的にダウンロードが始まります。

```note
 キーペアファイルのダウンロードは、作成時のみ可能です。この操作で必ずダウンロードしてください。また、ダウンロードする
ファイルは、秘密鍵であるため、本来的には、第三者に盗まれないよう大切に保管すべきファイルである事に注意してください。
```

```note
 過去の操作にて、キーペア名を同じ名前で指定している場合、ファイルをダウンロードする際に、Webブラウザーによって自動的
に名前が変更される場合があります。(chromeでは、自動的に、mykey(1).pem,mykey(2).pemのようになります。)
 また、過去のファイルがすでに不要となっている場合で、ダウンロード時に手動で上書きが可能な場合は、上書きで保存してくだ
さい。上書きができない場合は、ダウンロード時に、適宜ファイル名を指定して保存してください。
 尚、ダウンロードしたファイルは、インスタンスVMへSSH接続する際に必要となるので、ファイル名を忘れないようにしてください。
ファイルの管理上、キーペア名とダウンロードのファイル名の相違が望ましくない場合は、キーペア作成時のキーペア名の指定にお
いて、ユニークな名称を指定してください。（ex:mykey_2,mykey_3...etc)
```

[![https://gyazo.com/9fbc07717872a18024ac13f3a1cdc92c](https://i.gyazo.com/9fbc07717872a18024ac13f3a1cdc92c.gif)](https://gyazo.com/9fbc07717872a18024ac13f3a1cdc92c)

ダウンロード完了後、再び「アクセスとセキュリティー」メニューを選択します。「キーペア」一覧画面に遷移します。

[![https://gyazo.com/0d7bb51c57f5acaeaa8d4cbeff38c041](https://i.gyazo.com/0d7bb51c57f5acaeaa8d4cbeff38c041.gif)](https://gyazo.com/0d7bb51c57f5acaeaa8d4cbeff38c041)

### フローティングIPの確保
ここからは、プロジェクトの外部から、内部ネットワークのインスタンスVMへ通信する場合に必要となるフローティングIPの取得を行います。
アクセスとセキュリティー画面にて、「Floating IP」タブを押下します。フローティングIP一覧画面に遷移します。

[![https://gyazo.com/6c6f15b6af6d148fbb064bc4e1d6e5de](https://i.gyazo.com/6c6f15b6af6d148fbb064bc4e1d6e5de.gif)](https://gyazo.com/6c6f15b6af6d148fbb064bc4e1d6e5de)

一覧右上部分の「＋Floating IPの確保」ボタンを押下します。「Floating IPの確保」ウィザードが開きます。

[![https://gyazo.com/254a5f3c793312ce85ce5e5f1829a0fa](https://i.gyazo.com/254a5f3c793312ce85ce5e5f1829a0fa.gif)](https://gyazo.com/254a5f3c793312ce85ce5e5f1829a0fa)

Floating IPの確保ウィザードにて、下表の項目を選択し、「IPの確保」ボタンを押下します。

| 項目 | 設定値 | 補足 |
|:-----------|:------------|:------------|
| プール  | exam-net | フローティングIPを取得したい外部ネットワークを設定する |

[![https://gyazo.com/6133f228a42bdf6d2f9b27b11baa2e22](https://i.gyazo.com/6133f228a42bdf6d2f9b27b11baa2e22.gif)](https://gyazo.com/6133f228a42bdf6d2f9b27b11baa2e22)

ここまでの操作によって、フローティングIPが予約された状態となります。


[次：インスタンスの起動](https://github.com/taraki1978/OpenStackBasicScenario/blob/master/kilo/rhelosp/jp/scenario/05-launch-instance.md)
