# BOX ファイルフォーマット

過去、 Box は VirtualBox がエクスポートする [tar ファイル](http://en.wikipedia.org/wiki/Tar_(computing))だけでした。Vagrant は複数の Provider をサポートしたため、現在 Box ファイルは各 Provider 毎に異なる tar ファイルになっています。まだ Box は tar ファイルですが、現在、オプションで [gzip](http://en.wikipedia.org/wiki/Gzip) 圧縮もされます。

Vagrant 1.0.x と VirtualBox のために作られた Box ファイルは Vagrant 1.1 + と VirtualBox Provider でも動作し続けます。

Box 内に必要な唯一のファイルは "metadata.json" ファイルです。この [JSON](http://www.json.org/) ファイルは Box に関するメタデータを含むことのできるトップレベルのオブジェクトを持っています。Vagrant ではメタデータに "provider" キーと そのBox の Provider の名前が必要です。

VirtualBox の Box の "metadata.json" ファイル：

```
{
  "provider": "virtualbox"
}
```

Box を追加するとき、 metadata.json ファイルが存在しない、または少なくとも "provider" キーを持つ有効な JSON が含まれていないファイルの場合は、 Vagrant はエラーになります。

