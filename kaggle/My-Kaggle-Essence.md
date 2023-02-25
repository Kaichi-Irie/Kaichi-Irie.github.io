# 自分的Kaggleの心得
## Pathは最初からきちんと変数に。
* どうせKaggle notebookだけじゃ足りないので、Kaggle notebook以外でも（最低限）同じように動くnotebookにする。
  * `INPUT_DIR = "/kaggle/input"`
* pathの結合は、必ず`os.path.join(PATH1,PATH2)`
  * `from os.path import join as j`でもいいかも？

## モデル管理はW&B、もしくは`now`&`preffix`
* ベースラインのノートブックに依存するが、WandBをササっと実装できたら理想。
* 時間がない時は、`{preffix}+{now}+{model_name} `で保存。

## まず、preprocess->train->infer->submitのパイプラインを自分で再現すること。
* コンペによっては、部分ごとに別の人のノートブックを使うことになるが、それらをまず統合＆submitまでするのを第一優先に。
* 訓練済みモデルや、前処理済みデータセットは用意されている状態で、他の部分だけを自分でいじってsubmitしがちだが、どうせ別の部分もいじることになる＆いじることになって初めて全体のパイプラインを通すことに苦労しがちなので。
* でも、依拠するノートブックを変えた時に、骨折り損になるかも（？）
  * パイプラインを組みやすい形を意識して、各部分が構成されているはずなので、結局骨折り損にはならない（？）