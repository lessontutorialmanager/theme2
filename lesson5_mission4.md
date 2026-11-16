# プログラムを自由に改造しよう！


```template
player.onChat("run", function (num1) {
    blocks.fill(
    BLOCK_OF_QUARTZ,
    pos(1, 0, 1),
    pos(5, 0, 4),
    FillOperation.Replace
    )
    blocks.fill(
    SAND,
    pos(2, 0, 2),
    pos(4, 0, 3),
    FillOperation.Replace
    )
    blocks.fill(
    GLASS,
    pos(1, 1, 1),
    pos(5, 4, 4),
    FillOperation.Replace
    )
    blocks.fill(
    AIR,
    pos(2, 1, 2),
    pos(4, 4, 3),
    FillOperation.Replace
    )
    blocks.fill(
    BLOCK_OF_QUARTZ,
    pos(1, 5, 1),
    pos(5, 5, 4),
    FillOperation.Replace
    )
    blocks.fill(
    SEA_LANTERN,
    pos(2, 5, 2),
    pos(4, 5, 3),
    FillOperation.Replace
    )
    if (num1 == 0) {
        mobs.spawn(mobs.monster(WITCH), pos(3, 1, 2))
    } else if (num1 == 1) {
        mobs.spawn(mobs.monster(HUSK), pos(3, 1, 2))
    } else {
        mobs.spawn(mobs.monster(ZOMBIE), pos(3, 1, 2))
    }
})
```

# 学んだプログラムを使ってみよう

## プログラムを自由にくみかえよう
・2かいに上がると、さらに囲いがあります！
<img src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson5/L5_cleared.gif" width="100%">
・条件分岐の⊕を押して、4種類以上の生き物を出せるようにしてみよう！

```blocks
player.onChat("run", function (num1) {
    blocks.fill(
    BLOCK_OF_QUARTZ,
    pos(1, 0, 1),
    pos(5, 0, 4),
    FillOperation.Replace
    )
    blocks.fill(
    SAND,
    pos(2, 0, 2),
    pos(4, 0, 3),
    FillOperation.Replace
    )
    blocks.fill(
    GLASS,
    pos(1, 1, 1),
    pos(5, 4, 4),
    FillOperation.Replace
    )
    blocks.fill(
    AIR,
    pos(2, 1, 2),
    pos(4, 4, 3),
    FillOperation.Replace
    )
    blocks.fill(
    BLOCK_OF_QUARTZ,
    pos(1, 5, 1),
    pos(5, 5, 4),
    FillOperation.Replace
    )
    blocks.fill(
    SEA_LANTERN,
    pos(2, 5, 2),
    pos(4, 5, 3),
    FillOperation.Replace
    )
    if (num1 == 0) {
        mobs.spawn(mobs.monster(WITCH), pos(3, 1, 2))
    } else if (num1 == 1) {
        mobs.spawn(mobs.monster(HUSK), pos(3, 1, 2))
    } else if (num1 == 2) {
        mobs.spawn(mobs.monster(ZOMBIE), pos(3, 1, 2))
    } else if (num1 == 3) {
        mobs.spawn(STRIDER, pos(3, 1, 2))
    } else {
        mobs.spawn(ALLAY, pos(3, 1, 2))
    }
})


```

## 自由にコードを使ってみよう
`||完了||`をおすと、すべてのコードが使えるようになります
ほかのコードを組み合わせて、もっとすごいプログラムを作れないか、試してみよう！
