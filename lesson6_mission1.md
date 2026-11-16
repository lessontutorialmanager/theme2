# 変数を使って建築しよう！①

```blocks
let 作り始める位置: Position = null
player.onChat("set", function () {
    作り始める位置 = player.position()
})
player.onChat("run", function () {
    blocks.fill(
    SMOOTH_SANDSTONE,
    positions.add(
    作り始める位置,
    pos(1, 0, 1)
    ),
    positions.add(
    作り始める位置,
    pos(8, 7, 8)
    ),
    FillOperation.Hollow
    )
})

```

```template
player.onChat("set", function () {})
player.onChat("run", function () {})
```

## 変数を使って建築しよう！ @unplugged
変数を使って建築してみよう！
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson6/L6_complete1.gif">



## 目標
まずはこれから作るものの形を確認しよう！
・チャットで「set」と入力したら、プレイヤーが立っている位置のワールド座標が変数に入る
・チャットで「run」と入力したら、変数に入った座標を基準にして、家の壁と屋根ができるようにプログラミングする
・大きさは、作り始めの位置から東に8ブロック、上に8ブロック、南に8ブロックにする
・滑らかな砂岩で作る
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson6/L6_complete1.gif">



## 変数を使おう！
今回は変数に場所を入れてみよう！
・「作り始める位置」という変数に、プレイヤーが立っている位置の座標を入れる



## Step1 変数を作ろう
まずは、座標を入れるための変数を作ろう
・``||variable.変数||``を開いて、「変数を追加する」を押す
・変数の名前を「作り始める位置」にして、「OK」を押す
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson6/L6_make_variable.gif">
<br></br>
これで変数をひとつ作ることができました！




## Step2 変数に座標を入れよう
作った変数に、プレイヤーの位置の座標を入れよう
・``||variable.変数||``を開いて、``||variable.変数 作り始める位置を0にする||``を取り出し、``||player.チャットコマンドsetを入力した時||``にはめ込む
・``||player.プレイヤー||``を開いて``||player.プレイヤーの位置||``を取り出し、``||variable.変数 作り始める位置を0にする||``にはめ込む
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson6/L6_set_variable.gif">

```blocks
let 作り始める位置: Position = null
player.onChat("set", function () {
    作り始める位置 = player.position()
})
```



## 屋根と壁を作る
次に、チャットで「run」と入力すると、``||variable.変数 作り始める位置||``に入った座標から、屋根と壁を作るプログラムを作っていきましょう！



## Step3 ブロックを並べる準備
``||variable.変数 作り始める位置||``を基準にしてブロックを並べられるように、まずは準備をしよう
・``||blocks.ブロック||``を開いて、``||blocks.ブロックを並べる||``を取り出し、``||player.チャットコマンドrunを入力した時||``にはめ込む
・ブロックの種類を「滑らかな砂岩」にする
・``||positions.ポジション||``から``||positions.(~0, ~0, ~0) + (~0, ~0, ~0)||``を取り出して、「範囲の始まり」「範囲の終わり」にはめ込む
・``||variable.変数||``から``||variable.作り始める位置||``を2つ取り出して、「範囲の始まり」「範囲の終わり」の``||positions.(~0, ~0, ~0) + (~0, ~0, ~0)||``の左側の``||positions.(~0, ~0, ~0)||``にはめ込む
・モードを「中空」にする
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson6/L6_fill.gif">
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson6/L6_fill.png">

```blocks
player.onChat("run", function () {
    blocks.fill(
    SMOOTH_SANDSTONE,
    positions.add(
    作り始める位置,
    pos(0, 0, 0)
    ),
    positions.add(
    作り始める位置,
    pos(0, 0, 0)
    ),
    FillOperation.Hollow
    )
})
```



## 座標を考えよう
テラコッタの位置を基準にして、下のようにたて8ブロック、横8ブロック並べるには、どのように座標を設定すれば良いか考えよう！
今回は、高さは0から7に設定しよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson6/L6_coordinates1.png">



## Step4 座標を設定しよう
考えたことをもとに、``||blocks.ブロックを並べる||``の範囲の始まりと終わりを設定しよう
・範囲の始まりを、``||positions.(作り始める位置) + (~1, ~0, ~1)||``にする
・範囲の終わりを、``||positions.(作り始める位置) + (~8, ~7, ~8)||``にする

```blocks
player.onChat("run", function () {
    blocks.fill(
    SMOOTH_SANDSTONE,
    positions.add(
    作り始める位置,
    pos(1, 0, 1)
    ),
    positions.add(
    作り始める位置,
    pos(8, 7, 8)
    ),
    FillOperation.Hollow
    )
})
```



## 実行しよう！
プログラミングができあがったら、▶ボタンを押して実行しよう
ゲーム画面にもどったら、テラコッタの上に立ってチャットで「set」と入力しよう
その後、少しはなれてチャットで「run」と入力しよう
もし建てる位置がずれてしまったときは、お願いされた村人に話しかけよう
建築が完成したら、村人に話しかけよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson6/L6_complete1.gif">



