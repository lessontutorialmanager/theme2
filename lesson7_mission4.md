# プログラムを自由に改造しよう！


```template
let 作り始める位置: Position = null
player.onChat("set1", function () {
    作り始める位置 = player.position()
})
player.onChat("run1", function () {
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
player.onChat("set2", function () {
    agent.teleport(pos(0, 0, 0), positions.toCompassDirection(player.getOrientation()))
})
player.onChat("run2", function (num1) {
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
player.onChat("set3", function () {
    agent.teleport(pos(0, 0, 0), positions.toCompassDirection(player.getOrientation()))
})
player.onChat("run3", function () {
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

# 学んだプログラムを使ってみよう

## プログラムを自由にくみかえよう
くりかえしの数やブロックの種類、高さを変えて、大きなビルを作ろう！

```blocks
let 作り始める位置: Position = null
player.onChat("set1", function () {
    作り始める位置 = player.position()
})
player.onChat("run1", function () {
    blocks.fill(
    WHITE_CONCRETE_POWDER,
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
    for (let index = 0; index < 6; index++) {
        blocks.fill(
        WHITE_CONCRETE,
        positions.add(
        作り始める位置,
        pos(1, 0, 1)
        ),
        positions.add(
        作り始める位置,
        pos(13, 6, 13)
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
        pos(12, 6, 12)
        ),
        FillOperation.Replace
        )
        blocks.fill(
        LIGHT_GRAY_CONCRETE,
        positions.add(
        作り始める位置,
        pos(1, 7, 1)
        ),
        positions.add(
        作り始める位置,
        pos(13, 7, 13)
        ),
        FillOperation.Replace
        )
        blocks.fill(
        AIR,
        positions.add(
        作り始める位置,
        pos(8, 7, 10)
        ),
        positions.add(
        作り始める位置,
        pos(11, 7, 12)
        ),
        FillOperation.Replace
        )
        作り始める位置 = positions.add(
        作り始める位置,
        pos(0, 8, 0)
        )
    }
})



```


## 自由にコードを使ってみよう
`||完了||`をおすと、すべてのコードが使えるようになります
ほかのコードを組み合わせて、もっとすごいプログラムを作れないか、試してみよう！
