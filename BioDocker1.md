#BioDockerへの道

20150307 Hidemasa Bono \<bonohu@gmail.com\>

遅ればせながら、Markdown勉強中なので、今回はこのスタイルでw

## なぜにDocker?
* [🐶](https://twitter.com/inut)
	* 鼻が利く彼が何やら最近Docker推し
		* 解析時に使った「環境」を「コンテナ」として配布可能
			* [DockerHub](https://hub.docker.com/)
		* 実行手続きの書かれたDockerfile
			* [Dockerfileの例(hmmsearch)](https://registry.hub.docker.com/u/bonohu/debian-hmmsearch2/)
		* →データ解析の再現性担保
* [Illumina BaseSpace developers' meeting in Japan](http://www.illuminakk.co.jp/events/seminar_japan.ilmn) (DBCLS柏 2014/10/29-30)
* [国内版バイオハッカソン BH14.14](http://wiki.lifesciencedb.jp/mw/BH14.14) (札幌市定山渓 2015/2/2-6)
	* リトリート的に何をやるか議論した結果、[Docker野郎Dチーム](http://wiki.lifesciencedb.jp/mw/BH14.14/Docker)結成

## 動かすための準備

Mac上で動かすには、Xcodeを入れた上で、Homebrewをインストール

### Homebrew

* git `brew install git`
* cask `brew tap phinze/cask; brew install brew-cask`
* vagrant `brew cask install vagrant`
* virtualbox `brew cask install virtualbox`

### coreos

1. `mkdir docker`
2. `cd docker`
3. `https://github.com/coreos/coreos-vagrant`
4. `cd coreos-vagrant`
5. `vagrant up`
6. `vagrant ssh`

coreos にログインできた?

### docker run test

coreos> `docker run -it inutano/cmatrix`

## 自分でも書いてみた

`hmmemit` in [HMMER package](http://hmmer.janelia.org/) 
https://github.com/bonohu/hmmemit/blob/master/Dockerfile

coreos> `docker run -it bonohu/hmmemit`

## その後に

coreos> `exit`
`vagrant status`

- まだcoreosはrunningであることがわかる
- 再度`vagrant ssh`でcoreosに入れる
- 終了させるには、以下の様に

`vagrant halt`
`vagrant status`

poweroff になったはず。



