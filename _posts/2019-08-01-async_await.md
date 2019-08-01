---
layout: post
title: "async / await"
date: 2019-07-30 15:19:34 +0900
categories: javascript
background: '/img/rosevine-bg.jpg'
---

# async? await?

이 두가지를 이용해서 비동기 자바스크립트를 동기식으로 만들 수 있다.

`async`,  `await`는 비교적 최근에 정의된 문법이다.
이 문법들을 사용하면 비교적 쉽게 비동기 코드를 작성 할 수 있다.


# async

`async`,  `await`의 사용방법은 간단하다. 함수의 선언앞에 붙여주면 된다.
function 앞에 `async`를 붙여주고, 비동기로 처리되는 부분 앞에 `await`를 붙여주면? 끄읕!

다만, `async`,  `await` 모두 반드시 **`promise`를 반환한다는 것!**

즉, 호출해서 결과값을 얻기 위해서는 반드시 `함수().then(result=>{ ... }) ` 를 사용하게 된다.

**before**
{% highlight rosevine %}
function fn() {
  return 42;
}

let result = fn();
console.log(result);
{% endhighlight %}

**after**
{% highlight rosevine %}
async function fn() {
  return 42;
}

fn().then(result => {
  console.log(result);
});
{% endhighlight %}


async 함수에서 Promise 이외의 값을 반환하는 경우는, 그 값에서 resolve되는 Promise가 리턴하게 된다.

물론, async 함수에서 지금까지의 방법으로 Promise 를 반환하는 것 또한 가능하다.


{% highlight rosevine %}
async function fn() {
  return new Promise((resolve, reject) => {
    resolve(42);
  });
}

fn().then(result => {
  console.log(result);
});
{% endhighlight %}


# await

async를 붙인 함수안에는 await Promise가 Promise.then(result=>{ ... }) 를 간략화해서 사용한다.


**before**
{% highlight rosevine %}
    async function fn() {
        return 42;
    }

    async function exec() {
        fn().then(result => {
            console.log(result);
        });
    }

    exec();
{% endhighlight %}

**after**
{% highlight rosevine %}
    async function fn() {
        return 42;
    }

    async function exec() {
        let result = await fn();
        console.log(result);
    }

    exec();
{% endhighlight %}