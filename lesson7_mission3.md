# エージェントに柵を並べさせよう！

```blocks
player.onChat("set", function () {
    agent.teleport(pos(0, 0, 0), positions.toCompassDirection(player.getOrientation()))
})
player.onChat("run", function () {
    while (agent.inspect(AgentInspection.Block, FORWARD) != BIRCH_FENCE) {
        if (agent.inspect(AgentInspection.Block, DOWN) == AIR) {
            agent.turn(LEFT_TURN)
            agent.move(FORWARD, 1)
            agent.move(LEFT, 1)
        } else {
            agent.setItem(BIRCH_FENCE, 1, 1)
            agent.move(FORWARD, 1)
            agent.place(BACK)
        }
    }
    agent.setItem(BIRCH_FENCE, 1, 1)
    agent.move(LEFT, 1)
    agent.place(RIGHT)
})
```

```template
player.onChat("set", function () {
	
})
player.onChat("run", function () {
	
})

```

## エージェントに柵を並べさせよう！ @unplugged
条件分岐を使って、エージェントに柵を並べさせよう！
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_complete3.gif">



## 目標
まずはこれから作るものの形を確認しよう！
・チャットで「set」と入力すると、エージェントがプレイヤーの位置に、プレイヤーと同じ向きでテレポートする
・チャットで「run」と入力すると、エージェントが屋上のはしにシラカバの柵を並べる
・1周するまで自動で並べる
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_complete3.gif">



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



## 条件分岐を考えよう①
最初に、全体の条件分岐を考えてみましょう
エージェントが、自分の下にあるブロックを確認して・・・
・空気のとき(下に床がないとき)は、左に曲がる
・空気じゃないとき(下に床があるとき)は、前に進んで後ろにシラカバのフェンスを置く
これをくり返せば、自動でフェンスを並べられそうです！
下の図で条件分岐を確認しよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_flowchart1.png">



## エージェントの下にあるブロックの調べ方
``||agent.エージェント||``にある``||agent.エージェントの前のブロック||``を使えば、エージェントのまわりにあるブロックが何か調べることができます！
これを使って、エージェントの下にあるブロックが空気かどうか、条件分岐を作りましょう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_conditional.png">



## Step2 条件分岐を作ろう
先ほど考えたことをもとに、条件分岐を作ろう！
・``||logic.論理||``から``||logic.もし～ならば でなければ||``を取り出して、``||player.チャットコマンドrunを入力した時||``にはめ込む
・``||logic.論理||``から``||logic.0 = 0||``を取り出して、``||logic.もし～ならば でなければ||``にはめ込む
・``||agent.エージェント||``から``||agent.エージェントの前のブロック||``を取り出して``||logic.0 = 0||``の左にはめ込み、「前」を「下」に変える
・``||blocks.ブロック||``から``||blocks.草ブロック||``を取り出して``||logic.エージェントの下のブロック = 0||``の右にはめ込み、種類を「空気」に変える
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_conditional.png">

```blocks
player.onChat("run", function () {
	if (agent.inspect(AgentInspection.Block, DOWN) == AIR) {

        } else {
            
        }
})
```


## 条件分岐を考えよう➁
条件分岐の中について考えよう！
まずは、エージェントの下のブロックが、空気じゃないとき(でなければ～の方)を先に考えよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_else.png">
<br></br>
・エージェントにシラカバのフェンスをわたす
・前に1ブロック進む
・後ろにフェンスを置く
とすれば良さそうです！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_agent_set_fence.gif">



## Step3 エージェントを動かす
先ほど考えたことをもとに、``||logic.でなければ||``の方の条件分岐を自分で考えてプログラミングしよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_agent_set_fence.gif">

```blocks
player.onChat("run", function () {
	if (agent.inspect(AgentInspection.Block, DOWN) == AIR) {

        } else {
            agent.setItem(BIRCH_FENCE, 1, 1)
            agent.move(FORWARD, 1)
            agent.place(BACK)
        }
})
```


## 条件分岐を考えよう③
次に、エージェントの下のブロックが、空気のときについて考えよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_then.png">
<br></br>
・エージェントを左に向ける
・前に1ブロック進む
・左に1ブロック進む
とすれば良さそうです！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_corner.gif">



