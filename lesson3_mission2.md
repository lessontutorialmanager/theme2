# 変数で並べよう！➁

```blocks
player.onChat("set", function () {
    agent.teleport(pos(0, 0, 0), positions.toCompassDirection(player.getOrientation()))
})
player.onChat("run", function () {
    for (let index = 0; index < 3; index++) {
        for (let index = 0; index < 4; index++) {
            for (let index = 0; index < 3; index++) {
                agent.setItem(BOOKSHELF, 1, 1)
                agent.place(FORWARD)
                agent.move(LEFT, 1)
            }
            agent.move(UP, 1)
            agent.move(RIGHT, 3)
        }
        agent.move(FORWARD, 3)
        agent.move(DOWN, 4)
    }
})


```

```template
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

## 本棚を並べよう！ @unplugged
くりかえしを使って、本棚を3セット並べよう！
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_complete2.gif">



## 目標
先ほど作ったプログラムを改造して、エージェントが本棚のかたまりを3つ並べるようにしよう！
・チャットコマンドで「set」と入力すると、エージェントがプレイヤーのところに、プレイヤーと同じ向きでテレポートする
・チャットコマンドで「run」と入力すると、エージェントが横3ブロック、たて4ブロック分の本棚を、3セット並べる
<br></br>
<img height="100%" width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_complete2.gif">



## これから作るものの確認
先ほどのプログラムでは、本棚を横3ブロック、たて4ブロック分並べるようにしました
今度は、「本棚を横3ブロック、たて4ブロック分並べる(先ほどのプログラム)」→「次の位置に移動する」を3回くりかえすようにしよう！
下の図で全体の流れを確認しよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_flowchart3.png">



## 次の位置に移動する
本棚を横3ブロック、たて4ブロック分並べたあと、エージェントは次のような位置にいます
<br></br>
1.全体
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_agent_after_moving.png">
<br></br>
2.上から見た図
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_from_above.png">
3.横から見た図
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_from_side.png">
<br></br>
次に本棚を並べ始める位置に移動するには、エージェントをどのように動かせば良いか考えよう！



## Step1 エージェントを移動させる
エージェントが、次に本棚を並べ始める位置に移動するように、自分で考えてプログラミングしよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_agent_next_position.gif">
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
    agent.move(FORWARD, 3)
    agent.move(DOWN, 4)
})
```



## Step2 全体をくりかえす
作成した、「本棚を横3ブロック、たて4ブロック分並べる(先ほどのプログラム)」→「次の位置に移動する」を3回くりかえすようにしよう！
・``||loops.ループ||``を開いて、``||loops.くりかえし4回||``を取り出して、``||player.チャットコマンドrunを入力した時||``の中にはさみ込む
・``||loops.くりかえし4回||``のくり返す回数を3にする

```blocks
player.onChat("run", function () {
    for (let index = 0; index < 3; index++) {
        for (let index = 0; index < 4; index++) {
            for (let index = 0; index < 3; index++) {
                agent.setItem(BOOKSHELF, 1, 1)
                agent.place(FORWARD)
                agent.move(LEFT, 1)
            }
            agent.move(UP, 1)
            agent.move(RIGHT, 3)
        }
        agent.move(FORWARD, 3)
        agent.move(DOWN, 4)
    }
})
```



## 実行しよう！
プログラミングができあがったら、▶ボタンを押して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、テラコッタの上に移動して本棚を作りたい方を向き、チャットで「set」と入力してエージェントを移動させよう
エージェントが正しい位置と向きになっているのを確認したら、チャットで「run」と入力して、本棚を並べさせよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_complete2.gif">
<br></br>
本棚ができあがったのを確認したら、研究者に話しかけよう
