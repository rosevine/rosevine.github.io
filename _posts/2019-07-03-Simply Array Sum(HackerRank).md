---
layout: post
title: "[HackerRank] Simply Array Sum"
date: 2019-07-03 15:09:34 +0900
categories: javascript
background: '/img/rosevine-bg.jpg'
---

# 배열 요소의 합을 정수로 반환합시다. 

**配列要素の合計を整数として返しましょう。**

Q : simpleArraySum()に答えを書いてください。

{% highlight rosevine %}
Complete the simpleArraySum function below.
function simpleArraySum(ar) {
    
}

function main() {
    const ws = fs.createWriteStream(process.env.OUTPUT_PATH);

    const arCount = parseInt(readLine(), 10);

    const ar = readLine().split(' ').map(arTemp => parseInt(arTemp, 10));
    

    let result = simpleArraySum(ar);
    console.log('result', result)

    ws.write(result + "\n");

    ws.end();
}
{% endhighlight %}


そして、main() 内の`ar`を足して`return`します。
私はこうしました！

{% highlight rosevine %}
Complete the simpleArraySum function below.
function simpleArraySum(ar) {
    let sum = 0;
    for (const i in ar) {
        sum = sum + ar[i]
    }
    console.log('sum', sum)
    ar = sum;
    return ar;
}

function main() {
    const ws = fs.createWriteStream(process.env.OUTPUT_PATH);

    const arCount = parseInt(readLine(), 10);

    const ar = readLine().split(' ').map(arTemp => parseInt(arTemp, 10));
    

    let result = simpleArraySum(ar);
    console.log('result', result)

    ws.write(result + "\n");

    ws.end();
}
{% endhighlight %}

以上です。