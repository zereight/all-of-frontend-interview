# enum vs const enum 상세 비교 (feat. 역맵핑)

[출처](https://velog.io/@logqwerty/Enum-vs-as-const)



객체 리터럴에 `as const`를 사용하면 `enum`과 유사한 효과를 낼 수 있습니다.

하지만 사용 목적이, 상수들을 하나로 묶어 추상화시키는 것이라면, `enum`을 사용하는 것이 목적에 맞습니다.



애초에 목적이 다르기 때문에 차라리 비교를 한다면

`enum`과 `const enum`을 비교하는게 낫습니다.

위 2개는 목적은 같으나, 트랜스파일된 결과는 아주 다르기 때문이지요.



아래는 enum의 트랜스파일링 코드입니다.

```ts
// transpile 이전
enum COLOR {
  red,
  blue,
  green
}

// transpile 이후
var COLOR;
(function (COLOR) {
    COLOR[COLOR["red"] = 0] = "red";
    COLOR[COLOR["blue"] = 1] = "blue";
    COLOR[COLOR["green"] = 2] = "green";
})(COLOR || (COLOR = {}));
```



IIFE로 되어있어서 가독성이 떨어지지만, 해석하면 다음과 같은 객체가 됩니다.

```ts
var COLOR = {
  red: 0,
  blue: 1,
  green: 2,
  '0': 'red',
  '1': 'blue',
  '2': 'green'
}
```



프로퍼티가 선언된다음 한번더 반대로 맵핑되고 있는 것을 알 수 있습니다.

이것을 [역맵핑(reverse mapping)](https://www.typescriptlang.org/docs/handbook/enums.html#reverse-mappings) 이라고 합니다.



아래는 const enum이 트랜스파일링된 코드입니다.

```ts
// transpile 이전
const enum COLOR {
  red,
  blue,
  green,
}
console.log(COLOR.red);
console.log(COLOR.blue);
console.log(COLOR.green);

// transplie 이후
console.log(0 /* red */);
console.log(1 /* blue */);
console.log(2 /* green */);
```



어째서인지 어떠한 객체 리터럴도 존재하지 않습니다!

const enum 프로퍼티에 접근하는 코드를 각 프로퍼티의 값을 치환해버리기 때문이지요!



**당연이 역맵핑이 필요하지 않은 경우라면 enum보다 const enum을 사용하는것이 맞겠지요?**

