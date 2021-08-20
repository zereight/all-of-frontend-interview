# async 이터레이터와 제너레이터

https://ko.javascript.info/async-iterators-generators

비동기 이터레이터를 사용하면 비동기적으로 들어오는 데이터를 필요에 따라 처리할 수 있다.



## async 이터레이터



비동기 이터레이터는 일반 이터레이터와 유사하며, 약간의 문법적인 차이가 있다.

아래는 일반 이터러블 객체이다.

```js
let range = {
  from: 1,
  to: 5,
  
  [Symbol.iterator](){
    return {
      current: this.from,
      last: this.to,
      
      next(){
        if(this.current <= this.last){
          return {done: false, value: this.current++};
        }else{
          return {done: true};
        }
      }
    }
  }
}


```



이제 이터러블 객체를 비동기적으로 만들어봅시다.

1. `Symbol.iterator` 대신에 `Symbol.asyncIterator` 를 사용해한다.
2. next()는 Promise를 반환해야 한다.
3. 비동기 이터블 객체를 대상으로 하는 반복작업은 `for await (let item of iterable)` 반복문을 사용해서  처리해야 한다.



아래는 1초마다 비동기적으로 값을 반환하는 이터러블 객체이다.



```js
let range = {
  from: 1,
  to: 5,
  
  [Symbol.asyncIterator](){
    return {
      current: this.from,
      last: this.to,
      
      async next(){
        await new Promise(resolve => setTimeout(resolve, 1000));
        
        if(this.current <= this.last){
          return {done: false, value: this.current++};
        }else{
          return {done: true};
        }
      }
    }
  }
}

(async () => {
  for await (let value of range){
    alert(value); // 1,2,3,4,5
  }
})
```



위 예시에서 볼 수 있듯이, async iterator는 일반 이터레이터와 구조가 유사하다.

하지만 아래와 같은 다른 점이 있다

1. 객체를 비동기적으로 반복 가능하도록 하려면, Symbol.asyncIterator 메서드가 반드시 구현되어 있어야 한다.
2. Symbol.asyncIterator는 Promise를 반환하는 next()가 구현된 객체를 반환해야 한다.
3. next() 는 반드시 async일 필요는 없다.
4. 반복 작업을 하려면 `for await (let value of range)` 를 사용한다. 



- 주의할점

Symbol.asyncIterabor도 이터레이터라서 spread 연산자를 쓰려고하면 에러가 난다.



