# Typescript 에서 enum, const enum, union types



[출처](https://engineering.linecorp.com/ko/blog/typescript-enum-tree-shaking/)



Enum은 열거형 데이터 타입으로 상수들을 명명하여 나열한 집합을 정의한 것이다.

임의의 숫자나 문자열을 할당할 수 있고, 하나의 유형으로 사용해서 버그를 줄일 수 있다.



**하지만**

Typescript에서 enum을 사용하면 Tree-shaking이 되지 않는다.

왜냐하면 Typescript가 자체적으로 구현했기 때문이다.

실제로 트랜스파일링 해보면 Tyescript 컴파일러는 IIFE를 포함한 코드를 생성하여 enum을 구현하는데, 번들러는 IIFE를 사용하지 않는 코드라고 판단할 수 없어서 Tree-shaking이 되지 않습니다.



이를 해결하기 위한 방법으로 

**Union Types**를 사용할 수 있다.

```tsx
const MOBILE_OS = {
  IOS: 'iOS',
  Android: 'Android'
} as const;
type MOBILE_OS = typeof MOBILE_OS[keyof typeof MOBILE_OS]; // 'iOS' | 'Android'
```

이렇게 사용하면, 아래와 같이 컴파일 된다.

```ts
const MOBILE_OS = {
    IOS: 'iOS',
    Android: 'Android'
};
```

타입을 정의한 이점을 그대로 누리면서, JS로 트랜스파일링해도 IIFE가 생성되지 않아서 Tree-shaking을 할 수도 있다.



**const enum은?**

사용을 해보면 enum과 별 차이를 못느끼지만, enum의 내용이 트랜스파일할 때, 인라인으로 확장된다는 점이 다르다.

```ts
const enum MOBILE_OS {
    IOS = 'iOS',
    ANDROID = 'Android',
}
const ios = MOBILE_OS.IOS
```

위 코드는 아래와같은 JS코드로 트랜스파일된다.

```ts
const ios = "iOS";
```



이렇게하면 Union Types처럼 Tree-shaking이 가능해진다.

하지만! 

긴 문자열을 할당하는 경우에는 Union Types와 비교해서 부족한 점이 있다.



```ts
// TypeScript
const enum NAME {
  JUGEM = '寿限無寿限無五劫の擦り切れ海砂利水魚の…', // 일본에서 '김수한무 거북이와 두루미 삼천갑자 동방삭...'과 비슷한 용도로 사용하는 긴 이름입니다.
TARO = '다로', 
JIRO = '지로', 
} 
const isJugem = name === NAME.JUGEM
 
// JavaScript 트랜스파일 후
const isJugem = name === "\u5BFF\u9650\u7121\u5BFF\u9650\u7121\u4E94\u52AB\u306E\u64E6\u308A\u5207\u308C\u6D77\u7802\u5229\u6C34\u9B5A\u306E\u2026" /* JUGEM */;
```

위 예제를 보아, const enum은 Babel로 트랜스파일링 안되는 것을 볼 수 있습니다.



> 순위

Union Types > const enum > enum

