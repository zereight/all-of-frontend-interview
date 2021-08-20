# iterable 객체란 feat. 이터레이터, 제너레이터



iterable === 반복 가능한 객체

배열을 일반화한 것이다.



이터러블 개념을 활용하면 어떤 객체에서든 for..of 반복문을 적용할 수 있다.



# 이터러블 vs 이터레이터

이터러블은 Symbol.iterator 메서드를 가지고 있는 객체를 말한다.

이터러블 객체는 for..of 문으로 순회할 수 있고, spread 문법의 피연산자로 사용할 수 있다.



이터러블 객체의 Symbol.iterator 메서드를 호출하면 iterator 객체를 반환한다.

반환된 iterator 객체는 next 메서드를 소유하고 있다.

이 next메서드를 호출할때, iterator result 객체를 반환한다면 iterator라고 할 수 있다.
(``obj[Symbol.iterator]()`` 으로 반환되는게 iterator!!)



iterator result는 value, done 프로퍼티를 가지고 있고, 순회가 끝날 시 done은 true, value는 undefined를 반환하는 객체이다. (value는 현재값, done는 순회가 언제끝나는가)



## 이터러블 객체 만들기

```js
const range = {
  from: 1,
  to: 5
}

range[Symbol.iterator] = function(){
  return {
    current: this.from,
    last: this.to,
    
    next(){
      if(this.current <= this.last) {
        return {done: false, value: this.current++};
      }else{
        return {done: true};
      }
    }
  }
}

for (let num of range) {
  alert(num);
}
```



위와 같이 Symbol.iterator를 사용해서 이터러블 객체를 만들 수도 있고,

제너레이터를 사용해서 만들 수도 있다.

```js
function* counter() {
  yield 1;
  yield 2;
  yield 3;
}

const generatorObj = counter();

// for..of로도 사용가능!
for(const i of generatorObj) {
  console.log(i);
}

// next를 사용해서도 가능!
generatorObj.next();

```





## 왜 이터러블 객체를 사용하나요?

이터터블 객체의 핵심은 관심사의 분리에 있다.

range에는 next()가 없다.

대신에 range`[Symbol.iterator]()` 를 호출해서 만든 이터레이터 객체와 반복할 값을 저장해 놓는다.



이렇게 하면 "이터레이터 객체"와 "반복 대상인 객체"를 분리할 수 있다.



## 문자열은 이터러블인가요?

배열과 문자열은 가장 광범위하게 쓰이는 내장 이터러블이다.



## 이터러블과 유사배열의 차이점은 무엇인가요?

- 이터러블은 Symbol.iterator가 구현된 객체
- 유사배열은 index, length 프로퍼티가 있어서 배열처럼 보이는 객체



