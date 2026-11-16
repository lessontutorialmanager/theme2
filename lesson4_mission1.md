# 変数で並べよう！①

```blocks
player.onChat("run", function (num1) {
    blocks.place(GLOWSTONE, world(-80, 79, num1))
    blocks.place(GLOWSTONE, world(-78, 79, num1))
    blocks.place(GLOWSTONE, world(-76, 79, num1))
})
```

```template
player.onChat("run", function () {})
```

## グロウストーンを並べよう！ @unplugged
変数で座標を指定して、グロウストーンを並べよう！
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson4/L4_complete1.png">



## 目標
変数で座標を指定して、グロウストーンを並べよう！
・チャットコマンドで「run ○」と入力すると、指定した座標にグロウストーンが設置される
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson4/L4_set1.gif">



## 座標を考える
グロウストーンを並べる座標は、6か所あります
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson4/L4_coordinates1.png">
<br></br>
6回座標を書き換えるのは大変なので、画像のように3か所をひとまとめにして、Z座標を変数で指定できるようにしよう！



## Step1 ブロックを設置する
指定した座標にブロックを置く準備をしよう
・``||blocks.ブロック||``から``||blocks.～を(~0, ~0, ~0)に置く||``を取り出してワークスペースの``||player.チャットコマンドrunを入力した時||``にはめ込む
・ブロックの種類をグロウストーンにする
・``||positions.ポジション||``から``||positions.ワールド(0, 0, 0)||``を取り出してワークスペースの``||blocks.～を(~0, ~0, ~0)に置く||``にはめ込む
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson4/L4_set_block.gif">
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson4/L4_position.gif">

```blocks
player.onChat("run", function () {
    blocks.place(GLOWSTONE, world(0, 0, 0))
})
```



## Step2 変数を作る
チャットで``||player.run ○||``と入力できるように変数を作成しよう
・``||player.チャットコマンドrunを入力した時||``の右はしにある、⊕を1回押す
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson4/L4_variable.gif">
<br></br>
これで、``||variables.num1||``という名前の変数ができました！

```blocks
player.onChat("run", function (num1) {
    blocks.place(GLOWSTONE, world(0, 0, 0))
})
```



## Step3 座標を設定する①
ブロックを置く座標を指定しよう！
・ブロックを置く座標を、``||positions.ワールド(-80, 79, num1)||``となるように設定しよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson4/L4_set_coordinates.gif">

```blocks
player.onChat("run", function (num1) {
    blocks.place(GLOWSTONE, world(-80, 79, num1))
})
```



## Step4 座標を設定する➁
同じように、あと2つグロウストーンを置けるようにプログラムしよう
・2つめの座標：``||positions.ワールド(-78, 79, num1)||``
・3つめの座標：``||positions.ワールド(-76, 79, num1)||``
・分からないときは、💡を押してヒントを見てみよう

```blocks
player.onChat("run", function (num1) {
    blocks.place(GLOWSTONE, world(-80, 79, num1))
    blocks.place(GLOWSTONE, world(-78, 79, num1))
    blocks.place(GLOWSTONE, world(-76, 79, num1))
})
```




## 実行しよう！
プログラミングができあがったら、▶ボタンを押して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、チャットで「run ○」と入力して、グロウストーンを○で指定したZ座標の位置に並べよう
○に入れる数字は、下の画像をもとに自分で考えてみよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson4/L4_coordinates1.png">
<br></br>
できあがったのを確認したら、研究者に話しかけよう

