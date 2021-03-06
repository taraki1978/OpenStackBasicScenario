## ネットワークの作成

*(重要)* 以下の操作に移る前に、必ず[基本的な操作シナリオ RHELOSP7][Link-Top]を一読してください。 

### ネットワークメニューの選択

画面上部の「ネットワーク」ドロップダウンリストから、「ネットワーク」メニューを選択し、ネットワーク画面に移動します。

*メニュー選択*
[![https://gyazo.com/8a7a02aa22a28a943ede90aad63dc687](https://i.gyazo.com/8a7a02aa22a28a943ede90aad63dc687.gif)](https://gyazo.com/8a7a02aa22a28a943ede90aad63dc687)

*ネットワーク画面*

既存で利用可能なネットワークとして、exam-net がリストに表示されます。

[![https://gyazo.com/75782a7c6bd6e7ceaaac425f2eee042d](https://i.gyazo.com/75782a7c6bd6e7ceaaac425f2eee042d.png)](https://gyazo.com/75782a7c6bd6e7ceaaac425f2eee042d)

```
exam-netは、事前にクラウド管理者によって、外部(External)ネットワークとして構築されていることを想定してます。
まだ、外部ネットワークが構成されていない場合、ネットワークリストには何も表示されません。
外部ネットワークの構成方法がわからない場合は、クラウド管理者へ問い合わせてください。
```

### クラウド内部ネットワークの作成

プロジェクトの内部ネットワークを作成します。
ネットワークリストの右上部分にある「＋ネットワークの作成」ボタンを押下します。ボタンを押下すると、ネットワーク作成ウィザードが開きます。
[![https://gyazo.com/0ca6c41a2b7206e3adcdfafc41280093](https://i.gyazo.com/0ca6c41a2b7206e3adcdfafc41280093.gif)](https://gyazo.com/0ca6c41a2b7206e3adcdfafc41280093)


ネットワーク作成ウィザードにて、下記の情報を入力します。（なお、入力値は任意のものであっても問題ありません。）

| 項目 | 設定値 | 補足 |
|:-----------|:------------|:------------|
| ネットワーク名  | Priv | ネットワークの管理名称     |
| 管理状態  | UP | デフォルト  |

[![https://gyazo.com/2bb4e24e7a9c1e1a3f9103874baa3a38](https://i.gyazo.com/2bb4e24e7a9c1e1a3f9103874baa3a38.png)](https://gyazo.com/2bb4e24e7a9c1e1a3f9103874baa3a38)


入力が完了したら、「次へ」ボタンを押下し、「サブネット」設定へ遷移します。
サブネット設定では、下記の情報を入力します。（なお、入力値は任意のものであっても問題ありません。）

| 項目 | 設定値 | 補足 |
|:-----------|:------------|:------------|
| サブネットの作成  | チェック・オン |     |
| サブネット名  | subpriv | サブネットの管理名  |
| ネットワークアドレス  | 172.18.1.0/24 | CIDR形式で指定  |
| ゲートウェイIP  | 172.18.1.1 |   |
| ゲートウェイなし  | チェック・オフ |   |

[![https://gyazo.com/d65883da2bd6749f7ff4baf50b7546ef](https://i.gyazo.com/d65883da2bd6749f7ff4baf50b7546ef.png)](https://gyazo.com/d65883da2bd6749f7ff4baf50b7546ef)

入力が完了したら、「次へ」ボタンを押下し、「サブネットの詳細」設定へ遷移します。
サブネットの詳細設定では、下記の情報を入力します。（なお、入力値は任意のものであっても問題ありません。）

| 項目 | 設定値 | 補足 |
|:-----------|:------------|:------------|
| DHCP有効  | チェック・オン | 作成されるネットワークでDHCPサービスを有効とする    |
| IPアドレス割り当てプール  |  | サブネットの管理名  |
| DNSサーバ  |  | ゲストVM作成時に自動的に設定させたい場合、指定する  |
| 追加のルート設定  |  |ゲストVM作成時に自動的に設定させたい場合、指定する |

[![https://gyazo.com/d6311f7ca28cbf5390b768038d480331](https://i.gyazo.com/d6311f7ca28cbf5390b768038d480331.png)](https://gyazo.com/d6311f7ca28cbf5390b768038d480331)



入力が完了したら、「作成」ボタンを押下します。

[![https://gyazo.com/525f78247da3d4293d73db216f2c78a7](https://i.gyazo.com/525f78247da3d4293d73db216f2c78a7.gif)](https://gyazo.com/525f78247da3d4293d73db216f2c78a7)


ネットワーク「Priv」が、ネットワークリストに表示されます。

[![https://gyazo.com/bf46013e6cbac916e06e6a17e3f970c0](https://i.gyazo.com/bf46013e6cbac916e06e6a17e3f970c0.png)](https://gyazo.com/bf46013e6cbac916e06e6a17e3f970c0)

[次：ルータの作成へ](https://github.com/taraki1978/OpenStackBasicScenario/blob/master/kilo/rhelosp/jp/scenario/03-create-router.md)

