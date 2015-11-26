## ルータの作成

この手順では、前の手順「ネットワークの作成」で作成したプロジェクト内部ネットワークと、外部ネットワークを接続するルータを作成します。

### ルータの作成

画面上部2段目のルータメニューを押下します。ルータ一覧画面に遷移します。

[![https://gyazo.com/27bbea2376586abe6cf5ad5e9c1d58bc](https://i.gyazo.com/27bbea2376586abe6cf5ad5e9c1d58bc.gif)](https://gyazo.com/27bbea2376586abe6cf5ad5e9c1d58bc)


ルータ一覧画面にて、リスト右上部にある「ルータの作成」ボタンを押下します。ルータの作成ウィザードが開きます。

[![https://gyazo.com/810d79c904544d84f275bc3ddf6db444](https://i.gyazo.com/810d79c904544d84f275bc3ddf6db444.gif)](https://gyazo.com/810d79c904544d84f275bc3ddf6db444)


ルータの作成画面にて、必要項目を下表のように入力します。

| 項目 | 設定値 | 補足 |
|:-----------|:------------|:------------|
| ルータ名  | router | ルータの識別名     |
| 管理状態  | UP | デフォルト  |
| 外部ネットワーク  | exam-net | 環境に合わせて、外部ネットワークを選択します |

[![https://gyazo.com/72317bf596fa303ee3c085c7a18c7be2](https://i.gyazo.com/72317bf596fa303ee3c085c7a18c7be2.png)](https://gyazo.com/72317bf596fa303ee3c085c7a18c7be2)

必要項目の入力完了後、「作成」ボタンを押下します。

[![https://gyazo.com/1a58e858c327aed85291a6073169bb2e](https://i.gyazo.com/1a58e858c327aed85291a6073169bb2e.gif)](https://gyazo.com/1a58e858c327aed85291a6073169bb2e)

ルータが作成され、ルータ一覧にルータが表示されます。*(要修正)*
[![https://gyazo.com/cfd17440586ad6427b23f9d3835e5398](https://i.gyazo.com/cfd17440586ad6427b23f9d3835e5398.png)](https://gyazo.com/cfd17440586ad6427b23f9d3835e5398)

### ルータへ内部ネットワーク接続用インターフェースの追加

ルータへインタフェースを作成するため、ルータ名のリンク部分を押下します。ルータ主詳細画面が表示されるので、続けて「インターフェース」タブを押下します。
[![https://gyazo.com/e4b46611e3afee150b9b6a2b3ee42dde](https://i.gyazo.com/e4b46611e3afee150b9b6a2b3ee42dde.gif)](https://gyazo.com/e4b46611e3afee150b9b6a2b3ee42dde)

インターフェース一覧画面にて、一覧右上部分の「＋インターフェースの追加」ボタンを押下します。「インターフェースの追加」ウィザードが表示されます。
[![https://gyazo.com/e3177d9334ed21ef71b3c1b2e7e8088b](https://i.gyazo.com/e3177d9334ed21ef71b3c1b2e7e8088b.gif)](https://gyazo.com/e3177d9334ed21ef71b3c1b2e7e8088b)

「インタフェースフェースの追加」画面にて、必要項目を下表のように入力します。

| 項目 | 設定値 | 補足 |
|:-----------|:------------|:------------|
| サブネット  | priv: 172.18.1.0/24(subpriv) | ネットワークの作成でしたネットワークを指定  |
| IPアドレス（省略可）  | 　 | 省略したばあい、第4オクテッドは"1"となる。  |

[![https://gyazo.com/7e2e923210ed3056fe6907ef178c0d33](https://i.gyazo.com/7e2e923210ed3056fe6907ef178c0d33.png)](https://gyazo.com/7e2e923210ed3056fe6907ef178c0d33)

必要項目の入力完了後、「インターフェースの追加」ボタンを押下します。
[![https://gyazo.com/c54d5c998c364782227cb1555fc47b75](https://i.gyazo.com/c54d5c998c364782227cb1555fc47b75.gif)](https://gyazo.com/c54d5c998c364782227cb1555fc47b75)

### ルータのネットワーク接続状況の確認

インターフェースが一覧に表示されたことを確認し、画面上部の「ネットワーク」ドロップダウンリストから、「ネットワークトポロジー」メニューを選択します。
[![https://gyazo.com/7924bdeb996394cc5f8281f2f9f6a1f3](https://i.gyazo.com/7924bdeb996394cc5f8281f2f9f6a1f3.gif)](https://gyazo.com/7924bdeb996394cc5f8281f2f9f6a1f3)

ネットワークトポロジー図にて、ルータがexam-netネットワークとprivネットワークに接続されている事を確認します。
[![https://gyazo.com/5acff8541d51cf5dfaaf2e1ffbcf6ef2](https://i.gyazo.com/5acff8541d51cf5dfaaf2e1ffbcf6ef2.png)](https://gyazo.com/5acff8541d51cf5dfaaf2e1ffbcf6ef2)

