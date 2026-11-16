# 学んだプログラムを使ってみよう


```template
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



## プログラムを自由にくみかえよう①
・``||player.チャットコマンドrunを入力した時||``の右はしにある、⊕を1回押して、``||variables.num2||``という変数を作る
・``||variables.num2||``を``||loops.くりかえし3回||``にはめ込む
・``||math.0 × 0||``を取り出して、``||agent.エージェントを右に3ブロック移動させる||``にはめ込む
・``||variables.num2||``を取り出して``||math.0 × 0||``にはめ込み、``||math.num2 × 2||``となるようにする
・エージェントに渡すブロックの種類をサボテンにし、ブロックを置いた後に、左に2ブロック移動するように変更する
こうすると、たとえばチャットで「run 2 3」と入力すると、エージェントがたて4ブロックの大きさのサボテンを、1ブロックおきに3つ(``||variables.num2||``)並べる動きを2セット(``||variables.num1||``)作るようになります！
「run ○ ○」の数字をいろいろ変えて試してみよう！
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_cleared_1.gif">
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson3/L3_cleared_2.gif">


```blocks
player.onChat("run", function (num1, num2) {
    for (let index = 0; index < num1; index++) {
        for (let index = 0; index < 4; index++) {
            for (let index = 0; index < num2; index++) {
                agent.setItem(BOOKSHELF, 1, 1)
                agent.place(FORWARD)
                agent.move(LEFT, 2)
            }
            agent.move(UP, 1)
            agent.move(RIGHT, num2 * 2)
        }
        agent.move(FORWARD, 3)
        agent.move(DOWN, 4)
    }
})

```


## プログラムを自由にくみかえよう➁
``||mobs.次の対象に～を～つ渡す||``と変数を組み合わせると、好きな数だけブロックやアイテムを取り出すことができます！
・``||player.チャットコマンドjumpを入力した時||``を取り出して、右はしの⊕を押し、``||variables.num1||``を作る
・``||mobs.次の対象に～を～つ渡す||``の数の部分に``||variables.num1||``をはめ込む
・対象を「自分」に変えて、好きなブロックやアイテムを設定する
これで「jump ○」と入力すると、設定したブロックやアイテムが、入力した数だけ手に入ります！

```blocks
player.onChat("run", function (num1) {
    mobs.give(
    mobs.target(LOCAL_PLAYER),
    GRASS,
    num1
    )
})
```

## 自由にコードを使ってみよう
`||完了||`をおすと、すべてのコードが使えるようになります
ほかのコードを組み合わせて、もっとすごいプログラムを作れないか、試してみよう！
