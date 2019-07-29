---
layout: post
title: "[HackerRank] Compare the Triplets"
date: 2019-07-05 11:09:34 +0900
categories: javascript
background: '/img/rosevine-bg.jpg'
---

# 비교 포인트 값을 구하라.

**トリプレットを比較しましょう**

Q : compareTriplets()の関数を完成してください。

{% highlight rosevine %}
'use strict';

const fs = require('fs');

process.stdin.resume();
process.stdin.setEncoding('utf-8');

let inputString = '';
let currentLine = 0;

process.stdin.on('data', function(inputStdin) {
    inputString += inputStdin;
});

process.stdin.on('end', function() {
    inputString = inputString.split('\n');

    main();7
});

function readLine() {
    return inputString[currentLine++];
}

// Complete the compareTriplets function below.
function compareTriplets(a, b) {


}

function main() {
    const ws = fs.createWriteStream(process.env.OUTPUT_PATH);

    const a = readLine().replace(/\s+$/g, '').split(' ').map(aTemp => parseInt(aTemp, 10));

    const b = readLine().replace(/\s+$/g, '').split(' ').map(bTemp => parseInt(bTemp, 10));

    const result = compareTriplets(a, b);

    ws.write(result.join(' ') + '\n');

    ws.end();
}

{% endhighlight %}


そして、compareTriplets(a, b) で scoreをリターンしましょう！

私はこうしました！

{% highlight rosevine %}
'use strict';

const fs = require('fs');

process.stdin.resume();
process.stdin.setEncoding('utf-8');

let inputString = '';
let currentLine = 0;

process.stdin.on('data', function(inputStdin) {
    inputString += inputStdin;
});

process.stdin.on('end', function() {
    inputString = inputString.split('\n');

    main();
});

function readLine() {
    return inputString[currentLine++];
}

// Complete the compareTriplets function below.
function compareTriplets(a, b) {
    let score = [0, 0]

    for (let i = 0; i < a.length; i++) {
        if (a[i] > b[i]) {
            score[0]++
        } else if (a[i] < b[i]) {
            score[1]++
        }
        // or
        // a[i] > b[i] ? score[0]++ : a[i] < b[i] ? score[1]++ : ''
    console.log('score', score)
    }
    return score

}

function main() {
    const ws = fs.createWriteStream(process.env.OUTPUT_PATH);

    const a = readLine().replace(/\s+$/g, '').split(' ').map(aTemp => parseInt(aTemp, 10));

    const b = readLine().replace(/\s+$/g, '').split(' ').map(bTemp => parseInt(bTemp, 10));

    const result = compareTriplets(a, b);

    ws.write(result.join(' ') + '\n');

    ws.end();
}

{% endhighlight %}

if문은 아래와 같이 `조건(삼항)연산자`로도 표현이 가능합니다.

ifは以下のように`条件(三項)演算子`でも可能です。

{% highlight rosevine %}

function compareTriplets(a, b) {
    let score = [0, 0]

    for (let i = 0; i < a.length; i++) {
        a[i] > b[i] ? score[0]++ : a[i] < b[i] ? score[1]++ : ''
    console.log('score', score)
    }
    return score
}

{% endhighlight %}

以上です。