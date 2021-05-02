# （いらすとや）モールモール

## Overview

[いらすとや](https://www.irasutoya.com/) のフリー素材画像だけで作った JavaScript 版『モールモール』です。
画像は全ていらすとやから動的にロードするので、ゲーム実行時に必要なファイルは index.html のみです（インターネット環境は必要です）。

## モールモール

1985年に当時のビクター音楽産業（現JVCケンウッド・ビクターエンタテインメント）からリリースされたパソコン向けパズルゲームです。
当初は MSX 向けにリリースされましたが、後に多くの機種に移植されました。また「モールモール２」など続編の展開もありました。

いわゆる「敵キャラ」の概念がなく、詰将棋のようにじっくり考えて解くゲームです。
また（ギブアップ時などを除くと）４方向の矢印キーだけでシンプルに操作できるゲームでした。

「モールモール２」ですが、以下のページで詳しく紹介されていました：

http://fm-7.com/museum/softhouse/victor/510201400.html


## モールモールのルール

- 主人公の MOLE（もぐら）を上下左右に動かして、**画面内にあるすべてのイモを取り終わってからゴール** にたどり着くことが目的です。

    - 面をクリアすると次の面が始まります。最終面をクリアするとゲームは終了します。

    - この移植版では任意の面を選んでスタートすることができます。

    - 途中で諦める場合は "retry" ボタンをクリックします（その面の初めからやり直しができます）。

- 画面には上から下に向かう重力が存在します。MOLE の下に何もない状態になると MOLE は１つ下に落ちてしまいます。下に何かがある状態になるか、最下段まで落ちていきます。

- 画面の外へは行けません（画面サイズは面ごとに異なります）。また目的方向に石があると移動できません。

- MOLE は左右および下方向へは（画面外であったり、石があったりしなければ）自由に移動できます。ただし上方向へ行くにははしごが必要です。MOLE がはしごと重なっている場合のみ（そして上に石がない場合のみ）上へ移動できます。

- MOLE とイモ、または土が重なると、その場所は何もない空間になります。

- MOLE の真上に石がある状態から MOLE が移動すると、移動前の場所にその石が落ちてきます。また落ちてきた石があった場所はなにもない空間になります。

    - 落ちてくる石の更に上にも石があった場合、その石も同時に落ちてきます。

    - 石は横方向へは動きません。

    - 面によってはうまく石を動かさないとクリアできないことがあります。



## 面エディット

ゲーム画面内の **edit** ボタンを押すと **面エディトモード** に移行します。

面エディットモードでは以下のキー操作が可能です：

| キー | 意味 |
|---|----------------|
| ↑ | カーソルを上に |
| ↓ | カーソルを下に |
| ← | カーソルを左に |
| → | カーソルを右に |
| Shift + ↑ | 面の高さを１つ減らす（最小４） |
| Shift + ↓ | 面の高さを１つ増やす（最大２０） |
| Shift + ← | 面の幅を１つ減らす（最小４） |
| Shift + → | 面の幅を１つ増やす（最大２０） |
| Shift + SPACE | カーソル位置のコマを変更する |

カーソル位置のコマは以下の順に変わっていきます：

| # | 意味 |
|---|----------------|
| 0 | なにもない空間 |
| 1 | ドア（ゴール） |
| 2 | はしご　　　　 |
| 3 | 土　　　　　　 |
| 4 | 石　　　　　　 |
| 5 | いも　　　　　 |

面エディットモード内で **play** ボタンをクリックすると、左上にモールが配置された状態で編集した面を実際にプレイすることができます。なお、この時の URL(https://dotnsf.github.io/molemole/?board=*****) は他の人に共有することが可能です。


## 外部ファイル

現行バージョンでは面データを外部ファイルとして用意し、起動時の URL パラメータで指定することで取り込むことができます。

外部ファイルは以下のような JSON ３次配列データです（上述の board 変数と同じフォーマットです。以下のデータは２面分のデータを保持しています）：

```
[
  [
    [ 0, 0, 0, 1 ],
    [ 2, 3, 4, 2 ],
    [ 2, 4, 4, 2 ],
    [ 2, 5, 5, 2 ]
  ],
  [
    [ 0, 4, 4, 0 ],
    [ 3, 3, 3, 3 ],
    [ 3, 3, 3, 3 ],
    [ 3, 3, 3, 1 ],
    [ 2, 5, 5, 3 ]
  ]
]
```

仮にこのファイル名が sample.json だった場合、以下のように URL パラメータを指定することで取り込むことが可能です：

```
https://dotnsf.github.io/molemole/?file=sample.json
```

## いらすとやから利用するイラスト

この移植版モールモールで利用している画像はすべて [「いらすとや」](https://www.irasutoya.com/) 様で公開されているものをそのまま使っています（一部のみ切り取ったり、別の色を加えたりはしていません）。利用している画像の一覧は以下のとおりです：

- ドア：　いろいろな状態のドアのイラスト https://www.irasutoya.com/2016/07/blog-post_832.html

- はしご：　木のはしごのイラスト https://www.irasutoya.com/2018/12/blog-post_0.html

- 土：　デジタルデータ風の背景素材（緑） https://www.irasutoya.com/2017/04/blog-post_62.html

- 石：　石垣のイラスト（背景素材） https://www.irasutoya.com/2018/07/blog-post_333.html

- イモ：　スネークフルーツのイラスト https://www.irasutoya.com/2015/08/blog-post_972.html

- 主人公：　もぐらのイラスト https://www.irasutoya.com/2013/01/blog-post_3363.html

## Copyright

2019 [K.Kimura @ Juge.Me](https://github.com/dotnsf) all rights reserved.
