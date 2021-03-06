# docker-sample-nginx

<kbd><img src="docker.png" width="800px"></kbd>

A sample nginx container for training

## 事前準備

以下のソフト、アカウントの準備を事前にしてください。
-Dockerのインストール、
　https://www.docker.com/products/docker-desktop
-Docker Hubのアカウント作成(Sign Up)
　https://hub.docker.com/
-Gitのインストール
  1. Homebrewのインストール　　https://brew.sh/index_ja
  2. HomeBrewを使ってgitをインストール  https://git-scm.com/download/mac
-Githubのアカウント作成(Sign Up)
 https://github.com/


## 研修

以下のコマンドでウェブサーバーを起動してみる(Dockerの動作確認)

```
$ docker run --rm -d -p 8080:80 --name web nginx
```

ブラウザーで　http://localhost:8080 にアクセスして動作確認

動作を停止

```
$ docker stop web
```

Githubびログイン後以下のアドレスにアクセス、レポジトリーをFork


```
https://github.com/osonoi/docker-sample-nginx.git
```

参考：　https://github.com/IBMDeveloperTokyo/DojoBasicLab/tree/master/Lab3_GitHub/Lab3-1_GitHub

このレポジトリーをClone

```
$ git clone https://github.com/(ご自分のアカウント名)/docker-sample-nginx.git
```

Dockerfile, indexを参照
イメージを作成

```
$ docker build -t webserver .
```

イメージを起動

```
$ docker run --rm -d -p 8080:80 --name web webserver
```

動作を停止

```
$ docker stop web
```

index.htmlを編集


イメージを作成

```
$ docker build -t webserver .
```

イメージを起動

```
$ docker run --rm -d -p 8080:80 --name web webserver
```

変更をgithubに反映

```
$ git init
$ git add index.html
$ git commit -m "コメント変更"
$ git push origin main
```


動作を停止

```
$ docker stop web
```

イメージをDockerHubにアップロード

```
$ docker login
$ docker tag webserver (ご自分のアカウント名)/webserver
$ docker push (ご自分のアカウント名)/webserver:latest

```

dockerHubでイメージを確認

https://hub.docker.com/

DockerHubのイメージで起動(できれば他のメンバーのアカウントのイメージを使って）

```
docker run --rm -d -p 8080:80 --name web (誰かののアカウント名)/webserver
```

