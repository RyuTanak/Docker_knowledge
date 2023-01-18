# Dockerの基本コマンド  

## その前に  

今回ローカル環境にDockerをインストール出来なかったため  
クラウド上のDockerを使用する。  

Udemyで紹介されたもの→[Docker Hub](https://www.docker.com/play-with-docker/)  
Docker Hubのアカウントを作成することで、利用することができる。  
だた、1日4時間しか使用できないと、使用制限付き  

GithubでDockerを利用する。  
Gituhbでログインしたら画面上のメニューから「Codespace」を選択する。  
右上の「New codespace」をクリック。  
レポジトリを選択するので、任意のレポジトリを選択し、「Create codespace」をクリック  
すると、ブラウザ上でVscodeが起動するので、Vscodeのターミナル画面でDockerを使用することができる。  

## docker run  

dockerコンテナを1つ起動するコマンド  
→docker imageがない場合、docker hubから自動で取得  

```
docker run イメージ名
```
今回は、docker run hello-worldを実行  
コンソールの中にHello From Docker!と出ればOK  

## docker ps  

起動中のコンテナを表示するコマンド  
-a オプションをつけると、停止中のコンテナも表示される  

先ほど起動したコンテナを見てみる。  
![image](./image/1.png)  
「docker ps」のみだと一覧にコンテナは表示されない  
　→コンテナはプロセスが動いていないと停止するという特性を持つ。  
   hello-worldコンテナはコンソールに「Hello From Docker」と表示するのみのコンテナのため  
   プロセスはすぐに止まる。  
-a をつけることで、表示される。  

### docker runのオプションコマンド  

先ほどのhello-worldコンテナの名前を変更する。  
```
docker run --name tanaka-udemy hello-world
```





