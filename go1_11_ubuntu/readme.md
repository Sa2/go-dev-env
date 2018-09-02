# Go build image

## Build image

```
docker build -t go-dev-env:go1.11-ubuntu ./
```

## Run container

コードを編集するならホスト側にもGolangをインストールしてホストで`go tool`をコンパイルする必要がある。
$GOPATH/binの中身はコンパイル済みのバイナリであるが故に、ホスト側でコンパイルしたものはゲストコンテナで実行できず、
ゲストコンテナでコンパイルしたものはホスト側では実行できない。

```
docker run -it -v <host $GOPATH/src>:/root/go/src --name go1_11-ubuntu -p 8080:8080 go-dev-env:go1.11-ubuntu
```

GOPATHは以下のコマンドで調べられる。

```
go env | grep GOPATH
```

デプロイすることなく開発だけの環境ならわざわざDockerでGoを開発するメリットは少なそう

## Container status

入れてるモジュールは無し

`GOPATH`は`/root/go/`にシンボリックリンクを貼ってある

上記のコマンド通りにコンテナを建てた場合`8080`をコンテナとホストで連携させている
