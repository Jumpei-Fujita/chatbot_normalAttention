# chatbot_normalAttention

## データセットの作成
chatbotを作成するにあたり、questionとanswerのペアになっているデータセットを以下のサイト（kaggle）からダウンロードし用いた。
データセットのQandAの例は以下のとおりである。<br>
![model](https://github.com/Jumpei-Fujita/chatbot_normalAttention/blob/main/example.png)
### 前処理
大文字の削除、短縮系や特殊文字等の排除を行った。

## モデル構築
以下のようにSeq2SeqモデルにAttentionを追加した。<br>
![model](https://github.com/Jumpei-Fujita/chatbot_normalAttention/blob/main/chatbotNormalAttn.png)<br>


## 学習
VAEはEncoderによって平均と分散が出力され、それらに従う正規分布に従う乱数を生成する。その平均と分散を以下のような誤差関数により学習していく。
![loss](https://github.com/Jumpei-Fujita/mixing_music_by_VAE/blob/master/vaeloss.png)<br>
最適化手法はAdamを用いた。
以下は学習の様子である。<br>
![model](https://github.com/Jumpei-Fujita/mixing_music_by_VAE/blob/master/graph.png)

## 結果
歌うたいのバラッドの正規分布に従う乱数、渡月橋の正規分布に従う乱数をそれぞれ半分ずつ足した時の結果を以下に示す。<br>
![model](https://github.com/Jumpei-Fujita/mixing_music_by_VAE/blob/master/heat50.png)<br>


## コードの実行手順
multi_VAE.ipynbを訓練部分まで順に実行していく。<br>
その後２曲をミックスさせた音楽を生成する場合はtest関数を実行する。<br>
ここで、test関数の引数となるalphaは２曲の割合であり、0 ~ 1である。<br>
alphaが高ければ高いほど渡月橋に近い曲になる。


