# 참조 타입에 대해 설명해주세요 (feat. obj.method를 할때 자바스크립트에서는 어떤일이 발생할까)

https://ko.javascript.info/reference-type

복잡한 상황에서 메서드를 호출하면 this값을 잃어버리는 경우가 있다.

```js
let user = {
  name: "John",
  hi() {
    alert(this.name);
  },
  bye() {
    alert("Bye");
  },
};

user.hi(); // John

(user.name === "John" ? user.hi : user.bye)(); // Error
```

마지막 줄에서 조건부 연산자를 사용해서 user.hi나 user.bye중 하나가 호출되도록 했는데, 어떤건 정상적으로 호출이 되었고, 어떤건 에러가 발생했다.

```js
user.hi();
```

는 정상적으로 호출이 되었고

```js
(user.name === "John" ? user.hi : user.bye)();
```

여기서는 에러가 발생했다.

원인이 무엇일까?

## 참조 타입 자세히 알아보기

obj.method를 할때 자바스크립트에서는 어떤일이 발생할까

1. `.`을 통해서 obj.method를 통해 객체 프로퍼티에 접근한다.
2. `()`는 접근한 프로퍼티(메서드)를 실행한다.

위 동작으로 실행하는데,

```js
user.hi();
```

는 어떻게 this가 제대로 전달되었을까?

```js
let hi = user.hi;
hi(); // Error
```

위 코드는 왜 this가 제대로 전달되지 않았을까?

> 왜냐하면 '.'이 함수가 아닌 참조타입값을 반환하기 때문이다.

참조 타입은 명세서에서만 사용되는 타입으로 개발자가 실제로는 사용할 수 없다.

참조 타입은 다음과 같은 3가지 조합으로 이루어져 있다.

- base: 객체
- name: 프로퍼티 이름
- strict: 엄격모드에서 true

즉, `user.hi` 로 프로퍼티에 접근하면, 함수가 아닌 참조 타입을 반환한다.

엄격 모드인 경우, 다음과 같이 반환된다.

`(user, hi, true)`

이런 참조형 값에 `()` 를 붙여서 호출하면 객체의 메서드와 연관된 모든 정보를 받는다. 이 정보를 기반으로 this(user)가 결정된다.

즉, 참조 타입은 `.` 연산에서 알아낸 정보를 `()`로 전달해주는 중개인 역할을 하는 것이다.

근데, 점 연산 이외의 연산(할당 연산 등)은 참조타입을 통째로 버리고 `user.hi` 값만 받아서 전달한다.

그렇기 때문에 점 이외의 연산에서는 this정보가 사라진다.

즉,

```js
obj.method();
obj.method();
obj[method]();
```

위와 같은 코드에서는 참조 타입을 사용하여 this값이 의도한 대로 전달되지만

```js
a = obj.method;
a();
```

위 처럼 할당 연산을 하게되면 참조 타입을 버리므로, this가 원하는대로 전달되지 않는다. 이런경우는 `bind` 를 사용하여 해결할 수도 있다.

```js
let obj, method;

obj = {
  go: function () {
    alert(this);
  },
};

obj.go(); // (1) [object Object]

obj.go(); // (2) [object Object]

(method = obj.go)(); // (3) undefined => 할당 연산때문

(obj.go || obj.stop)(); // (4) undefined => 그냥 메서드 호출 연산빼고 모두 참조 타입을 버린다고 생각하자.
```
