# 読解ノート：自分のアプリのコード3箇所

> **氏名：** （自分の名前）
> **AI利用レベル：** 1（質問のみ。説明は自分の言葉で書く）
> **最終更新：** 2026-10-19

生成AIに書いてもらったコードでも、自分で書いたコードでもかまいません。自分のアプリの中から3箇所を選んで、次の3つの問いに答えてください。分からないところは、生成AIに「この行は何をしていますか」「この行を消すとどうなりますか」と聞いてかまいません。ただし、書くのは自分の言葉です。

> 💡 担任の先生の指示で、項目が増えることがあります。

---

## 箇所1：（例：品名を追加するボタンの処理）

```swift
let connectedBubbles =
    connectedBubbles(startingFrom: startBubble)

// 3個未満の場合は消さない
if connectedBubbles.count < 3 {
    comboCount = 0
    return
}

// 連続消去に成功したのでコンボを加算する
comboCount += 1
```

**何をしているか：**
同じ種類のバブルが3個以上つながったら、消します。3個未満の場合は消しません。

**なぜこう書くのか：**
3個未満の場合は、returnで処理を終わらせるためです。
**もしこう書かなかったら：**
returnがないと、3個未満でもバブルが消えてしまう可能性があります。
---

## 箇所2：（見出し）

```swift
let adjacentBubbles = neighborCells(of: candidate)
    .filter { neighbor in
        self.bubble(at: neighbor) != nil
    }

// 接している通常バブルが1個だけの場合
guard adjacentBubbles.count == 1 else {
    continue
}

// 支えになるバブルを確認する
guard adjacentBubbles[0] == supportCell else {
    continue
}
```

**何をしているか：**
クモが出る場所を探しています。周りにバブルが1個だけある場所を選びます。
**なぜこう書くのか：**
クモを落としやすくするためです。
**もしこう書かなかったら：**
クモがいくつものバブルにつながって、落としにくくなります。
---

## 箇所3：（見出し）

```swift
let droppedCount = beforeDropCount - bubbles.count
let droppedSpiderCount = spiderCountBefore - spiderCells.count

droppedBubbleCount += droppedCount

let totalRemovedCount = removedCount + droppedCount

let dropBonus = droppedCount * 50

let gainedScore =
    (removeScore + dropBonus) * difficulty.scoreMultiplier

score += gainedScore
```

**何をしているか：**
消したバブルの数から点数を計算します。落ちたバブルにも点数をつけます。
**なぜこう書くのか：**
消したバブルと落ちたバブルでは、点数が違うからです。
**もしこう書かなかったら：**
落ちたバブルの点数が正しく計算できなくなります。
---

## 自分ではまだ説明できない箇所（正直に）

（アプリの中で「動いているけれど何をしているか分からない」ところを書く。ここに書いたものは、後期の文法の授業で分かるようになります。）
