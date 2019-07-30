---
layout: post
title: "제너레이터(Generator)"
date: 2019-07-30 14:19:34 +0900
categories: javascript
background: '/img/rosevine-bg.jpg'
---

# 제너레이터(Generator) 란?

`JavaScript ES6` 부터 사용 가능한 기능이다.
일반적으로 함수는 처음부터 같은 흐름으로 처리를 하지만,
제너레이터는 실행중 값을 리턴할 수 있고, 다시 그 위치에서부터 실행이 가능하다는 장점을 지녔다.

제너레이터는 `비동기코드`를 `동기식코드`를 작성하는 것과 같이 작성이 가능하다.
많은 데이터를 순차적으로 처리할 때 도움이 된다.
비동기코드 작성시, 제너레이터를 사용한다면 편리함을 느낄수있을 것이다.


# 제너레이터(Generator) 특징 


1. new 없이 제너레이터 객체 생성이 가능하다.
2. 제너레이터는 function 뒤에 '*' 키워드를 붙여 사용한다.
3. yield 옆에 있는 값을 return 한다.
4. 제너레이터 함수를 실행하면 next() 메소드 사용이 가능하다.


{% highlight rosevine %}
    function* generator_function() {
        yield 1;
        yield 2;
        yield 3;
        yield 4;
        yield 5;
    }

    let generator = generator_function();

    console.log(generator.next().value); // 1
    console.log(generator.next().value); // 2
    console.log(generator.next().value); // 3
    console.log(generator.next().value); // 4
    console.log(generator.next().value); // 5
    console.log(generator.next().done); // true
{% endhighlight %}

위 코드를 실행하면 결과 값은 

{% highlight rosevine %}
1
2
3
4
5
true
{% endhighlight %}

이렇게 나온다.

한가지 더 예시를 보자.

{% highlight rosevine %}
    function* gen() {
        var abc = yield 'apple';
        console.log(abc); // abc
    }

    var g = gen();

    console.log(g.next()); // {value: 'apple', done: false}
    console.log(g.next('abc'));
{% endhighlight %}

실행결과는,

{% highlight rosevine %}
{value: "apple", done: false}
abc
{value: undefined, done: true}
{% endhighlight %}

next() 메소드는 매개변수를 쓸 수있는데, 이렇게 되면 기능이 조금 달라진다.
보통은 `yield 가 next()에게 값을 return 해주는데 반해, `
`next()안에 매개변수가 담겨있다면, next()가 yield에게 값을 전달해주게된다.`

즉, 매개변수 'abc'를 yield 에게 넘겨줬기 때문에, return 값은 'apple' 아닌 'abc'가 되는 것이다.

# 제너레이터(Generator) 종료방법

제너레이터를 종료하는 방법으로는 

`return()`
`throw()`

두 방법이 있다.
