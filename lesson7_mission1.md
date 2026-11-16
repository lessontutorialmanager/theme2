# 大きな建物を作ろう！

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
    pos(1, -1, 1)
    ),
    positions.add(
    作り始める位置,
    pos(13, -1, 13)
    ),
    FillOperation.Replace
    )
    for (let index = 0; index < 3; index++) {
        blocks.fill(
        GLASS,
        positions.add(
        作り始める位置,
        pos(1, 0, 1)
        ),
        positions.add(
        作り始める位置,
        pos(13, 4, 13)
        ),
        FillOperation.Replace
        )
        blocks.fill(
        AIR,
        positions.add(
        作り始める位置,
        pos(2, 0, 2)
        ),
        positions.add(
        作り始める位置,
        pos(12, 4, 12)
        ),
        FillOperation.Replace
        )
        blocks.fill(
        SMOOTH_SANDSTONE,
        positions.add(
        作り始める位置,
        pos(1, 5, 1)
        ),
        positions.add(
        作り始める位置,
        pos(13, 5, 13)
        ),
        FillOperation.Replace
        )
        blocks.fill(
        AIR,
        positions.add(
        作り始める位置,
        pos(8, 5, 10)
        ),
        positions.add(
        作り始める位置,
        pos(11, 5, 12)
        ),
        FillOperation.Replace
        )
        作り始める位置 = positions.add(
        作り始める位置,
        pos(0, 6, 0)
        )
    }
})


