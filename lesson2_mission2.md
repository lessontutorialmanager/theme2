# 変数を使って建築しよう！➁

```blocks
player.onTravelled(SNEAK, function () {
    if (blocks.testForBlock(BONE_BLOCK, pos(0, -7, 0))) {
        blocks.place(RED_CONCRETE, pos(0, -1, 0))
    } else if (blocks.testForBlock(BONE_BLOCK, pos(0, -8, 0))) {
        blocks.place(RED_CONCRETE, pos(0, -1, 0))
    } else if (blocks.testForBlock(BONE_BLOCK, pos(0, -9, 0))) {
        blocks.place(RED_CONCRETE, pos(0, -1, 0))
    } else {
        blocks.place(WHITE_CONCRETE, pos(0, -1, 0))
    }
})

```

```template
player.onTravelled(WALK, function () {})
```

## 地中の化石を検知しよう！ @unplugged
条件分岐を使って、地中に化石のある場所を見つけよう！
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson2/L2_complete1.gif">



## 目標
まずはこれからやることを確認しよう！
・スニーク(しゃがみ)しながら歩いたら、プレイヤーの足もとにコンクリートを置く
・プレイヤーの7～9ブロック下に骨ブロックがあるときは、赤色のコンクリートを置く
・プレイヤーの7～9ブロック下に骨ブロックがないときは、白色のコンクリートを置く
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson2/L2_complete1.gif">



## Step1 プレイヤーがスニークした時
ワークスペースの``||player.プレイヤーが歩いた時||``を``||player.プレイヤーがスニークした時||``に変えよう

```blocks
player.onTravelled(SNEAK, function () {})
```



## 条件分岐を考えよう！
条件分岐を考えてみよう！
・プレイヤーの7ブロック下に骨があれば、プレイヤーの１ブロック下に赤色のコンクリートを置く
・なかった場合、プレイヤーの8ブロック下に骨があれば、プレイヤーの１ブロック下に赤色のコンクリートを置く
・なかった場合、プレイヤーの9ブロック下に骨があれば、プレイヤーの１ブロック下に赤色のコンクリートを置く
・なかった場合、プレイヤーの１ブロック下に白色のコンクリートを置く



## Step2 条件分岐を作ろう
``||logic.論理||``を開いて、``||logic.もし～なら でなければ||``を取り出してはめ込もう
``||logic.もし～なら でなければ||``の⊕マークを2回押そう
<br></br>

```blocks
player.onTravelled(SNEAK, function () {
    if (true) {
    	
    } else if (false) {
    	
    } else if (false) {
    	
    } else {
    	
    }
})
```



## Step3 ブロックを調べよう
先ほどの考えをもとにして、3～5ブロック下に骨があるか調べられるようにしよう
・``||blocks.ブロック||``を開いて、``||blocks.～が(~0, ~0, ~0)に存在する||``を取り出し、``||logic.もし～なら でなければ||``に3つはめこむ
・3つの``||blocks.～が(~0, ~0, ~0)に存在する||``の、ブロックの種類を骨に変更する
・3つの``||blocks.～が(~0, ~0, ~0)に存在する||``の座標を、上から「7ブロック下」「8ブロック下」「9ブロック下」になるように、自分で考えて設定する
<br></br>
・分からないときは、💡を押してヒントを見てみよう

```blocks
player.onTravelled(SNEAK, function () {
    if (blocks.testForBlock(BONE_BLOCK, pos(0, -7, 0))) {
    } else if (blocks.testForBlock(BONE_BLOCK, pos(0, -8, 0))) {
    } else if (blocks.testForBlock(BONE_BLOCK, pos(0, -9, 0))) {
    } else {
    }
})

```



## Step4 コンクリートを置こう
3～5ブロック下に骨があったときは赤色、なかったときは白色のコンクリートを置くようにしよう
・``||blocks.ブロック||``を開いて、``||blocks.～を(~0, ~0, ~0)に置く||``を取り出し、``||logic.もし～なら でなければ||``に4つはめこむ
・4つの``||blocks.～を(~0, ~0, ~0)に置く||``のうち、上3つは赤色のコンクリート、一番下の1つは白色のコンクリートに設定する
・4つの``||blocks.～を(~0, ~0, ~0)に置く||``の座標を、「プレイヤーの1ブロック下」になるように、自分で考えて設定する
<br></br>
・分からないときは、💡を押してヒントを見てみよう

```blocks
player.onTravelled(SNEAK, function () {
    if (blocks.testForBlock(BONE_BLOCK, pos(0, -7, 0))) {
        blocks.place(RED_CONCRETE, pos(0, -1, 0))
    } else if (blocks.testForBlock(BONE_BLOCK, pos(0, -8, 0))) {
        blocks.place(RED_CONCRETE, pos(0, -1, 0))
    } else if (blocks.testForBlock(BONE_BLOCK, pos(0, -9, 0))) {
        blocks.place(RED_CONCRETE, pos(0, -1, 0))
    } else {
        blocks.place(WHITE_CONCRETE, pos(0, -1, 0))
    }
})
```



## 実行しよう！
プログラミングができあがったら、▶ボタンを押して実行しよう
ゲーム画面にもどったら、スニークしながら歩いて、地中に骨があるところを探そう！
探し終わったら、研究者に話しかけよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson2/L2_complete1.gif">
・できているかどうかわからないときは、💡を押してヒントを見てみよう
![mission1_goal](https://vcode-esia.com/images_for_world_data/school/2nd/Lesson2/L2_goal2.png)

