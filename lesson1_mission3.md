# 相対座標で建築しよう！③

```blocks
player.onChat("c", function () {
    blocks.fill(
    AIR,
    pos(1, 0, 1),
    pos(8, 7, 8),
    FillOperation.Hollow
    )
})
player.onChat("run", function () {
    blocks.fill(
    GOLD_BLOCK,
    pos(1, 0, 1),
    pos(8, 6, 8),
    FillOperation.Hollow
    )
    blocks.fill(
    AIR,
    pos(2, 6, 2),
    pos(7, 6, 7),
    FillOperation.Replace
    )
    blocks.fill(
    GOLD_BLOCK,
    pos(2, 7, 2),
    pos(7, 7, 7),
    FillOperation.Replace
    )
})

```

```template
player.onChat("c", function () {
    blocks.fill(
    AIR,
    pos(1, 0, 1),
    pos(8, 7, 8),
    FillOperation.Hollow
    )
})
player.onChat("run", function () {})
```

## 相対座標で建築しよう！ @unplugged
相対座標を使って建築しよう！
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson1/L1_mission3.png">



## 目標
まずはこれから作るものの形を確認しよう！
・チャットで「run」と入力したら、家の壁と屋根ができるようにプログラミングする
・大きさは、たて8ブロック、横8ブロック、高さ8ブロックにする
・金ブロックで作る
・1番上の屋根の部分は、画像のようにたて6ブロック、横6ブロックにする
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson1/L1_mission3.png">



## 相対座標とは・・・
・相対座標では、自分が立っている場所が(~0, ~0, ~0)
・1番左の数字は、自分が立っている位置を0として、東に進むとふえる
・2番目の数字は、自分が立っている位置を0として、上に進むとふえる
・1番右の数字は、自分が立っている位置を0として、南に進むとふえる
<br></br>
今回は、画像のテラコッタブロックの位置に立って、相対座標で場所を考えて家を建てよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson1/L1_coordinates.png">



## Step1 ブロックを取り出そう
``||blocks.ブロック||``から``||blocks.ブロックを並べる||``を取り出して、``||player.チャットコマンドrunを入力した時||``にはめ込もう
<br></br>



## Step2 座標を考えよう
画像を見て、自分が立つところ(画像のテラコッタブロックのところ)から、色のついた範囲にブロックを並べるには、どうすれば良いか考えよう
自分が立つところが(~0, ~0, ~0)のとき、東と南にそれぞれ何ブロック目から何ブロック目まで色がついているだろう？
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson1/L1_fill_6.gif">
<br></br>
・東：1ブロック目から8ブロック目
・南：1ブロック目から8ブロック目



## Step3 設定を変えよう
さっき考えたことをもとにして、``||blocks.ブロックを並べる||``の設定を変えよう
・ブロックの種類：金ブロック
・範囲の始まり、範囲の終わりについては自力で考えてみよう！
※高さについては、0ブロック目から6ブロック目までになるようにしよう
・モード：中空



## Step4 屋根の作り方
画像を見て、屋根の作り方や、座標を考えてみよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson1/L1_replace_3.gif">
<br></br>
・並べたブロックの一番上に、空気ブロックを並べることで穴を空ける
・その上にたて6ブロック、横6ブロックの大きさでブロックを並べる



## Step5 ブロックを取り出そう
``||blocks.ブロック||``からもうひとつ``||blocks.ブロックを並べる||``を取り出して、``||player.チャットコマンドrunを入力した時||``の一番下にはめ込もう



## Step6 設定を変えよう
さっき並べたブロックの一番上に穴を空けられるように、``||blocks.ブロックを並べる||``の設定を変えよう
・ブロックの種類：空気
・範囲の始まり、範囲の終わりについては、自力で考えてみよう！
・モード：置き換え



## Step7 屋根の部分を作ろう
``||blocks.ブロック||``から3つ目の``||blocks.ブロックを並べる||``を取り出して、``||player.チャットコマンドrunを入力した時||``の一番下にはめ込もう
はめ込んだら、屋根を作るために、``||blocks.ブロックを並べる||``の設定を変えよう
・ブロックの種類：金ブロック
・範囲の始まり、範囲の終わりについては、自力で考えてみよう！
・モード：置き換え



## 実行しよう！
プログラミングができあがったら、▶ボタンを押して実行しよう
ゲーム画面にもどったら、建築を作り始める位置(画像のテラコッタブロックのところ)に移動して、チャットで「run」と入力しよう
もし建てる位置がずれてしまったときは、チャットで「c」と入力するか、お願いされた村人に話しかけよう
建築が完成したら、村人に話しかけよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson1/L1_coordinates.png">



