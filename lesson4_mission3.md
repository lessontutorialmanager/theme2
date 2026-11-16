# 変数で並べよう！③

```blocks
player.onChat("run", function (num1) {
    blocks.place(WHITE_TULIP, world(-81, 81, num1))
    blocks.place(ORANGE_TULIP, world(-83, 81, num1))
    blocks.place(RED_TULIP, world(-85, 81, num1))
})
```

```template
player.onChat("run", function () {})
```

## チューリップを並べよう！ @unplugged
変数で座標を指定して、チューリップを並べよう！
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson4/L4_complete3.png">



## 目標
変数で座標を指定して、チューリップを並べよう！
・チャットコマンドで「run ○」と入力すると、指定した座標にチューリップが設置される
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson4/L4_set3.gif">



## 座標を考える
チューリップを並べる座標は、18か所あります
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson4/L4_coordinates3.png">
<br></br>
18回座標を書き換えるのは大変なので、画像のように3か所をひとまとめにして、Z座標を変数で指定できるようにしよう！



## Step1 ブロックを設置する
指定した座標にブロックを置く準備をしよう
・``||blocks.ブロック||``から``||blocks.～を(~0, ~0, ~0)に置く||``を取り出してワークスペースの``||player.チャットコマンドrunを入力した時||``にはめ込む
・ブロックの種類をグロウストーンにする
・``||positions.ポジション||``から``||positions.ワールド(0, 0, 0)||``を取り出してワークスペースの``||blocks.～を(~0, ~0, ~0)に置く||``にはめ込む




## Step2 変数を作る
チャットで``||player.run ○||``と入力できるように変数を作成しよう
・``||player.チャットコマンドrunを入力した時||``の右はしにある、⊕を1回押す




## Step3 座標を設定する
ブロックを置く座標を指定しよう！
画像をもとに、座標を自分で考えてプログラミングしよう！



## 実行しよう！
プログラミングができあがったら、▶ボタンを押して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、チャットで「run ○」と入力して、チューリップを○で指定したZ座標の位置に並べよう
○に入れる数字は、下の画像をもとに自分で考えてみよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson4/L4_coordinates3.png">
<br></br>
できあがったのを確認したら、研究者に話しかけよう
座標をどうすれば良いか分からないときは、ヒントを見てみよう！

```blocks
player.onChat("run", function (num1) {
    blocks.place(WHITE_TULIP, world(-81, 81, num1))
    blocks.place(ORANGE_TULIP, world(-83, 81, num1))
    blocks.place(RED_TULIP, world(-85, 81, num1))
})
```
