<!-- $theme: default -->

# Keras(Tensorflow)を使う！

---

## Tensorflowとは

+ GoogleのDeepLearningFlamework
+ 2017 Apl 時点でv1.1
	+ 行列演算
	+ DeepLearningに関する関数
	+ 画像処理関数などなど

---

## Kerasとは

+ Tensolflowをバックエンドに，直感的な記述でニューラルネットを記述するために生まれたモジュール
+ 開発者の@fcholletさんいわく「Tensorflowは使いやすいが計算グラフの理解のところが難しくて万人向けではない」
+ 「できるだけ多くの人にDeeoLearningに触れてもらいたい」という開発理念の下に生まれたのがKerasモジュール

> 引用元
> http://tjo.hatenablog.com/entry/2016/06/09/190000

---

## Tensorflowの動作環境

+ Python2.7(.11) or 3.5(.2)以上 推奨
+ pyenv というPythonのバージョン管理ソフトによる管理
+ モジュール管理ソフト
	+ pip
	+ conda(4.2.7推奨,4.3以降はなぜかSierraでうまく動作しない)
+ (virtualenvやcondaによる仮想環境での実行)

---
## MacでKeras(Tensorflow)を動かすための環境構築
### pyenvのインストール
```
brew install pyenv
```

し終わったら，zshの人は```~/.zshrc```,bashの人は```~/.bash_profile```に以下を記述して保存して```source```する．

```
export PYENV_ROOT=${HOME}/.pyenv
if [ -d "${PYENV_ROOT}" ]; then
	export PATH=${PYENV_ROOT}/bin:$PATH
	eval "$(pyenv init -)"
fi
```

---

### Anacondaのインストール
+ AnacondaはPythonと数値解析関連のモジュールを一括でインストールしてくれる非常に優秀なディストリビューション．
+ 数値解析に必要なnumpyやpandas,グラフ描画のmatplotlib等様々なライブラリがAnacondaにまとまっている．
```
pyenv install anaconda3-4.3.1
```

Pythonとモジュールを一括で入れるので少々時間がかかる．


### pyenv内のpython(Anaconda3)を使うための設定

```
pyenv global anaconda3-4.3.1
pyenv rehash
```

---
ターミナルで```python```を実行した際に以下のようになっていればOK．
```python
Python 3.6.0 |Anaconda 4.3.1 (x86_64)| 
(default, Dec 23 2016, 13:19:00) 
[GCC 4.2.1 Compatible Apple LLVM 6.0 
(clang-600.0.57)] on darwin
Type "help", "copyright", "credits" or 
"license" for more information.
```
(便宜上改行)

---

### Keras(Tensorflow)をインストールする仮想環境の構築

condaはモジュール管理と仮想環境の管理をすることができる．今回はKeras(Tensorflow)用の仮想環境を準備する．

```
conda create -n keras python=3.6 jupyter graphviz
```

Proceed ([y]/n)? には y で進めていく．
仮想環境の構築が完了したら，早速立ち上げていく．

```
source ~/.pyenv/versions/anaconda3-4.3.1/bin/activate keras; pip install pydot
```
以上のコマンド(1行で)を実行する．インストールが完了し[COMPLETE]下に必要コマンドがあればそれも実行する．

その後
```
source ~/.pyenv/versions/anaconda3-4.3.1/bin/deactivate
```
して一度仮想環境を終了し，もう一度仮想環境を立ち上げる

---

もし今後もKeras(Tensorflow)を使っていくのであればzshrc or bash_profileに
```
alias keras_on='source ~/.pyenv/versions/anaconda3-4.3.1/bin/activate keras'
alias conda_off='source ~/.pyenv/versions/anaconda3-4.3.1/bin/deactivate'
```
を入れると楽になる．

(エイリアスした)コマンドを実行した際に，自分のターミナルの先頭に

```
(keras) ...
```

となっていれば仮想環境が起動できている状態なので，ここにKerasとTensorflowをインストールしていく．

---

### Keras(Tensorflow)のインストール
```
conda install -c conda-forge tensorflow
```
でTensorflowをインストール．その次に，

```
pip install keras h5py pydot
```
でKerasをインストール．今回はTensorflowを使用するため設定の変更は必要ないが，もしバックエンドを変更したい場合は以下を変更する．

```
~/.keras/keras.json
```
から

---

```
{
    "image_dim_ordering": "th",
    "floatx": "float32",
    "backend": "tensorflow",
    "epsilon": 1e-07
}
```
バックエンドを変更する．デフォルトではtensorflowになっているが，必要があればtheanoに変更できる．

インストールが終わったら，ターミナルで```python```を起動し，
```python
import keras
import tensorflow
```

で問題なくモジュールが読み込まれるかを確認する．エラーが出なければ環境構築はおしまい．