## Step4 エージェントを動かす
エージェントの下のブロックが空気のときに、エージェントが次にブロックを並べ始める位置に移動するように、自分で考えてプログラミングしよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_corner.gif">

```blocks
player.onChat("run", function () {
	if (agent.inspect(AgentInspection.Block, DOWN) == AIR) {
            agent.turn(LEFT_TURN)
            agent.move(FORWARD, 1)
            agent.move(LEFT, 1)
        } else {
            agent.setItem(BIRCH_FENCE, 1, 1)
            agent.move(FORWARD, 1)
            agent.place(BACK)
        }
})
```



## ループの終わりを考えよう
エージェントが、自分の下にあるブロックを確認して・・・
・空気のとき(下に床がないとき)は、左に曲がる
・空気じゃないとき(下に床があるとき)は、前に進んで後ろにシラカバのフェンスを置く
という条件分岐を、何回くりかえせば良いでしょうか？エージェントがフェンスを1周並べたときをイメージしてみましょう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_after_setting.png">
<br></br>
上のように、エージェントの前にフェンスがあったら、くり返しを止めれば良さそうです！
「エージェントの前にフェンスが無いあいだずっとくり返す」ということをしたいときは、``||loops.ループ||``にある、``||もし～ならずっと||``を使います！
このコードを使って、全体をくり返そう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_while.png">



## Step5 ループを設定しよう
先ほど考えたことをもとに、ループを設定しよう！
・``||loops.ループ||``から``||loops.もし～ならくりかえし||``を取り出して、作ったプログラムをはさみ込む
・``||logic.論理||``を開いて、``||logic.0 = 0||``を取り出して``||loops.もし～ならくりかえし||``にはめ込み、種類を「≠」(同じでない)に変える
・``||agent.エージェント||``から``||agent.エージェントの前のブロック||``を取り出して``||logic.0 = 0||``の左にはめ込む
・``||blocks.ブロック||``から``||blocks.草ブロック||``を取り出して``||logic.エージェントの下のブロック = 0||``の右にはめ込み、種類を「空気」に変える

```blocks
player.onChat("set", function () {
    agent.teleport(pos(0, 0, 0), positions.toCompassDirection(player.getOrientation()))
})
player.onChat("run", function () {
    while (agent.inspect(AgentInspection.Block, FORWARD) != BIRCH_FENCE) {
        if (agent.inspect(AgentInspection.Block, DOWN) == AIR) {
            agent.turn(LEFT_TURN)
            agent.move(FORWARD, 1)
            agent.move(LEFT, 1)
        } else {
            agent.setItem(BIRCH_FENCE, 1, 1)
            agent.move(FORWARD, 1)
            agent.place(BACK)
        }
    }
})
```



## 最後の1つを置こう
ループを使って、エージェントが1周するまでフェンスを並べ続けるプログラムができました
最後の1か所にフェンスを置くにはどうすれば良いか考えてみよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_last_one.png">
<br></br>
・フェンスを1つわたす
・左に1ブロック進む
・右にフェンスを置く
とすれば良さそうです！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_end.gif">



## Step6 最後のブロックを置かせる
先ほど考えたことをもとに、エージェントが最後の1か所にフェンスを置くように、自分で考えてプログラミングしよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_end.gif">

```blocks
player.onChat("run", function () {
    while (agent.inspect(AgentInspection.Block, FORWARD) != BIRCH_FENCE) {
        if (agent.inspect(AgentInspection.Block, DOWN) == AIR) {
            agent.turn(LEFT_TURN)
            agent.move(FORWARD, 1)
            agent.move(LEFT, 1)
        } else {
            agent.setItem(BIRCH_FENCE, 1, 1)
            agent.move(FORWARD, 1)
            agent.place(BACK)
        }
    }
    agent.setItem(BIRCH_FENCE, 1, 1)
    agent.move(LEFT, 1)
    agent.place(RIGHT)
})
```


## 実行しよう！
プログラミングができあがったら、▶ボタンを押して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、床のはしに移動して作りたい方を向き、チャットで「set」と入力してエージェントを移動させよう
エージェントが左に曲がりながら進めるように、向きに注意しよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_ok.png">
<br></br>
エージェントが正しい位置と向きになっているのを確認したら、チャットで「run」と入力して、フェンスを並べさせよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson7/L7_complete3.gif">
