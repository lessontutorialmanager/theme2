# 変数で並べよう！➁

```blocks
player.onChat("run", function (num1) {
    blocks.place(CHEST, world(-80, 75, num1))
    blocks.place(CHEST, world(-78, 75, num1))
    blocks.place(CHEST, world(-76, 75, num1))
})
```

```template
player.onChat("run", function () {})
```

## チェストを並べよう！ @unplugged
変数で座標を指定して、チェストを並べよう！
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson4/L4_complete2.png">



## 目標
変数で座標を指定して、チェストを並べよう！
・チャットコマンドで「run ○」と入力すると、指定した座標にチェストが設置される
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson4/L4_set2.gif">



## 座標を考える
チェストを並べる座標は、6か所あります
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson4/L4_coordinates2.png">
<br></br>
6回座標を書き換えるのは大変なので、画像のように3か所をひとまとめにして、Z座標を変数で指定できるようにしよう！



## Step1 ブロックを設置する
指定した座標にブロックを置く準備をしよう
・``||blocks.ブロック||``から``||blocks.～を(~0, ~0, ~0)に置く||``を取り出してワークスペースの``||player.チャットコマンドrunを入力した時||``にはめ込む
・ブロックの種類をグロウストーンにする
・``||positions.ポジション||``から``||positions.ワールド(0, 0, 0)||``を取り出してワークスペースの``||blocks.～を(~0, ~0, ~0)に置く||``にはめ込む

```blocks
player.onChat("run", function () {
    blocks.place(GLOWSTONE, world(0, 0, 0))
})
```



## Step2 変数を作る
チャットで``||player.run ○||``と入力できるように変数を作成しよう
・``||player.チャットコマンドrunを入力した時||``の右はしにある、⊕を1回押す

```blocks
player.onChat("run", function (num1) {
    blocks.place(GLOWSTONE, world(0, 0, 0))
})
```



## Step3 座標を設定する①
ブロックを置く座標を指定しよう！
・ブロックを置く座標を、``||positions.ワールド(-80, 75, num1)||``となるように設定しよう！

```blocks
player.onChat("run", function (num1) {
    blocks.place(GLOWSTONE, world(-80, 75, num1))
})
```



## Step4 座標を設定する➁
同じように、あと2つグロウストーンを置けるようにプログラムしよう
座標については、先ほどの画像をもとにして自分で考えてみよう！
・分からないときは、💡を押してヒントを見てみよう

```blocks
player.onChat("run", function (num1) {
    blocks.place(GLOWSTONE, world(-80, 75, num1))
    blocks.place(GLOWSTONE, world(-78, 75, num1))
    blocks.place(GLOWSTONE, world(-76, 75, num1))
})
```




## 実行しよう！
プログラミングができあがったら、▶ボタンを押して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、チャットで「run ○」と入力して、チェストを○で指定したZ座標の位置に並べよう
○に入れる数字は、下の画像をもとに自分で考えてみよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson4/L4_coordinates2.png">
<br></br>
できあがったのを確認したら、研究者に話しかけよう

