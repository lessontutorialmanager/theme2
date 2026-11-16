# 変数で並べよう！①

```blocks
player.onChat("set", function () {
    agent.teleport(pos(0, 0, 0), positions.toCompassDirection(player.getOrientation()))
})
player.onChat("run", function () {
    for (let index = 0; index < 4; index++) {
        for (let index = 0; index < 3; index++) {
            agent.setItem(BOOKSHELF, 1, 1)
            agent.place(FORWARD)
            agent.move(LEFT, 1)
        }
        agent.move(UP, 1)
        agent.move(RIGHT, 3)
    }
})


```

```template
player.onChat("set", function () {})
player.onChat("run", function () {})
```

## 本棚を並べよう！ @unplugged
くりかえしを使って、本棚を並べよう！
<n></n>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_complete1_1.gif"><img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_complete1_2.gif">



## 目標
エージェントを使って、本棚を並べよう！
・チャットコマンドで「set」と入力すると、エージェントがプレイヤーのところに、プレイヤーと同じ向きでテレポートする
・チャットコマンドで「run」と入力すると、エージェントが横3ブロック、たて4ブロック分本棚を並べる
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_complete1_1.gif">
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_complete1_2.gif">



## エージェントをプレイヤーのもとにテレポートさせる
まずは、チャットコマンドで「set」と入力すると、エージェントがプレイヤーのところに、プレイヤーと同じ向きでテレポートするようにしよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_complete1_1.gif">



## Step1 エージェントをテレポートさせよう
``||agent.エージェント||``から``||agent.エージェントを(~0, ~0, ~0)へ～向きにテレポートさせる||``を取り出してワークスペースの``||player.チャットコマンドsetを入力した時||``にはめ込もう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_agent_teleport.gif">

```blocks
player.onChat("set", function () {
    agent.teleport(pos(0, 0, 0), WEST)
})
```



## エージェントの向きについて
エージェントがテレポートしたとき、プレイヤーが向いている方向を向くようにしよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_tp.gif">
<br></br>
``||agent.エージェントを(~0, ~0, ~0)へ～向きにテレポートさせる||``の向きの部分に、下のコードを組み合わせると、エージェントがプレイヤーのもとにテレポートしたとき、プレイヤーと同じ方向を向くようになります
こうしておくと、毎回エージェントの向きを変えなくてすむので便利です！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_direction.png">



## Step2 エージェントがプレイヤーと同じ向きになるようにしよう
・``||positions.ポジション||``を開いて、``||positions.～の四方位||``を取り出して``||agent.エージェントを(~0, ~0, ~0)へ～向きにテレポートさせる||``にはめ込む
・``||player.プレイヤー||``を開いて、``||player.プレイヤーの向いている方角||``を取り出して、``||positions.～の四方位||``にはめ込む
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_compass_direction.gif">

```blocks
player.onChat("set", function () {
    agent.teleport(pos(0, 0, 0), positions.toCompassDirection(player.getOrientation()))
})
```



## 本棚を並べよう
エージェントが立っているところから、本棚を横に3つ、たてに4つ並べるようにしよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_count.png">
<br></br>
はじめに、全体の流れを、下の図で考えてみよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_flowchart1.png">
<br></br>
まずは、本棚を横に3つ並べて、次の並べはじめの位置に移動するようプログラムしよう



## 本棚を1列並べる
本棚を1列並べられるようにプログラミングしよう
1.エージェントに本棚を1つ渡す
2.エージェントに前に本棚を置かせる
3.エージェントを左に1ブロック移動させる
の3つの動きを、3回くり返せば横に3つ並べることができます！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_set_block.gif">



## Step3 本棚を3つ並べよう
くりかえしを使って、エージェントが本棚を3つ横に並べられるように、自分で考えてプログラミングしよう！
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_loop_next_column.gif">
・分からないときは、💡を押してヒントを見てみよう

```blocks
player.onChat("run", function () {
    for (let index = 0; index < 3; index++) {
        agent.setItem(BOOKSHELF, 1, 1)
        agent.place(FORWARD)
        agent.move(LEFT, 1)
    }
})
```



## 次の場所に移動する
本棚を1列並べたら、次に本棚を並べ始める位置にエージェントを移動させよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_loop_next_row.gif">



## Step4 エージェントを移動させよう
エージェントが、次に本棚を並べ始める位置に移動するように、自分で考えてプログラミングしよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_loop_next_row.gif">
<br></br>
・分からないときは、💡を押してヒントを見てみよう

```blocks
player.onChat("run", function () {
    for (let index = 0; index < 3; index++) {
        agent.setItem(BOOKSHELF, 1, 1)
        agent.place(FORWARD)
        agent.move(LEFT, 1)
    }
    agent.move(UP, 1)
    agent.move(RIGHT, 3)
})
```



## 本棚の高さの分だけくりかえす
これで、「本棚を3つ並べる」→「次の並べはじめの位置に移動する」というプログラムができました！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_flowchart2.png">
<br></br>
これまでに作ったプログラムを4回くりかえして、本棚がたて4ブロック分になるようにしましょう！
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_complete1_2.gif">



## Step5 くりかえしを設定しよう
「本棚を3つ並べる」→「次の並べはじめの位置に移動する」というプログラムを、4回くりかえすように、自分で考えてプログラミングしよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_complete1_2.gif">
<br></br>
・分からないときは、💡を押してヒントを見てみよう

```blocks
player.onChat("run", function () {
    for (let index = 0; index < 4; index++) {
        for (let index = 0; index < 3; index++) {
            agent.setItem(BOOKSHELF, 1, 1)
            agent.place(FORWARD)
            agent.move(LEFT, 1)
        }
        agent.move(UP, 1)
        agent.move(RIGHT, 3)
    }
})
```



## 実行しよう！
プログラミングができあがったら、▶ボタンを押して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、テラコッタの上に移動して本棚を作りたい方を向き、チャットで「set」と入力してエージェントを移動させよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_complete1_1.gif">
<br></br>
エージェントが正しい位置と向きになっているのを確認したら、チャットで「run」と入力して、本棚を並べさせよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_complete1_2.gif">
<br></br>
本棚ができあがったのを確認したら、研究者に話しかけよう

