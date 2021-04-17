[함수에 대해 아는 대로 말해보세요.](#what-is-function)

[일급 객체란 무엇인가요?](#first-class-object)

[함수 표현식, 함수 선언식이란 무엇인가요?](#function-expresstion)

[값, 식, 문](#literal,-expression,-statement)

[화살표 함수와 function의 차이점은 무엇인가요?](#arrow-function-vs-regular-function)

### What is function

> 함수의 정의

함수라는 용어 자체를 생각하자면, 어떤 함(函)에 input을 넣어서 그에 상응하는 output이 나오는 개념을 일컫는 말입니다. 실제 사용자는 "함"에 들어있는 동작을 몰라도 input을 넣어서 output을 얻을 수 있습니다.

> js에서의 함수 특징

자바스크립트에서는 함수는 function으로 표현할 수 있습니다,
function은 그 자체로 하나의 type으로 취급됩니다. 함수를 변수에 대입할 수도 있고, 함수에 프로퍼티를 지정하는 것도 가능합니다. 그리고 함수안에 함수도 정의할 수 있습니다.
이러한 자바스크립트에서의 함수를 [일급 객체](#first-class-object) 라고도 부릅니다.

> js에서 함수 사용법

자바스크립트 함수는 function예약어 => function 이름 => 괄호열기 => 파라미터들을 `,`로 구분하여 나열 => 괄호닫기 => 중괄호로 싸여진 코드블록
형태로 사용할 수 있습니다.

지금 설명드린 것과 다르게, function에 이름을 생략하여 익명함수를 사용할 수도 있습니다.

그리고 함수의 output은 `return`이라는 예약어를 통해 사용할 수 있습니다.
만약 자바스크립트에서 함수에 return을 안해줬다면 `undefined`가 반환되게 됩니다.

또한, 함수를 어떻게 정의하느냐에 따라서 [함수 표현식과 함수 선언식](#function-expresstion)으로 나뉩니다.

> 함수 실행의 6단계

기본적으로 함수의 동작을 caller와 callee로 표현하는데요.

함수 실행의 6단계는 다음과 같습니다.

0: 일단 현재 PC(프로그램 카운터)를 LR(링크 레지스터)에 저장한다.

1. caller는 callee가 액세스할 수 있는 a0~a3 총 4개의 레지스터에 파라미터 저장을 한다. (파라미터 개수가 4개를 넘어가면 스택에 저장)
2. caller가 callee에게 "너가 해!" 제어권을 넘긴다.
3. callee가 메모리 공간을 할당받는다.
4. callee는 이제 자기 할 일을 한다.
5. callee는 caller가 액세스할 수 있는 v0~1 레지스터에 리턴값을 저장한다.
6. callee는 v레지스터에 저장된 값을 넘기고, 제어권이 caller에게 넘어간다.

7: LR(링크 레지스터)에 있던 주소값을 PC로 전달하여 원래 동작을 수행한다.

[https://peter-cho.gitbook.io/book/7/7_2](https://peter-cho.gitbook.io/book/7/7_2)

</a>

### First class object

> 일급 객체의 정의

(작성중)

### Function expresstion

> 함수 선언식

(작성중)

> 함수 표현식

(작성중)

### literal, expression, statement

> 값, 식, 문

1. 값
   값은 프로그램에 의해 조작될 수 있는 대상을 말한다. 값은 다양한 방법으로 생성할 수 있으며, 가장 간단한 표기법은 리터럴이다.
   리터럴의 종류에는

   - 숫자 리터럴 `1001`
   - 문자열 리터럴 `"hi"`
   - 불리언 리터럴 `true`
   - null 리터럴 `null`
   - undefined 리터럴 `undefined`
   - 객체 리터럴 `{a:'1'}`
   - 배열 리터럴 `[1,2,3,4]`
   - 정규 표현식 리터럴 `/ab+c/`
   - 함수 리터럴 `function(){}`
     등이 있다.

2. 식
   식은 하나의 값으로 평가된다. 값, 변수, 객체의 프로퍼티, 배열의 요소, 함수 호출, 메소드 호출, 피연산자와 연산자 조합은 모두 표현식이고 하나의 값으로 평가된다.

   - `5*10 > 10`

3. 문
   문은 리터럴, 연산자, 표현식, 키워드 등으로 구성되고 세미콜론으로 끝나며, 프로그램에 의해 단계별로 수행될 명령들의 집합이다.
   - `var x = 5;`
   - `var z = x + y;`

식은 값으로 평가되기 때문에, 보통 '문'과 '식'으로 비교를 많이한다. '문'과 '식'의 차이는 `식은 값인 것`이고, `문은 값이 아닌것`이라고 할 수 있다.

### arrow function vs regular function

> 화살표 함수와 function의 차이점은 무엇인가요?

화살표 함수는 function 표현에 비해서 구문이 짧고(그래서 콜백 함수로 사용하기 적합), 자신의 this, arguments 등을 바인딩 하지 않습니다. (arguments 대시넹 rest 파라미터를 사용할 수 있습니다.) 또한 화살표함수는 prototype 속성이 없습니다.

화살표 함수는 항상 익명함수이고, function은 익명함수 또는 이름을 정의할 수 있습니다.

this가 따로 바인딩 되지 않으니까, 선언된 코드 바로 바깥의 함수의 this(lexical this)를 사용하는 것과 같습니다.
그에 반해, function의 this는 아래 처럼, 함수 종류에 따라서 this가 가리키는 객체가 다릅니다.

- 생성자 => 새로운 객체
- strict 모드 => undefined
- 메소드: 베이스 객체
- 콜백: 전역 객체 window

### Higher-order-function

> 고차 함수란 무엇인가요?

고차 함수는 한개 이상의 함수가 argument(전달인자) 이거나, 함수를 리턴시키는 함수를 의미합니다.

<code>const hof = () => () => 5</code>

높은 추상화가 적용된 고차 함수를 사용해서 명령형인 코드가 아니라, 선언적인 코드를 작성할 수 있다.
ex) filter이라는 고차 함수를 쓰지 않으면, for문을 활용해서 불필요한 코드들이 사용됨.

고차 함수를 활용하는 경우는 다음과 같습니다.

- 클로저

  ```js
  const closure = function () {
    let count = 0;
    return function increment() {
      count++;
      return count;
    };
  };
  const incrementFn = closure();
  incrementFn(); // 1
  incrementFn(); // 2
  ```

- 메모이제이션/캐싱

  ```js
  function memoizedAddTo80() {
    let cache = {};
    return function (n) {
      if (n in cache) {
        return cache[n];
      } else {
        cache[n] = n + 80;
        return cache[n];
      }
    };
  }

  const memoized = memoizedAddTo80();
  memoized(5); // 85
  ```

- 그 외 함수형 프로그래밍
  여기서 고차함수가 빛을 발하는 순간은 바로 함수형 프로그래밍이다.
