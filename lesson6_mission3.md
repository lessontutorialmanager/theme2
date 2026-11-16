# 変数を使って建築しよう！③

```blocks
let 作り始める位置: Position = null
player.onChat("set", function () {
    作り始める位置 = player.position()
})
player.onChat("run", function () {
    for (let index = 0; index < 2; index++) {
        blocks.fill(
        BRICKS,
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
        作り始める位置 = positions.add(
        作り始める位置,
        pos(7, 0, -5)
        )
    }
})
```

```template
player.onChat("set", function () {})
player.onChat("run", function () {})
```

## 変数を使って建築しよう！ @unplugged
変数を使って建築してみよう！
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson6/L6_complete3.gif">



## 目標
まずはこれから作るものの形を確認しよう！
・チャットで「set」と入力したら、プレイヤーが立っている位置のワールド座標が変数に入る
・チャットで「run」と入力したら、変数に入った座標を基準にして、家の壁と屋根ができるようにプログラミングする
・大きさは、作り始めの位置から東に8ブロック、上に8ブロック、南に15ブロックにする
・家の中を、下のように東に8ブロック、上に8ブロック、南に8ブロックの部屋2つに分ける
・レンガブロックで作る
下の図で全体の形を確認しよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson6/L6_coordinates3.png">



## 変数を使おう！
「作り始める位置」という変数に、プレイヤーが立っている位置の座標が入るようにプログラミングしていこう！



## Step1 変数を作ろう
まずは、座標を入れるための変数を作ろう
・``||variable.変数||``を開いて、「変数を追加する」を押す
・変数の名前を「作り始める位置」にして、「OK」を押す
<br></br>
これで変数をひとつ作ることができました！




## Step2 変数に座標を入れよう
作った変数に、プレイヤーの位置の座標を入れよう
・``||variable.変数||``を開いて、``||variable.変数 作り始める位置を0にする||``を取り出し、``||player.チャットコマンドsetを入力した時||``にはめ込む
・``||player.プレイヤー||``を開いて``||player.プレイヤーの位置||``を取り出し、``||variable.変数 作り始める位置を0にする||``にはめ込む

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
・ブロックの種類を「レンガブロック」にする
・``||positions.ポジション||``から``||positions.(~0, ~0, ~0) + (~0, ~0, ~0)||``を取り出して、「範囲の始まり」「範囲の終わり」にはめ込む
・``||variable.変数||``から``||variable.作り始める位置||``を2つ取り出して、「範囲の始まり」「範囲の終わり」の``||positions.(~0, ~0, ~0) + (~0, ~0, ~0)||``の左側の``||positions.(~0, ~0, ~0)||``にはめ込む
・モードを「中空」にする

```blocks
player.onChat("run", function () {
    blocks.fill(
    BRICKS,
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



## 2つの部屋の作り方を考えよう
テラコッタの位置を基準にして、下のようにたて8ブロック、横8ブロックの部屋を2つ作るにはどうすれば良いか考えよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson6/L6_coordinates3.png">
<br></br>
2つ目のミッションと同じように、2つ目の部屋の座標を考えるのはむずかしそうです…
こんなときは、``||variable.変数 作り始める位置||``に入った座標を動かせば、同じ形の部屋をくり返しで2つ作るだけで作ることができます！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson6/L6_shift_start.gif">



## Step4 座標を設定しよう
まずは、``||blocks.ブロックを並べる||``の範囲の始まりと終わりが、東に8ブロック、南に8ブロックになるように自分で考えて設定しよう
※今回は、高さは0～7ブロックに設定しよう

```blocks
player.onChat("run", function () {
    blocks.fill(
    BRICKS,
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



## 作り始める位置を移動させよう
テラコッタの位置から、次のブロックを並べる基準の位置まで、``||variable.変数 作り始める位置||``を動かそう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson6/L6_shift_start.png">
<br></br>
上の図をもとに、``||variable.変数 作り始める位置||``に入った座標を、どのように動かせば良いか考えよう



## Step5 変数に入った座標を動かす準備
``||variable.変数 作り始める位置||``に入った座標をを動かす準備をしよう
・``||variable.変数||``を開いて、``||variable.変数 作り始める位置を0にする||``を取り出し、``||player.チャットコマンドrunを入力した時||``にはめ込む
・``||positions.ポジション||``から``||positions.(~0, ~0, ~0) + (~0, ~0, ~0)||``を取り出して、``||variable.変数 作り始める位置を0にする||``にはめ込む
・``||variable.変数||``から``||variable.作り始める位置||``を取り出して、``||positions.(~0, ~0, ~0) + (~0, ~0, ~0)||``の左側の``||positions.(~0, ~0, ~0)||``にはめ込む
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson6/L6_change_variable1.gif">

```blocks
player.onChat("run", function () {
    blocks.fill(
    BRICKS,
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
    作り始める位置 = positions.add(
    作り始める位置,
    pos(0, 0, 0)
    )
})
```




## コードの意味
変数に入った座標を動かしたいときは、今回のようにコードを組み合わせます
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson6/L6_change_variable2.png">
<br></br>
``||positions.(~0, ~0, ~0)||``の数字を変えて、``||variable.作り始める位置||``に入った座標を動かそう！



## Step6 変数に入った座標を動かそう
``||variable.変数 作り始める位置||``に入った座標を、下の図をもとに自分で考えて動かそう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson6/L6_shift_start.png">

```blocks
player.onChat("run", function () {
    blocks.fill(
    BRICKS,
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
    作り始める位置 = positions.add(
    作り始める位置,
    pos(7, 0, -5)
    )
})
```



## ループさせよう
ここまでで、①``||variable.変数 作り始める位置||``に座標を入れる⇒➁1つ目の部屋を並べる⇒③``||variable.変数 作り始める位置||``の座標を動かす、というプログラムを作りました
2つ目の部屋の形は、1つ目の部屋の形と同じです！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson6/L6_coordinates3.png">
<br></br>
ということは…ここまでに作ったプログラムを2回くり返せば、もうひとつ``||blocks.ブロックを並べる||``を作らなくてもよくなります！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson6/L6_shift_start.gif">
<br></br>
ここからは、これまでに作ったプログラムをループさせよう！



## Step7 全体をくり返そう
``||loops.くりかえし||``を使って全体をループさせよう！
・``||loops.ループ||``から``||loops.くりかえし4回||``を取り出して、``||player.チャットコマンドrunを入力した時||``の中のプログラムをはさみ込む
・回数を2回にする
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson6/L6_repeat.gif">

```blocks
player.onChat("run", function () {
    for (let index = 0; index < 2; index++) {
        blocks.fill(
        BRICKS,
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
        作り始める位置 = positions.add(
        作り始める位置,
        pos(7, 0, -5)
        )
    }
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
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson6/L6_complete3.gif">



