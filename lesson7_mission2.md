# 階段を作ろう！

```blocks
player.onChat("set", function () {
    agent.teleport(pos(0, 0, 0), positions.toCompassDirection(player.getOrientation()))
})
player.onChat("run", function (num1) {
    for (let index = 0; index < num1; index++) {
        for (let index = 0; index < 3; index++) {
            agent.setItem(SANDSTONE_STAIRS, 1, 1)
            agent.place(FORWARD)
            agent.move(LEFT, 1)
        }
        agent.move(RIGHT, 3)
        agent.move(UP, 1)
        agent.move(FORWARD, 1)
    }
})
```

```template
player.onChat("set", function () {})
player.onChat("run", function () {})
```

## 階段を作ろう！！ @unplugged
エージェントを動かして階段を作ろう！
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_complete2.gif">



## 目標
まずはこれから作るものの形を確認しよう！
・チャットで「set」と入力すると、エージェントがプレイヤーの位置に、プレイヤーと同じ向きでテレポートする
・チャットで「run 6」と入力すると、エージェントが6段の階段を作るようにする
・階段の横の大きさは3ブロック分にする
・ブロックは砂岩の階段を使う
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_complete2.gif">



## エージェントをプレイヤーのもとにテレポートさせる
まずは、チャットコマンドで「set」と入力すると、エージェントがプレイヤーのところに、プレイヤーと同じ向きでテレポートするようにしよう



## Step1 エージェントをテレポートさせよう
エージェントがプレイヤーの位置に、プレイヤーと同じ向きでテレポートするようにしよう！
・``||agent.エージェント||``から``||agent.エージェントを(~0, ~0, ~0)へ～向きにテレポートさせる||``を取り出してワークスペースの``||player.チャットコマンドsetを入力した時||``にはめ込む
・``||positions.ポジション||``を開いて、``||positions.～の四方位||``を取り出して``||agent.エージェントを(~0, ~0, ~0)へ～向きにテレポートさせる||``にはめ込む
・``||player.プレイヤー||``を開いて、``||player.プレイヤーの向いている方角||``を取り出して、``||positions.～の四方位||``にはめ込む

```blocks
player.onChat("set", function () {
    agent.teleport(pos(0, 0, 0), positions.toCompassDirection(player.getOrientation()))
})
```



## 1段分の動きを考える
エージェントが階段ブロックを1段分並べるには、どんな動きをすれば良いか考えよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_agent_set_block.gif">



## Step2 ブロックを1段分並べる動きを考える
エージェントが砂岩の階段を横に3つ並べる動きを、自分で考えてプログラミングしてみよう！

```blocks
player.onChat("run", function () {
    for (let index = 0; index < 3; index++) {
        agent.setItem(SANDSTONE_STAIRS, 1, 1)
        agent.place(FORWARD)
        agent.move(LEFT, 1)
    }
})
```



## 次の位置に移動する
次にブロックを並べ始める位置に、エージェントを移動させるには、どうすれば良いか考えよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_agent_move.gif">


## Step3 エージェントを動かす
エージェントが、次にブロックを並べる位置へ移動するよう、自分で考えてプログラミングしてみよう！

```blocks
player.onChat("run", function () {
    for (let index = 0; index < 3; index++) {
        agent.setItem(SANDSTONE_STAIRS, 1, 1)
        agent.place(FORWARD)
        agent.move(LEFT, 1)
    }
    agent.move(RIGHT, 3)
    agent.move(UP, 1)
    agent.move(FORWARD, 1)
})
```



## ループさせよう
チャットコマンドで「run 6」と入力すると、6回くり返すように、全体をループさせるにはどうすれば良いでしょうか？
・``||variables.num1||``という変数を作る
・``||variables.num1||``回全体をくり返す
とすれば良さそうです！



## Step4 変数を使ってループする
``||player.チャットコマンドrunを入力した時||``の⊕を押して``||variables.num1||``を作り、全体を``||variables.num1||``回くり返すように自分で考えてプログラミングしてみよう

```blocks
player.onChat("run", function (num1) {
    for (let index = 0; index < num1; index++) {
        for (let index = 0; index < 3; index++) {
            agent.setItem(SANDSTONE_STAIRS, 1, 1)
            agent.place(FORWARD)
            agent.move(LEFT, 1)
        }
        agent.move(RIGHT, 3)
        agent.move(UP, 1)
        agent.move(FORWARD, 1)
    }
})
```



## 実行しよう！
プログラミングができあがったら、▶ボタンを押して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、テラコッタの上に移動して階段を作りたい方を向き、チャットで「set」と入力してエージェントを移動させよう
エージェントが正しい位置と向きになっているのを確認したら、チャットで「run」と入力して、階段を並べさせよう
2階、3階でも同じことをくり返して、屋上にたどり着こう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_complete2_2.gif">
<br></br>



