# BOX

Box は Vagrant マシンを構築するためのスケルトンです。作業環境を持ち出すために、 Box は Vagrant を実行する任意のプラットフォーム上で使用できるポータブルなファイルです。

`vagrant box` ユーティリティは Box を管理するためのすべての機能を提供します。現在、手動で Box を作成する必要があります。

Box は [Provider 固有](http://docs.vagrantup.com/v2/providers/)です。そのため、使っている Provider に合わせて適切な Box を取得する必要があります。

Box の正確なファイルフォーマットに興味があるならば、[専用のページ](./format.md)があります。これは高度なトピックであるため、一般的なユーザーが知る必要はありません。


## BOX の追加

Box を追加することは簡単です：

```
$ vagrant box add name url
```

`name` は Box が Vagrantfile から参照される論理名です。ここにはなんでも指定できますが、 Vagrant が使用する Box を探せるように `config.vm.box` の指定と name が一致することを確認してください。

`url` は Box の場所です。これにはローカルファイルシステムまたは リモートの Box への HTTP URL のパスを指定できます。

Vagrant は Box アーカイブ内の "metadata.json" ファイルを読み込み Provider を自動的に決定します。どの Provider 向けの Box であるかを `--provider` フラグで Vagrant に渡すこともできます。

ダウンロードしている Box の確認を行なうとき、これは推薦されます。さらに、名前と Provider が同じ Box がすでに存在する場合は Vagrant はエラーで早期に終了できます。それ以外の場合はこのようにエラーが表示される前に Box 全体をダウンロードしなければなりません。

Box が異なる Provider 向けの Box であれば、同じ名前でも複数存在することができます。以下の Box リストの例は、異なる Provider に裏打ちされた複数の precise64 Box があることを示しています。これは単一の Vagrantfile 内の `config.vm.box` に Provider を横断した適切な Box を参照させておきます。


## BOX のリスト

Vagrant では `vagrant box list` を使ってローカルにインストールされている Box を表示します：

```
$ vagrant box list
precise64 (virtualbox)
precise64 (vmware_fusion)
```

Vagrant はすべての Box と括弧内に Provider を一覧表示します。


## BOX の削除

Box の追加と同じくらい簡単に Box の削除を行なうことができます：

```
$ vagrant box remove precise64 virtualbox
```

二つの引数は、 Box と Box の Provider の論理名です。


## Providerのオプションパラメータ？
Vagrant の将来のリリースでは、Box を削除する時の Provider パラメーターは任意になります。この場合、 Vagrant は削除することのできる Box のリストを表示し、ユーザーにどれを削除したいかを尋ねます。現在、これは実装されていません。

