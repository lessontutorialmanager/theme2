# 変数で並べよう！③

```blocks
player.onChat("run", function (num1) {
    for (let index = 0; index < num1; index++) {
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
player.onChat("set", function () {
    agent.teleport(pos(0, 0, 0), positions.toCompassDirection(player.getOrientation()))
})


```

```template
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

## 本棚を並べよう！ @unplugged
変数を使って、好きな回数だけくりかえせるようにしよう！
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_complete3.gif">



## 目標
先ほど作ったプログラムを改造して、エージェントが本棚のかたまりを、チャットコマンドで設定した数だけ並べるようにしよう！
・チャットコマンドで「set」と入力すると、エージェントがプレイヤーのところに、プレイヤーと同じ向きでテレポートする
・チャットコマンドで「run ○」と入力すると、エージェントが横3ブロック、たて4ブロック分の本棚を、○の分だけ並べる
<br></br>
<img height="100%" width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_complete3.gif">
<br></br>
<img height="100%" width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_chatcommand.png">



## これから作るものの確認
先ほどのプログラムでは、「本棚を横3ブロック、たて4ブロック分並べる(先ほどのプログラム)」→「次の位置に移動する」を3回くりかえすようにしました
今度は、場所によって何回くりかえすかが変わります
下の図の、どの部分の数字を変えれば良いか考えてみよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_flowchart3.png">



## 変数を使おう
横3ブロック、たて4ブロック分の本棚を、4回や2回並べたいときは、次のようになります
<br></br>
1.4回並べたいとき
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_variable1.png">
<br></br>
2.2回並べたいとき
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_variable2.png">
<br></br>
3.次のように、○回の部分の数字を変えられるようになれば、毎回プログラムの数字を入れなおさなくても良くなって、プログラムがもっと便利になります！
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_variable3.png">
<br></br>
変数を使って、毎回ちがう数字を入れられるように設定してみよう！



## Step1 変数を作成する
チャットで``||player.run ○||``と入力できるように変数を作成しよう
・``||player.チャットコマンドrunを入力した時||``の右はしにある、⊕を1回押す
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_set_variable.gif">
<br></br>
これで、``||variables.num1||``という名前の変数ができました！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_variable4.png">

```blocks
player.onChat("run", function (num1) {
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



## Step2 変数を入れる
作成した``||variables.num1||``を、くりかえしにはめこもう！
・``||variables.変数||``を開いて、``||variables.num1||``を取り出して、``||loops.くりかえし3回||``にはめこむ
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_variable5.gif">

```blocks
player.onChat("run", function (num1) {
    for (let index = 0; index < num1; index++) {
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



## 変数のルール
変数には、同じ名前の変数には同じものが一気に入る、というルールがあります
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_variable6.png">
<br></br>
たとえば、チャットで「run 4」と入力して、今回作成した``||variables.num1||``に4という数字を入れると、``||variables.num1||``と書かれたところ全てに4が一度に入ります
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_variable7.png">
<br></br>
また、「run 2」と入力すれば、``||variables.num1||``と書かれたところ全てに2が入ります
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_variable8.png">
<br></br>
この変数のルールを使えば、毎回プログラムを修正しなくても、「run ○」と入力するだけでちがう数の本棚を並べることができます！



## 実行しよう！
▶ボタンを押して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、手前にあるテラコッタの上に移動して本棚を作りたい方を向き、チャットで「set」と入力してエージェントを移動させよう
エージェントが正しい位置と向きになっているのを確認したら、チャットで「run 4」と入力して、本棚を4セット並べさせよう
次に、奥のテラコッタに移動し、「set」と入力してエージェントを移動させたら、「run 2」と入力して、本棚を2セット並べさせよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_complete3.gif">
<br></br>
本棚ができあがったのを確認したら、研究者に話しかけよう
