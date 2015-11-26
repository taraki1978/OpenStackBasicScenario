## インスタンス起動の準備

これまでの手順で、インスタンスを接続するネットワークが準備できましたので、ここでは、インスタンス起動前の準備を行います。

### セキュリティーグループの作成
セキュリティグループの作成では、外部ネットワークからセキュリティグループ内のVMインスタンスに対して、HTTP、SSH、ICMPでのアクセスが可能なように設定します。

画面上部の「コンピュート」ドロップダウンリストから、「アクセスとセキュリティー」メニューを選択します。アクセスとセキュリティー画面が表示されます。
[![https://gyazo.com/d4e9793040058b02df82eb389103e5d1](https://i.gyazo.com/d4e9793040058b02df82eb389103e5d1.gif)](https://gyazo.com/d4e9793040058b02df82eb389103e5d1)

アクセスとセキュリティー画面の、「セキュリティーグループ」タブにて、「＋セキュリティーグループの作成」ボタンを押下します。「セキュリティグループの作成」ウィザードが表示されます。
[![https://gyazo.com/cea98e9d30bded5827853f9fed81b53f](https://i.gyazo.com/cea98e9d30bded5827853f9fed81b53f.gif)](https://gyazo.com/cea98e9d30bded5827853f9fed81b53f)

「セキュリティグループの作成」ウィザードにて、必要項目を下表に従い入力します。

| 項目 | 設定値 | 補足 |
|:-----------|:------------|:------------|
| 名前  | Web＆SSH | 任意のセキュリティーグループ名     |
| 説明  |  | 必要に応じて説明を入力します。  |

[![https://gyazo.com/cea4f35cee4c3cea43a7b90fae406ee5](https://i.gyazo.com/cea4f35cee4c3cea43a7b90fae406ee5.png)](https://gyazo.com/cea4f35cee4c3cea43a7b90fae406ee5)

入力項目を確認し、「セキュリティーグループの作成」ボタンを押下します。Web&SSHセキュリティーグループが一覧に表示されます。
[![https://gyazo.com/020dc4f236a6330e2fc085532cae7fb0](https://i.gyazo.com/020dc4f236a6330e2fc085532cae7fb0.gif)](https://gyazo.com/020dc4f236a6330e2fc085532cae7fb0)

セキュリティーグループ一覧の「Web&SSH」行の最右部にある「ルールの管理」ボタンを押下します。設定済みのルール一覧が表示されます。
[![https://gyazo.com/03534de6b57d5040d2438f5e5d534c0f](https://i.gyazo.com/03534de6b57d5040d2438f5e5d534c0f.gif)](https://gyazo.com/03534de6b57d5040d2438f5e5d534c0f)

ルール一覧の上部にある「＋ルールの追加」ボタンを押下します。「ルールの追加」ウィザードが表示されます。
[![https://gyazo.com/2c8fd9f6699495fd16efc6760f19db2b](https://i.gyazo.com/2c8fd9f6699495fd16efc6760f19db2b.gif)](https://gyazo.com/2c8fd9f6699495fd16efc6760f19db2b)

#### ICMPの許可

「ルールの追加」ウィザードにて、下表のようにICMP用の設定を入力します。

| 項目 | 設定値 | 補足 |
|:-----------|:------------|:------------|
| ルール  | ALL ICMP |  |
| 方向 | 受信 |   |
| 接続相手 | CIDR | 接続相手の定義方法を指定  |
| CIDR | 0.0.0.0/0 | 全てのホストからの接続を許可しています。 |

[![https://gyazo.com/a8c79a0b34174fe91f1e8e5e283cdf1b](https://i.gyazo.com/a8c79a0b34174fe91f1e8e5e283cdf1b.png)](https://gyazo.com/a8c79a0b34174fe91f1e8e5e283cdf1b)

入力後、「作成」ボタンを押下します。一覧に作成したルールが表示されます。
[![https://gyazo.com/dbb758d78ab89af951ead9f5e50e7869](https://i.gyazo.com/dbb758d78ab89af951ead9f5e50e7869.gif)](https://gyazo.com/dbb758d78ab89af951ead9f5e50e7869)

#### HTTPの許可
続けて、先のICMP許可と同様、「＋ルールの追加」ボタンを押下し、下表のようにHTTP用の設定を入力します。入力後、「作成」ボタンを押下します。

| 項目 | 設定値 | 補足 |
|:-----------|:------------|:------------|
| ルール  | HTTP |  |
| 接続相手 | CIDR | 接続相手の定義方法を指定  |
| CIDR | 0.0.0.0/0 | 全てのホストからの接続を許可しています。 |

[![https://gyazo.com/8756584c81c2a8743c69a00349d32797](https://i.gyazo.com/8756584c81c2a8743c69a00349d32797.png)](https://gyazo.com/8756584c81c2a8743c69a00349d32797)

#### SSHの許可
続けて、先のICMP許可と同様、「＋ルールの追加」ボタンを押下し、下表のようにSSH用の設定を入力します。入力後、「作成」ボタンを押下します。

| 項目 | 設定値 | 補足 |
|:-----------|:------------|:------------|
| ルール  | SSH |  |
| 接続相手 | CIDR | 接続相手の定義方法を指定  |
| CIDR | 0.0.0.0/0 | 全てのホストからの接続を許可しています。 |

[![https://gyazo.com/8d0b1d09c32ed2dcb795ab2e65841f54](https://i.gyazo.com/8d0b1d09c32ed2dcb795ab2e65841f54.png)](https://gyazo.com/8d0b1d09c32ed2dcb795ab2e65841f54)

ICMP,HTTP,SSHのルール作成が完了すると、ルール一覧には5行のルールが表示された状態となります。
[![https://gyazo.com/c84cb6150bbd190527fb58ff5e1ebe4d](https://i.gyazo.com/c84cb6150bbd190527fb58ff5e1ebe4d.png)](https://gyazo.com/c84cb6150bbd190527fb58ff5e1ebe4d)

