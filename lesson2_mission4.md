# プログラムを自由に改造しよう！


```template
player.onTravelled(SNEAK, function () {
    if (blocks.testForBlock(BONE_BLOCK, pos(0, -4, 0))) {
        blocks.place(RED_CONCRETE, pos(0, -1, 0))
    } else if (blocks.testForBlock(BONE_BLOCK, pos(0, -5, 0))) {
        blocks.place(ORANGE_CONCRETE, pos(0, -1, 0))
    } else if (blocks.testForBlock(BONE_BLOCK, pos(0, -6, 0))) {
        blocks.place(YELLOW_CONCRETE, pos(0, -1, 0))
    } else {
        blocks.place(WHITE_CONCRETE, pos(0, -1, 0))
    }
})
```

# 学んだプログラムを使ってみよう

## プログラムを自由にくみかえよう
砂漠を緑化しよう！</p>
プレイヤーの足もとがもし砂だったら、草ブロックに置き換えよう！</p>
また、チャットで「s」と入力したらプレイヤーに棒をわたし、棒を使うとジャングルの木が生えるようにしよう</p>
<img src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson2/L2_green.png" width="100%">

```blocks
player.onItemInteracted(STICK, function () {
    blocks.place(JUNGLE_SAPLING, pos(0, 0, 0))
})
player.onTravelled(SNEAK, function () {
    if (blocks.testForBlock(SAND, pos(0, -1, 0))) {
        blocks.fill(
        GRASS,
        pos(-1, -1, -1),
        pos(1, -1, 1),
        FillOperation.Replace
        )
    }
})
player.onChat("s", function () {
    mobs.give(
    mobs.target(LOCAL_PLAYER),
    STICK,
    1
    )
})

```

## 自由にコードを使ってみよう
`||完了||`をおすと、すべてのコードが使えるようになります</p>
ほかのコードを組み合わせて、もっとすごいプログラムを作れないか、試してみよう！</p>
