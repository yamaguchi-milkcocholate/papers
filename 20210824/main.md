## TabNet: Attentive Interpretable Tabular Learning

[arXiv](https://arxiv.org/abs/1908.07442)



### 概要

TabNetはテーブルデータに対して、入力データ毎に特徴選択と情報抽出を繰り返しながら、勾配ベースで学習が可能なモデルである．決定木のような解釈可能性をもちつつ、実験では勾配ブースティング決定木や多層ニューラルネットに比べて性能向上が確認できた．

### TabNet

TabNetは複数のDecision stepを繰り返す．Decision stepはFeature selection（特徴選択）とInput processing（情報抽出）から成る．各ステップでは、入力データの中からある事柄に関係する特徴を選択して、情報を抽出することが期待される．Figure 1は、ステップ1で職業について、ステップ2で資産投資について、情報を抽出しており、それらの情報から年収を予測する例である．

<img src="/Users/teppei/Documents/GitHub/papers/20210824/images/fig1.png" style="zoom:40%;" />

各Decision stepでは、前ステップからの情報と入力データから特徴を選択する（Mask）．各ステップで抽出された情報を結合して最終的な出力が得られる（Output）．また、各ステップのMaskと抽出された情報から、その入力データにおける特徴量の影響度が得られる（Feature attirbutes）．この特徴量の影響度がTabnetのもつ解釈可能性である．

<img src="/Users/teppei/Documents/GitHub/papers/20210824/images/fig2.png" style="zoom:40%;" />

情報抽出部（Feature transformer）の前半では全ステップで重みを共有しており、ロバスト性やメモリや学習時間の効率性の面で効果的である．特徴選択部（Attentive transformer）ではSoftmax関数よりも疎なベクトルが得られるSparsemaxを採用している．

<img src="/Users/teppei/Documents/GitHub/papers/20210824/images/fig3.png" style="zoom:40%;" />

### 実験

Forest Cover Typeという実世界データセットでの結果．

<img src="/Users/teppei/Documents/GitHub/papers/20210824/images/fig4.png" style="zoom:40%;" />

また、自然言語処理のように事前学習により性能向上が確認できた．

<img src="/Users/teppei/Documents/GitHub/papers/20210824/images/fig5.png" style="zoom:40%;" />

<img src="/Users/teppei/Documents/GitHub/papers/20210824/images/fig6.png" style="zoom:40%;" />