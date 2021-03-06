# 20170407
## 自然言語処理
* 分かち書き
 - 日本語などの語句と語句の間に空白のない言語に対して，空白を埋め込む方法．

* ベタな下処理
 1. wikipediaなどから大量のテキストデータを入手
 2. wp2txtなどでノイズを除去
 3. mecabを使い分かち書き
 4. mecab辞書に単語の登録

# 20170409
## imagemagick
### フォルダ内にある画像全体に対しての正規化

```
for file in `ls`; do convert ${file} -equalize ${file}; done
```

# 20170410
## 機械学習

* オフライン学習
 - データを与え機械学習からモデルを作成し，出力されたモデルから再びデータを与え評価を行う方法．

* オンライン学習
 - オフライン学習とは違い，データを学習するたびにモデルが更新される方法．

# 20170414
## OOPについて
* プログラムが異常終了→ガベージコレクションを疑う

# 20170418
## 異常検知入門

異常検知モデルの構築の構築は概ね以下の3ステップで行う．

* 分布推定
 - 正常のモデルを作る．例えば，身長と体重に関するばらつきを含んだモデル(確率分布)を作る．

* 異常度の定義
 - 正常からのずれの度合い（異常度）を定義する．先の例に合わせると，身長と体重のバランスが崩れている人を異常度を持つ人とする．

* 閾値の設定
 - 異常度がある値を超えたら異常と判定するような閾値を設定する．

### 確率分布

正常モデルを作るためには，以下の作業で行う．

* 未知パラメータを含む確率分布モデルを仮定する

* 未知パラメータをデータに合わせこむ

### 数学の小窓

* 標準偏差
 - データの散らばり具合を表す指標．
 - 標準偏差が大きい→平均uから遠く離れたデータが多い→散らばり大
 - 標準偏差が小さい→平均uに近いデータが多い→散らばり小

データの散らばり具合を表す指標として，他にも「分散」がある．

* 分散
 - 分散も標準偏差と同様，散らばり具合を表す指標．
 - 分散が大きい→散らばり大
 - 分散が小さい→散らばり小

確率分布に対して多くは標準偏差ではなく分散が用いられることが多い．なぜなら，分散は計算が楽でありなおかつ綺麗な形で収まることが多いから．

### 機械学習で確率分布を求める

データから正常モデルを構築するには対象となる系の性質において次の問題を解く必要がある．

* 密度推定問題
* 次元削減問題
* 回帰問題
* 分類問題
* 時系列解析問題

機械学習で異常検知を行う場合はこれらの問題を駆使して解き，異常度と閾値に応じた適切な形で求める．

# 20170419
## 異常検知入門

* 正規分布
 - 平均と分散が固定された時に，最も自然で偏見のない分布．

# 20170421
## couseraメモ
* 機会学習におけるシータの扱いとは (調べる )
* シグモイド関数とは(調べる)
 - シータを求めることによってロジスティック回帰における閾値を求めることができる．
 - 決定境界を知ることによって，ロジスティック回帰の仮説関数が何をしているのかを理解することができる．

 - 最適化の目的関数→コスト関数

# tensorflow基礎
## データ構造について

スカラを使う上で以下のデータ構造について知っておくべきである．

* スカラ
 - 0次元配列であり，スカラやマトリックスに掛かる係数として使う．

* ベクトル
 - 1次元配列．

* マトリックス
 - 2次元配列．

これらを複合して，テンソルという多次元配列を作り，tensorflowに投げるデータとする．

# 20170422
## tensorflow基礎

* ソフトマックス関数
 - 証跡を元に，その対象データが各分類クラスである確率を出力する．
 - mnistを例にとると．1つの画像に対して0~9それぞれの数字である確率を出力する．
 - その確率の合計は常に1になるように正規化されている．
 - 画像データから特定の分類クラス(数字)に対する証跡を算出するステップ．
 - その証跡を確率へ変換するステップ．

損失関数，引いては交差エントロピーがよくわからないので要確認

# 20170426
## pythonテクニック

```python
In [35]: hoge = np.arange(10)

In [36]: print(hoge)
[0 1 2 3 4 5 6 7 8 9]

In [37]: aryFlag = (hoge % 2 == 0)

In [38]: print(aryFlag)
[ True False  True False  True False  True False  True False]

In [39]: foo = hoge[aryFlag]

In [40]: print(foo)
[0 2 4 6 8]
```
