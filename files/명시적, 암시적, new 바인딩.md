# This



this는 object를 참조하는 keyword이다



브라우저상에서 전역객체는 window이고
node에서의 this는 {} 빈객체가 출력된다. (실제로 node에서의 this는 module.exports이다.)



> this 바인딩 우선순위

1. 기본 바인딩

```js
function hello(){
  console.log(this.name);
}

var name = "doby";

hello();
```



위 예제는 `"doby"`가 출력된다.

기본적으로 자바스크립트는 this가 전역 객체에 바인딩되기 때문이다.
(만약 strict mode였다면 전역개체가 undefined여서 type error가 발생했을 것이다.)



2. 암시적 바인딩

암시적 바인딩은 함수 호출 시, 객체의 프로퍼티로 접근해서 실행하는 경우를 예로 들 수 있다.

```js
function hello(){
  console.log(this.name);
}

var obj = {
  name: "doby",
  hello
}

obj.hello(); // doby
```

Function 함수는 실행될때, 호출부의 객체 프로퍼티로 접근했을 경우, 이 객체를 this와 바인딩하는 규칙을 갖는다. (동적 바인딩) arrow function은 정적 바인딩이다.

```js
function hello() {
  console.log(this.name);
}

var obj = {
  name: 'doby',
  hello
}

helloFn = obj.hello;

name = "global text";

helloFn(); // global text
```



위 예제는 obj.hello로 비록, 프로퍼티로 접근을 했으나, helloFn에 함수의 참조값으로 저장함으로써 일반 함수처럼 취급된다.



```js
function hello() {
  console.log(this.name)
}

var obj = {
  name: "chris",
  hello: hello,
}

setTimeout(obj.hello, 1000)  // "global context!"

name = "global context!"
```

위 예제도 마찬가지고, `setTimeout` 의 콜백함수로 넘기는데 함수의 참조값을 넘기므로 일반함수처럼 취급된다.



3. 명시적 바인딩

암시적 바인딩 보다 더 직관적으로, 어떤 객체를 this에 바인딩할 것인지를 나타내는 방법이다.

call, apply, bind 함수가 그런 역할을 한다.

call과 apply를 함수의 인자 전달 방식만 다르다. (call은 인자를 순서대로 넣어주고, apply는 array로 넘겨줌 aa로 외우자! )

즉, call/apply는 사용할 this와 인자를 넘겨서 호출할 수 있고,
bind는 this를 바꾸기만할뿐 호출은 하지 않는다는 특징이 있다.



call이나 apply 첫 인자로 null을 주면 undefined가 아니라 기본 바인딩을 통해서 전역객체를 바라보게 된다.

bind도 2번째인자를 줄 수 있는데, 2번째인자는 해당 함수의 인자를 고정시켜버리는 역할을 한다.



4. new 바인딩

new 바인딩은 함수 앞에 new를 실행해서 사용한다.
그와 동시에 this가 해당 객체로 바인딩 된다.

즉, new로 반환된 obj 객체는 this와 바인딩되는 것이다.



---



요약

# 명시적/암시적 바인딩, 동적/정적 바인딩



> 명시적 바인딩

bind/apply/call을 사용하여 "난 객체를 이 this로 바인딩 할거야" 라고 코드에 의도를 나타내는 방법을 말한다.



> 암시적 바인딩

함수 호출 시, 객체의 프로퍼티로 접근해서 그 객체의 this와 바인딩하는 방법을 말한다.



> 정적 바인딩

arrow function을 예로 들 수 있으며, 함수를 선언할 때 this에 바인딩할 객체가 정적으로 결정되는 것을 말한다.



> 동적 바인딩

일반 function 처럼, 함수를 호출할 때 함수가 어떻게 호출되었는지에 따라서 this에 바인딩할 객체가 동적으로 결정되는 것을 말한다.



그 외)

기본 바인딩은 기본적으로 전역 객체에 컨텍스트가 바인딩되는 규칙을 말하고,

new 바인딩은 new로 반환된 obj 객체를 this 컨텍스트와 바인딩되는 규칙을 따르는 것을 말한다.



Ref

https://velog.io/@proshy/JS-상황에-따른-this-바인딩

https://jeonghwan-kim.github.io/2017/10/22/js-context-binding.html