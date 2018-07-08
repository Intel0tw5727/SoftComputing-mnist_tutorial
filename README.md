<!-- $theme: default -->

# Keras(Tensorflow)を使う！

---

## Tensorflowとは

+ Google製の数値計算ライブラリ(一般的には深層学習ライブラリとして浸透)
+ 2018 Jul 時点でv1.8.0
	+ 行列演算
    + 「計算グラフ」に基づいたコード構造
	+ DeepLearningに関する関数やクラスが豊富

+ ですが
    + **初心者にはソースを書くのが難しい！！**

---

## Kerasとは

+ Tensolflowをバックエンドに，直感的な記述でニューラルネットを記述するために生まれたモジュール
+ 開発者の@fcholletさんいわく「Tensorflowは使いやすいが計算グラフの理解のところが難しくて万人向けではない」
+ 「できるだけ多くの人にDeepLearningに触れてもらいたい」という開発理念の下に生まれたのがKerasモジュール

> 引用元
> http://tjo.hatenablog.com/entry/2016/06/09/190000

---

## Keras(Tensorflow)の動作環境

+ Python3.5以上 推奨
	+ Python2でもできるけど2020年にサポートが打ち切られるため3系を推奨！(3系最新は3.6.6, 3.7.0) 
+ pyenv というPythonのバージョン管理ソフトによる管理
+ モジュール管理ソフト
	+ pip
	+ conda(4.2.7推奨,4.3以降はなぜかSierraでうまく動作しない)

---
## MacでKeras(Tensorflow)を動かすための環境構築
### pyenvのインストール
```
brew install pyenv
```

し終わったら，zshの人は`$HOME/.zshrc`,bashの人は`$HOME/.bashrc`もしくは`$HOME/.bash_profile`に以下を記述して保存して`source 設定ファイル`する．

```
export PYENV_ROOT=${HOME}/.pyenv
if [ -d "${PYENV_ROOT}" ]; then
	export PATH=${PYENV_ROOT}/bin:$PATH
	eval "$(pyenv init -)"
fi
```
```
source ~/.zshrc
```

---

### Anacondaのインストール
+ AnacondaはPythonと数値解析関連のモジュールを一括でインストールしてくれる非常に優秀なディストリビューション．
+ 数値解析に必要なnumpyやpandas,グラフ描画のmatplotlib等様々なライブラリがAnacondaにまとまっている．
```
pyenv install anaconda3-5.1.0
```

Pythonとモジュールを一括で入れるので少々時間がかかる．


### pyenv内のpython(Anaconda3)を使うための設定

```
pyenv global anaconda3-5.1.0
pyenv rehash
```

---
ターミナルで```python```を実行した際に以下のようになっていればOK．
```python
Python 3.6.2 |Anaconda, Inc.| 
(default, Sep 21 2017, 18:29:43)
[GCC 4.2.1 Compatible Clang 4.0.1
(tags/RELEASE_401/final)] on darwin
Type "help", "copyright", "credits" 
or "license" for more information.
```
(便宜上改行)

---

### Keras(Tensorflow)のインストール

anacondaをインストールし終えたら、今回の実行環境を作るため以下のコマンドを実行する。

```
pip install jupyter tensorflow keras matplotlib dask
```

インストールが終わったら，ターミナルで`python`を起動し，
```python
import keras
import tensorflow
```

で問題なくモジュールが読み込まれるかを確認する．エラーが出なければ環境構築はおしまい．

---

### Jupyter notebookの起動

```
jupyter notebook 
```

をターミナルに打ち込んで起動。

既にあるディレクトリやファイルを実行する場合は，

```
jupyter notebook /path/to/file.ipynb
```

+ 例
```
jupyter notebook SoftComputing_ml_tutorial/
MNISTForMachineLearningBeginners.ipynb
```

---

ブラウザが起動してnotebookが確認ができる.フォルダ指定する際も同様．もしも起動しないときには

![](/Users/Kakutofu/Desktop/スクリーンショット%202018-01-15%2014.38.58.png)

使用しているブラウザにアドレスとトークンをコピペして見よう。
