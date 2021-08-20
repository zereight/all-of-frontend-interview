# as const



[출처](https://velog.io/@logqwerty/Enum-vs-as-const)



Typescript에서 가독성을 높이기 위한 수단으로 서로 연관된 상수들을 하나의 namespace에 묶어서 관리할 때, 다음과 같이 `as const`라는 키워드로 type assertion을 할 수 있습니다.

또한, 같은 목적으로 `enum`을 사용할 수도 있는데,

이 둘은 목적부터 다릅니다.



`enum`은 다른 언어의 Enum 문법처럼 서로 연관된 상수들을 하나의 namespace로 묶어서 추상화시키기 위해 도입된 것입니다.

반면, `as const`는 type assertion의 한 종류로써 리터럴 타입의 **추론 범위를 줄이고**, **값의 재할당을 막기위한 목적**으로 만들어졌습니다.



>  추론 범위를 줄인다

아래 코드를 한번 봅시다.

```ts
const greeting1 = "hello world"; // "hello world"으로 추론
let greeting2 = 'hello world'; // string으로 추론
```



typescript는 const로 선언할 경우, 자동으로 리터럴 자체로 타입을 추론합니다.

하지만 let으로 선언하면, 리터럴이 속한 타입으로 타입을 추론하게 됩니다.

만약, let으로 선언했는데 리터럴로 한정시키고 싶다면

```ts
let greeting2 = "hello world" as const;
```



위와 같이 `as const`를 통해서 type assertion을 해주어야 합니다.

const 로 선언된 것과 똑같은 효과를 일으키기 때문이죠.

(물론 위와 같은 상황에서는 그냥 const로 선언하세요 ㅎㅎ)





그럼 애초부터 const로 선언했으면 되는 건데.. 도대체 어디에 사용해야할까요?

바로 Object 같은 참조 타입에서 사용합니다.

`const obj = {a: 1};` 이라도 a를 변경할 수 있기 때문이죠.



예를 들어 봅시다.

```ts
const language = {
  korean: "ko", // string으로 추론됨
  english: "en" // string으로 추론됨
};

language.korean = 'ko2'; 
language.english = 'en2';
```



const로 선언했는데도, string으로 추론됨을 알 수 있습니다!



하지만 `as const`를 사용하면 어떻게 될까요?

```ts
const language = {
  korean: "ko", // 'ko' 으로 추론됨
  english: "en" // 'en' 으로 추론됨
} as const;

language.korean = 'ko2';  // 수정 불가 (read-only)
language.english = 'en2'; // 수정 불가 (read-only)
```

객체의 모든 프로퍼티들이 readOnly로 변경되고, 각 프로퍼티들이 리터럴 값으로 추론되게 됩니다! (depth 상관 x)









