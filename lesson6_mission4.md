# プログラムを自由に改造しよう！

```blocks
let 作り始める位置: Position = null
player.onChat("set", function () {
    作り始める位置 = player.position()
})
player.onChat("run", function () {
    for (let index = 0; index < 2; index++) {
        blocks.fill(
        BRICKS,
        positions.add(
        作り始める位置,
        pos(1, 0, 1)
        ),
        positions.add(
        作り始める位置,
        pos(8, 7, 8)
        ),
        FillOperation.Hollow
        )
        作り始める位置 = positions.add(
        作り始める位置,
        pos(7, 0, -5)
        )
    }
})


```

```template
let 作り始める位置: Position = null
player.onChat("set", function () {
    作り始める位置 = player.position()
})
player.onChat("run", function () {
    for (let index = 0; index < 2; index++) {
        blocks.fill(
        BRICKS,
        positions.add(
        作り始める位置,
        pos(1, 0, 1)
        ),
        positions.add(
        作り始める位置,
        pos(8, 7, 8)
        ),
        FillOperation.Hollow
        )
        作り始める位置 = positions.add(
        作り始める位置,
        pos(7, 0, -5)
        )
    }
})
```
# 学んだプログラムを使ってみよう

## プログラムを自由にくみかえよう①
``||variables.変数 作り始める位置||``に入った座標を動かす位置を調整すると、2階建てを一瞬で作ることができます！
数字を変えて実験してみよう！
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson6/L6_example1.gif">

```blocks
let 作り始める位置: Position = null
player.onChat("set", function () {
    作り始める位置 = player.position()
})
player.onChat("run", function () {
    for (let index = 0; index < 2; index++) {
        blocks.fill(
        BRICKS,
        positions.add(
        作り始める位置,
        pos(1, 0, 1)
        ),
        positions.add(
        作り始める位置,
        pos(8, 7, 8)
        ),
        FillOperation.Hollow
        )
        作り始める位置 = positions.add(
        作り始める位置,
        pos(0, 7, 0)
        )
    }
})
```



## プログラムを自由にくみかえよう①
さらに、``||loops.くりかえし||``の数を変えれば、ブロックを並べる⇒座標を動かす⇒ブロックを並べる・・・と何度もくり返してくれます
ビルのような大きな建物を作ってみよう！
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson6/L6_example2.gif">

```blocks
let 作り始める位置: Position = null
player.onChat("set", function () {
    作り始める位置 = player.position()
})
player.onChat("run", function () {
    for (let index = 0; index < 6; index++) {
        blocks.fill(
        BRICKS,
        positions.add(
        作り始める位置,
        pos(1, 0, 1)
        ),
        positions.add(
        作り始める位置,
        pos(8, 7, 8)
        ),
        FillOperation.Hollow
        )
        作り始める位置 = positions.add(
        作り始める位置,
        pos(0, 7, 0)
        )
    }
})
```


## 自由にコードを使ってみよう
`||完了||`をおすと、すべてのコードが使えるようになります
ほかのコードを組み合わせて、もっとすごいプログラムを作れないか、試してみよう！