```

```template
player.onChat("run", function () {})
player.onChat("set", function () {})
```

## 変数を使って目印を作ろう！ @unplugged
変数を使って3階建ての建物を作ろう！
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_complete1.gif">



## 目標
まずはこれから作るものの形を確認しよう！
・チャットで「set」と入力した時、プレイヤーの位置を``||variables.変数 作り始める位置||``に入れる
・土台は、東に13ブロック、南に13ブロックの大きさで、滑らかな砂岩を並べる
・土台の上に、壁を作る→屋根を作る→壁を作る・・・とくりかえして、3階建てにする
最初に横から見た全体の形を確認しよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_from_side.png">



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



## 土台の座標を考えよう
作った変数の位置を基準にして、土台を並べよう
土台は、基準の位置よりも高さが1ブロック下に、東に13、南に13ブロックの大きさにしよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_basement.png">



## Step3 ブロックを並べよう
``||variable.変数 作り始める位置||``を基準にして、先ほど考えた通りにブロックを並べよう
・ブロックの種類：滑らかな砂岩
・範囲：``||variable.変数 作り始める位置||``を基準にして、東に13ブロック、南に13ブロック
※高さは-1にしよう

```blocks
player.onChat("run", function () {
    blocks.fill(
    SMOOTH_SANDSTONE,
    positions.add(
    作り始める位置,
    pos(1, -1, 1)
    ),
    positions.add(
    作り始める位置,
    pos(13, -1, 13)
    ),
    FillOperation.Replace
    )
})
```



## 壁の座標を考えよう
作った土台の上に、壁を並べよう！
壁は、``||variable.変数 作り始める位置||``を基準にして、高さ0～4まで、ガラスブロックで作ろう
まずガラスブロックを並べて、その後空気で中をくりぬこう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_wall.png">



## Step4 ブロックを並べよう
``||variable.変数 作り始める位置||``を基準にして、先ほど考えた通りにブロックを並べよう
まずガラスを並べて、そのあと空気を並べよう
座標は自分で考えてみよう！
※高さは0～4にしよう

```blocks
player.onChat("run", function () {
    blocks.fill(
    SMOOTH_SANDSTONE,
    positions.add(
    作り始める位置,
    pos(1, -1, 1)
    ),
    positions.add(
    作り始める位置,
    pos(13, -1, 13)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    GLASS,
    positions.add(
    作り始める位置,
    pos(1, 0, 1)
    ),
    positions.add(
    作り始める位置,
    pos(13, 4, 13)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    AIR,
    positions.add(
    作り始める位置,
    pos(2, 0, 2)
    ),
    positions.add(
    作り始める位置,
    pos(12, 4, 12)
    ),
    FillOperation.Replace
    )
})
```



## 天井の座標を考えよう
壁の上の天井の座標について考えよう！
壁は、``||variable.変数 作り始める位置||``を基準にして、高さ5の位置に、滑らかな砂岩で作ろう
まず滑らかな砂岩を並べて、そのあと上の階に上がるための穴を空気ブロックを並べて作ろう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_ceiling.png">



## Step5 ブロックを並べよう
``||variable.変数 作り始める位置||``を基準にして、先ほど考えた通りにブロックを並べよう
まず滑らかな砂岩を並べて、そのあと空気を並べよう
座標は自分で考えてみよう！
※高さは5にしよう

```blocks
player.onChat("run", function () {
    blocks.fill(
    SMOOTH_SANDSTONE,
    positions.add(
    作り始める位置,
    pos(1, -1, 1)
    ),
    positions.add(
    作り始める位置,
    pos(13, -1, 13)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    GLASS,
    positions.add(
    作り始める位置,
    pos(1, 0, 1)
    ),
    positions.add(
    作り始める位置,
    pos(13, 4, 13)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    AIR,
    positions.add(
    作り始める位置,
    pos(2, 0, 2)
    ),
    positions.add(
    作り始める位置,
    pos(12, 4, 12)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    SMOOTH_SANDSTONE,
    positions.add(
    作り始める位置,
    pos(1, 5, 1)
    ),
    positions.add(
    作り始める位置,
    pos(13, 5, 13)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    AIR,
    positions.add(
    作り始める位置,
    pos(8, 5, 10)
    ),
    positions.add(
    作り始める位置,
    pos(11, 5, 12)
    ),
    FillOperation.Replace
    )
})
```



## 変数に入った座標を動かそう
次に作り始める位置に、``||variable.変数 作り始める位置||``に入った座標を動かそう！
壁は、``||variable.変数 作り始める位置||``を基準にして、高さ5の位置に、滑らかな砂岩で作ろう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_shift_variable.gif">



## Step6 変数の座標を動かそう
``||variable.変数 作り始める位置||``に入った座標を動かそう
・``||variable.変数 作り始める位置||``に入った座標を、元の位置から6ブロック上に動かす
座標は自分で考えてみよう！
コードの作り方は下の図を参考にしよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_change_variable.png">

```blocks
player.onChat("run", function () {
    blocks.fill(
    SMOOTH_SANDSTONE,
    positions.add(
    作り始める位置,
    pos(1, -1, 1)
    ),
    positions.add(
    作り始める位置,
    pos(13, -1, 13)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    GLASS,
    positions.add(
    作り始める位置,
    pos(1, 0, 1)
    ),
    positions.add(
    作り始める位置,
    pos(13, 4, 13)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    AIR,
    positions.add(
    作り始める位置,
    pos(2, 0, 2)
    ),
    positions.add(
    作り始める位置,
    pos(12, 4, 12)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    SMOOTH_SANDSTONE,
    positions.add(
    作り始める位置,
    pos(1, 5, 1)
    ),
    positions.add(
    作り始める位置,
    pos(13, 5, 13)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    AIR,
    positions.add(
    作り始める位置,
    pos(8, 5, 10)
    ),
    positions.add(
    作り始める位置,
    pos(11, 5, 12)
    ),
    FillOperation.Replace
    )
    作り始める位置 = positions.add(
    作り始める位置,
    pos(0, 6, 0)
    )
})
```



## くりかえそう！
「壁を作る→天井を作る→変数に入った座標を動かす」の部分をループさせて、3階建てにしよう！
3階建てを作るためには、①1階の壁と天井➁2階の壁と天井③3階の壁と天井、の3回くり返せば良さそうです！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_shift_variable.gif">



## Step7 ループさせよう！
「壁を作る→天井を作る→変数に入った座標を動かす」の部分を3回くり返すように、自分で考えてプログラミングしてみよう！
```blocks
player.onChat("run", function () {
    blocks.fill(
    SMOOTH_SANDSTONE,
    positions.add(
    作り始める位置,
    pos(1, -1, 1)
    ),
    positions.add(
    作り始める位置,
    pos(13, -1, 13)
    ),
    FillOperation.Replace
    )
    for (let index = 0; index < 3; index++) {
        blocks.fill(
        GLASS,
        positions.add(
        作り始める位置,
        pos(1, 0, 1)
        ),
        positions.add(
        作り始める位置,
        pos(13, 4, 13)
        ),
        FillOperation.Replace
        )
        blocks.fill(
        AIR,
        positions.add(
        作り始める位置,
        pos(2, 0, 2)
        ),
        positions.add(
        作り始める位置,
        pos(12, 4, 12)
        ),
        FillOperation.Replace
        )
        blocks.fill(
        SMOOTH_SANDSTONE,
        positions.add(
        作り始める位置,
        pos(1, 5, 1)
        ),
        positions.add(
        作り始める位置,
        pos(13, 5, 13)
        ),
        FillOperation.Replace
        )
        blocks.fill(
        AIR,
        positions.add(
        作り始める位置,
        pos(8, 5, 10)
        ),
        positions.add(
        作り始める位置,
        pos(11, 5, 12)
        ),
        FillOperation.Replace
        )
        作り始める位置 = positions.add(
        作り始める位置,
        pos(0, 6, 0)
        )
    }
})
```



## 実行しよう！
プログラミングができあがったら、▶ボタンを押して実行しよう
ゲーム画面にもどったら、テラコッタの上に立ってチャットで「set」と入力しよう
その後、少しはなれてチャットで「run」と入力しよう
もし建てる位置がずれてしまったときは、村長に話しかけよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_complete1.gif">
