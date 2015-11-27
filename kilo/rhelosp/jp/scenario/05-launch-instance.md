## インスタンスの起動
この操作では、実際にプロジェクトの内部ネットワーク上に、インスタンスVMを起動させます。

### インスタンスの起動

画面上部2段目の「インスタンス」メニューを押下します。インスタンス一覧画面に遷移します。

[![https://gyazo.com/0b7265ef94bb1d35c5b1f6e4c6134962](https://i.gyazo.com/0b7265ef94bb1d35c5b1f6e4c6134962.gif)](https://gyazo.com/0b7265ef94bb1d35c5b1f6e4c6134962)


インスタンス一覧の右上部分にある「インスタンスの起動」ボタンを押下します。インスタンスの起動ウィザードが表示されます。

[![https://gyazo.com/f098c6300645c7612d3c6d557d02d00f](https://i.gyazo.com/f098c6300645c7612d3c6d557d02d00f.gif)](https://gyazo.com/f098c6300645c7612d3c6d557d02d00f)


インスタンスの起動ウィザードにて、下表の項目を入力しします。

| 項目 | 設定値 | 補足 |
|:-----------|:------------|:------------|
| アベイラビリティーゾーン  | nova | デフォルト |
| インスタンス名  | web01 | インスタンスVMの名称を指定 |
| フレーバー  | m2.tiny | カスタムであらかじめ用意する必要有。クラウドリソースに余裕がある場合、m1.smallの選択も可(*1) |
| インスタンス数  | 1 | 1以上の整数で指定。2以上を指定すると、インスタンス名-nnのように添え字付でインスタンスが作成される。|
| インスタンスのブートリソース  | イメージから起動 |(*1)  |
| イメージ名 | RHEL7.1(415.5　MB) | 予めイメージが登録されている必要がある。(*1) |

(*1)本シナリオを操作するために、事前にクラウド環境のセットアップを実施しています。クラウド環境の詳細情報は、下記を参照。
[クラウド環境の詳細(クラウド監理者向け情報)](準備中)

[![https://gyazo.com/6b2e048dad281914fb613a6f8b633d7c](https://i.gyazo.com/6b2e048dad281914fb613a6f8b633d7c.png)](https://gyazo.com/6b2e048dad281914fb613a6f8b633d7c)


必要項目の入力が完了した後、上部タブの**「アクセスとセキュリティ」**タブを押下します。

[![https://gyazo.com/d37f209cae5d1aba83e15dd15bbe2aed](https://i.gyazo.com/d37f209cae5d1aba83e15dd15bbe2aed.gif)](https://gyazo.com/d37f209cae5d1aba83e15dd15bbe2aed)

「アクセスとセキュリティ」設定にて、下表の項目を入力します。

| 項目 | 設定値 | 補足 |
|:-----------|:------------|:------------|
| キーペア | mykey | インスタンス起動の前準備(続き)「キーペアの作成」で作成したものを指定。 |
| セキュリティグループ  | Web & SSH | インスタンス起動の前準備「セキュリティグループの作成」で作成したものを指定。 |

[![https://gyazo.com/0d4965be15e0360198b3ee1901c3136e](https://i.gyazo.com/0d4965be15e0360198b3ee1901c3136e.png)](https://gyazo.com/0d4965be15e0360198b3ee1901c3136e)

必要項目の入力が完了した後、上部タブの**「ネットワーク」**タブを押下します。

[![https://gyazo.com/8cf697228942e37210db534fcfa59193](https://i.gyazo.com/8cf697228942e37210db534fcfa59193.gif)](https://gyazo.com/8cf697228942e37210db534fcfa59193)


「ネットワーク」設定にて、インスタンスVMにアタッチするネットワークを指定します。

| 項目 | 設定値 | 補足 |
|:-----------|:------------|:------------|
| 選択済みネットワーク | priv(XXXXXXXX) |   |

選択時は、「利用可能なネットワーク」欄内にリストされているネットワーク名右隅の青い＋アイコンを押下します。

[![https://gyazo.com/98085888cbabb4533152ab64a4ee1076](https://i.gyazo.com/98085888cbabb4533152ab64a4ee1076.gif)](https://gyazo.com/98085888cbabb4533152ab64a4ee1076)

設定した内容を確認し、ウィザード右下の「起動」ボタンを押下します。インスタンスの起動処理が実行されます。

[![https://gyazo.com/f399630e0a5665f4a5e354783a1b9bd3](https://i.gyazo.com/f399630e0a5665f4a5e354783a1b9bd3.gif)](https://gyazo.com/f399630e0a5665f4a5e354783a1b9bd3)

インスタンスの起動処理が管理完了すると、ステータス欄が稼働中となります。

[![https://gyazo.com/151dc4e41ca6b3865ce7f6e5377f42ae](https://i.gyazo.com/151dc4e41ca6b3865ce7f6e5377f42ae.png)](https://gyazo.com/151dc4e41ca6b3865ce7f6e5377f42ae)

### フローティングIPのインスタンスVMへの割り当て

作成されたインスタンスの「アクション」ドロップダウンリストから、「Floating IP の割り当て」を選択します。Floating IPの割り当て管理ウィザードが開きます。

[![https://gyazo.com/c8199d8721d46c6767aa8b6582400ec7](https://i.gyazo.com/c8199d8721d46c6767aa8b6582400ec7.gif)](https://gyazo.com/c8199d8721d46c6767aa8b6582400ec7)

IPアドレス欄ドロップダウンリストから、割り当てるIP（インスタンス起動の前準備（続き）「フローティングIPの確保」操作で確保したもの）を選択します。

[![https://gyazo.com/be97c51350b480ff5320a1e90771feee](https://i.gyazo.com/be97c51350b480ff5320a1e90771feee.gif)](https://gyazo.com/be97c51350b480ff5320a1e90771feee)

設定が完了した後、「割り当て」ボタンを押下します。インスタンスVMへ、フローティングIPが割り当てられます。

[![https://gyazo.com/8301ee7b6e5cd82731c7a5ec4e1f57d7](https://i.gyazo.com/8301ee7b6e5cd82731c7a5ec4e1f57d7.gif)](https://gyazo.com/8301ee7b6e5cd82731c7a5ec4e1f57d7)

インスタンス一覧のIPアドレス欄の記載内容が、内部ネットワーク(172.18.1.0/24)と、外部ネットワーク(192.168.50.0/24)からそれぞれ割り当てられている状態となります。

[![https://gyazo.com/8e830a38a4c03c0ac2b533eb64239a0c](https://i.gyazo.com/8e830a38a4c03c0ac2b533eb64239a0c.png)](https://gyazo.com/8e830a38a4c03c0ac2b533eb64239a0c)

### 構築状況の確認

画面上段のネットワークドロップダウンリストから、「ネットワークトポロジー」メニューを選択し、ネットワークトポロジーのイメージを表示します。

[![https://gyazo.com/c43fb28adb4f3a72db1449cdababbebc](https://i.gyazo.com/c43fb28adb4f3a72db1449cdababbebc.gif)](https://gyazo.com/c43fb28adb4f3a72db1449cdababbebc)

インスタンスの起動により、内部ネットワークに、インスタンスVM（web01)が接続されていることを確認します。

