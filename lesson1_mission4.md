# 相対座標で建築しよう！③

```blocks
player.onChat("c", function () {
    blocks.fill(
    AIR,
    pos(1, 0, 1),
    pos(8, 7, 8),
    FillOperation.Hollow
    )
})
player.onChat("run", function () {
    blocks.fill(
    GOLD_BLOCK,
    pos(1, 0, 1),
    pos(8, 6, 8),
    FillOperation.Hollow
    )
    blocks.fill(
    AIR,
    pos(2, 6, 2),
    pos(7, 6, 7),
    FillOperation.Replace
    )
    blocks.fill(
    GOLD_BLOCK,
    pos(2, 7, 2),
    pos(7, 7, 7),
    FillOperation.Replace
    )
})

```

```template
player.onChat("c", function () {
    blocks.fill(
    AIR,
    pos(1, 0, 1),
    pos(8, 7, 8),
    FillOperation.Hollow
    )
})
player.onChat("run", function () {
    blocks.fill(
    GOLD_BLOCK,
    pos(1, 0, 1),
    pos(8, 6, 8),
    FillOperation.Hollow
    )
    blocks.fill(
    AIR,
    pos(2, 6, 2),
    pos(7, 6, 7),
    FillOperation.Replace
    )
    blocks.fill(
    GOLD_BLOCK,
    pos(2, 7, 2),
    pos(7, 7, 7),
    FillOperation.Replace
    )
})
```

# 学んだプログラムを使ってみよう

## プログラムを自由にくみかえよう
扉と窓も自分でつけてみよう！
屋根と壁だけでなく、扉と窓もプログラミングでつけてみよう！
・``||blocks.ブロックを(~0, ~0, ~0)に置く||``を使ってオークのドアを置く
・``||blocks.ブロックを並べる||``を使って窓の位置にガラスを並べる
・壁と屋根のブロックの素材を好きなものにする
さらに挑戦したい人は、ベッドをプログラミングで好きな位置に置いてみよう！

```blocks
player.onChat("run", function () {
    blocks.fill(
    DIAMOND_BLOCK,
    pos(1, 0, 1),
    pos(8, 6, 8),
    FillOperation.Hollow
    )
    blocks.fill(
    AIR,
    pos(2, 6, 2),
    pos(7, 6, 7),
    FillOperation.Replace
    )
    blocks.fill(
    DIAMOND_BLOCK,
    pos(2, 7, 2),
    pos(7, 7, 7),
    FillOperation.Replace
    )
    blocks.place(OAK_DOOR, pos(2, 1, 1))
    blocks.fill(
    GLASS,
    pos(3, 2, 8),
    pos(6, 3, 8),
    FillOperation.Replace
    )
    blocks.place(BED, pos(3, 1, 3))
})

```

## 自由にコードを使ってみよう
`||完了||`をおすと、すべてのコードが使えるようになります
ほかのコードを組み合わせて、もっとすごいプログラムを作れないか、試してみよう！
