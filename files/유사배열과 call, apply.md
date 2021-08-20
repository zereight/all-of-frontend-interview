# 유사배열과 call, apply



```js
var array = [1,2,3];
array; // [1,2,3]

var nodes = document.querySelectorAll('div'); // NodeList
var els = document.body.children; // HTMLCollection
```



위 코드에서 array는 배열이고,

`nodes`, `els` 는 유사배열이다.



둘다 []으로 감싸어져 있어서 헷갈릴 수 있다.

Array임을 판단할 수 있는 함수인 `Array.isArray` 를 통해 판별을 해보면,

```js
Array.isArray(array); // true
Array.isArray(nodes); // false
Array.isArray(els); // false
```

으로 나온다.



이런 `node`, `els` 같은 것들을 유사배열이라고 부른다.



유사배열은 다음과 같이 구성된다.

```js
var temp = {
  0: 'a',
  1: 'b',
  2: 'c',
  length: 3
}
```

인덱스를 0부터 차례대로 가지고 있고, length 프로퍼티를 가지고 있는 객체이다.

이게 바로 Array도 객체라는 사실을 이용하여 만들어진 트릭인데,  실제 Array처럼 `temp[0]` `temp.length` 등으로 사용할 수 있다.

하지만, Array의 `map`, `forEach`  등의 메서드는 사용할 수 없다. (NodeList의 forEach는 자체적으로 구현된 것임)



유사배열에서 `map`, `forEach` 를 쓰려면? 

`Array.from` 을 사용하거나,

`call`, `apply` 메서드를 사용할 수 있다.

```js
Array.prototype.forEach.call(nodes, el => console.log(el));

[].forEach.call(nodes, el => console.log(el));
```

처럼!







Ref

https://www.zerocho.com/category/JavaScript/post/5af6f9e707d77a001bb579d2