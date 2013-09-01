# プロビジョナーの基本的な使い方

Vagrant は提供している複数のオプションで、どのようにマシンをプロビジョニングするか決めます。標準的な使い方とすべてのプロビジョナーに共通する重要なポイントを説明します。

## 設定

まず、 `config.vm.provision` メソッド呼び出しで [Vagrantfile](http://docs.vagrantup.com/v2/vagrantfile/) 内に各プロビジョナーが設定されます。たとえば、次の Vagrantfile ではシェルがプロビジョニングを行います：

    Vagrant.configure("2") do |config|
      # ... other configuration  
      config.vm.provision :shell, :inline => "echo hello"
    end

各プロビジョナーは `:shell` のような識別子を持っています。これはプロビジョニング設定の第1パラメータとして使用されます。これに続くパラメーターは、特定のプロビジョナーで設定を行なうための基本的なキー/バリューです。基本的なキー/バリューの代わりに、代入文のような構文の Ruby ブロックを使用することもできます。次は前の例を効率的にしたものです：

    Vagrant.configure("2") do |config|
      # ... other configuration  
      config.vm.provision :shell do |s|
        s.inline = "echo hello"
      end
    end

ブロックベース構文の利点は、オプションの組が多くなっても読みやすいことです。さらに、 Chef のようないくつかのプロビジョナーは、キー/バリューではできない設定を容易に行なうために、ブロック内で呼び出すことができる特別なメソッドを持っています。


## 複数のプロビジョナー

複数の `config.vm.provision` メソッドを使うと、複数のプロビジョナーを定義できます。これらのプロビジョナーは定義された順序で実行されます。これはさまざまな場面で有用です。最も一般的な例は、シェル·スクリプトがシステムのいくつかをブートストラップすることで、別のプロビジョナーが後で引き継ぐことができるようになります。


## プロビジョナーの実行

プロビジョナーの実行には、次の3つのケースがあります： `vagrant up` 、 `vagrant reload` 、 `vagrant provision`

プロビジョナーを実行したくない場合は、 `up` や `reload` に `--no-provision` フラグを渡します。

複数のプロビジョナーを持っていて、特定のプロビジョナーを実行したい場合は、 `--provision-with` フラグを使用します。たとえば、シェルと Puppet を持っていて、シェルだけを実行したい場合は、 `vagrant provision --provision-with shell` とします。

