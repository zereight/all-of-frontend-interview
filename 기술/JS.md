[함수에 대해 아는 대로 말해보세요.](#what-is-function)

[일급 객체란 무엇인가요?](#first-class-object)

[함수 표현식, 함수 선언식이란 무엇인가요?](#function-expresstion)

[값, 식, 문](#literal-expression-statement)

[화살표 함수와 function의 차이점은 무엇인가요?](#arrow-function-vs-regular-function)

[함수형 프로그래밍이란 무엇인가요?](#functional-programming)

[즉시 실행 함수 (IIFE)](#iife)

[옵셔널 체이닝은 언제 사용해야 하나요?](#optional-chaining)

[컨텍스트와 스코프에 대해서 설명해주세요.](#context-scope)

[런타임과 컴파일](#runtime-compiletime)

[동적 타이핑, 정적 타이핑](#dynamic-typing-and-static-typing)

[Prototype에 관하여](#proptotype)

[attributes vs property](#attributes-vs-property)

[디바운스와 쓰로틀링](#debounce-throttling)

[focusout과 blur의 차이](#focusout-blur)

[명시적/암시적 바인딩, 동적/정적 바인딩](#binding)

[바인딩 우선순위](#binding-priority)

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

### 명시적/암시적 바인딩, 동적/정적 바인딩

### Binding

> 명시적 바인딩

명시적 바인딩은 bind/apply/call을 사용하여 "난 객체를 이 this로 바인딩 할거야!" 라고 코드에 의도를 나타내는 방법을 말한다.

> 암시적 바인딩

암시적 바인딩은 함수 호출시, 객체의 프로퍼티로 접근해서 그 객체의 this와 바인딩하는 방법을 말한다.

> 정적 바인딩

정적 바인딩은 arrow function를 예로 들 수 있다. 함수를 선언할 때 this에 바인딩할 객체가 정적으로 결정되기 때문이다.

> 정적 바인딩

동적 바인딩은 일반 function를 예로 들 수 있다. 함수를 호출할 때 함수가 어떻게 호출되었는지에 따라서 this에 바인딩할 객체가 동적으로 결정되기 떄문이다.

그 외)

> 기본 바인딩

기본 바인딩은 기본적으로 전역 객체에 컨텍스트가 바인딩되는 규칙을 따르는 것을 뜻한다.

> new 바인딩

new 바인딩은 new로 반환된 obj 객체를 this 컨텍스트와 바인딩되는 규칙을 따르는 것을 뜻한다.

### Binding-priority

new 바인딩 > 명시적 바인딩 > 암시적 바인딩 > 기본 바인딩

[https://jeonghwan-kim.github.io/2017/10/22/js-context-binding.html](https://jeonghwan-kim.github.io/2017/10/22/js-context-binding.html)

### First class object

> 일급 객체의 정의

일급 객체란 아래 3가지 조건을 충족하면 1급 객체라고 부를 수 있다.

1. 변수나 데이터에 할당 할 수 있어야 한다.
2. 인자로 넘길 수 있어야 한다.
3. 리턴값으로 리턴할 수 있어야 한다.

즉, 특정언어에서 일급 객체란, 일반적으로 다른 객체들에 적용가능한 연산을 모두 지원하는 객체를 가리킨다.

아래는 일급 함수의 특징이다.

4. 익명으로 생성이 가능하다.
5. 런타임에 생성이 가능하다.

자바스크립트에서 함수는 1급 객체이자, 1급 함수라서 콜백패턴, 고차함수, 클로저, 커링, 메모이제이션 등이 가능해진다.

### Function expresstion

> 함수 선언식

(작성중)

> 함수 표현식

(작성중)

### literal-expression-statement

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
  여기서 고차함수가 빛을 발하는 순간은 바로 [함수형 프로그래밍](#functional-programming)이다.

###functional programming

> 함수형 프로그래밍

함수형 프로그래밍을 사용함으로써 얻을 수 있는 장점 대표적인 2가지는
"높은 수준의 추상화", "함수 단위의 재사용"이 있다.

1.  높은 수준의 추상화
    기본적으로 함수형 프로그래밍은 선언형 프로그래밍의 특성을 함수들의 조합을 사용하여 구현하는 패러다임이다.
    명령형 프로그래밍, 객체지향 프로그래밍 보다 높은 수준의 추상화를 통해서 개발자가 문제 해결에만 집중할 수 있게 해준다는 점이 큰 장점이다.

    코딩테스트를 c++로 보거나, python/js로 볼때 큰 차이점을 느낀 사람도 있을 것이다. c++은 대표적인 명령형 프로그래밍으로 사용자가 컴퓨터에게 어떻게 동작해야할지 로우 레벨까지 일일히 모두 정의해줘야하지만, python/js는 높은 수준의 추상화를 통해서 사용자가 오로지 문제해결에만 집중할 수 있도록 도와주어 코딩테스트에 유리하다고 할 수 있다. (python이 js보다 내장 라이브러리가 더 많아서 인기 많음.)

    포토샵도 그렇다. 이미지 프로세싱은 생각보다 복잡한 연산을 필요로하는데 우리는 포토샵이 제공하는 추상화된 기능들을 통해서 포토샵 행위에만 집중할 수 있다.

    즉, 높은 수준의 추상화는 복잡한 무언가에서 핵심적인 개념이나 기능을 간추려서 단순하게 만드는 것을 의미하고 이것은 사용자가 프로그램을 사용하는데 있어서 편함을 제공할 수 있다.

    물론, 높은 수준의 추상화의 단점은 "성능이 안좋다", "이렇게 추상화하면 최적화는 어떻게 하나"와 같은 논란에 휩싸이고 대표적으로 자바, GC가 있다. [예시](https://evan-moon.github.io/2019/12/15/about-functional-thinking/)

2.  함수 단위의 코드 재사용
    객체지향 프로그래밍에서 어떤 존재를 추상화하여 표현하고 재사용할 수 있는 최소 단위는 객체이기 때문에, 그 이상 작게 쪼개기 힘들어진다. 하지만 함수형 프로그래밍에서는 객체로 표현된 큐나 스택이 아닌, 이 존재들의 자료를 다루는 동작에만 집중한다.
    예를 들어서

```js
const queue = [1, 2, 3];
queue.push(4);
const head = queue.shift();

const stack = [1, 2, 3];
stack.unshift(0);
stack.shift();
```

위와 같은 코드처럼, 딱히 객체로 선언하지 않아도 함수들을 재사용할 수 있다.

다만, 이렇게 작은 단위의 함수를 넓은 범위로 재사용하게 되면, 프로그램의 복잡성이 빠르게 증가하기 때문에 이를 방어하기 위해서, 함수가 함수 외부에 있는 값을 수정하면 안된다거나, 같은 input이면 같은 output을 반환해야한다는 몇 가지 제약 조건이 필요하게 되었는데 그렇게 탄생한 개념이 `순수 함수`이다.

### iife

> 즉시 실행 함수 (IIFE)

Immediately Invoked Function Expression

즉, 정의되자마자 즉시 실행되는 함수를 뜻한다.

> 어떻게 동작하나요?

```js
(function () {
  statements;
})();
```

크게 2가지로 구분할 수 있다.

1. ()로 둘러싸인 익명함수
2. 즉시 실행 함수를 생성하는 ()

`function() {}` 으로만 선언되는 경우, 파서는 '문'으로 인식합니다.
'문'은 자바스크립트 해석기에게 명령을 지시하고 사라지는 것이기 때문에 '값'으로 남지 않습니다.

따라서, ()으로 묶어서 함수 선언'문'이 아닌, 함수 표현'식'이라는 것을 명시적으로 나타내어야 합니다.
물론 ()으로 묶지 않더라도, 앞에 연산자를 붙여준다면 즉시 실행 함수로 사용할 수 있습니다.

```js
+(function (a, b) {
  return console.log(a + 1);
})(1 + 2)(
  // 3
  function (a, b) {
    return console.log(a + 1);
  }
)(1 + 2); // 3
```

### optional-chaining

> 옵셔널 체이닝은 언제 사용해야 하나요?

존재하지 않을 수도 있는 메서드를 호출할떄 사용한다.
즉, 함수 호출과 optional chaining을 사용하면, 메서드를 찾을 수 없는 경우에
해당 표현식이 자동으로 undefined를 반환하게 할 수 있다.

### context-scope

> 컨텍스트와 스코프에 대해서 설명해주세요.

1. 컨텍스트
   컨텍스트는 객체를 기반으로 한 용어로써, 함수가 어떻게 호출되는지에 따라서 this를 지칭하는 객체가 달라지게 되는데, 이렇게 현재 this가 무엇을 지칭하느냐를 구분짓는 것이 컨텍스트이다.
   만약, 함수 a와 b의 this가 서로 다른 객체를 지칭하고 있는경우, 두 함수의 컨텍스트는 다르다고 할 수 있다.

2. 스코프
   스코프는 함수를 기반으로한 용어이다. 특정 함수가 실행될 때,
   해당 함수에서 변수에 대한 접근 범위가 어디까지 인지를 나타내는 개념이 스코프이다.

### runtime compiletime

> 런타임과 컴파일 타임

1. 런타임
   컴파일 과정을 마친 프로그램이 사용자에 의해 실행될때의 환경 또는 시간.
   자바스크립트는 Node.js, Browser를 런타임이라고 부를 수 있다.

2. 컴파일 타임
   컴파일은 원시코드에서 목적코드로 옮기는 과정을 말하며, 일반적으로 사람이 이해하기 쉬운 자연어를 기계어 또는 어셈블리어로 번역하는 과정이다.
   그러므로, 컴파일 타임은 컴파일이 진행되는 과정. 즉, 소스코드가 기계어 코드로 변환되는 일련의 과정을 뜻한다.

### dynamic-typing-and-static-typing

> 정적 타이핑과 동적 타이핑

1. 정적 타이핑
   자료형을 컴파일 당시에 결정하는 것으로, 변수에 들어갈 값을 사전에 정의해놓아야한다. 컴파일 진행 시, 자료형에 맞지 않는 자료형이 할당되면 컴파일 에러를 발생시킨다.
   C, C++, Java 등이 이런 언어에 속하며, 컴파일 당시에 자료형에 대한 판단을 진행하기 때문에 속도가 빠르고 타입 에러로 발생하는 문제점을 초기에 발견할 수 있다.

2. 동적 타이핑
   정적 타이핑과 다르게, 자료형을 컴파일 타임이 아닌, 런타임에 결정하는 것으로, 자료형의 명시 없이 병수명만 가지고 선언 및 값을 할당하는 것이 가능하다.
   python, js 등이 잇으며 런타임 당시에 타입에 대한 결정을 진행하므로 프로그래밍 입장에서는 편할 수 있지만, 런타임 동안 예상치 못한 에러가 발생할 수 있고, 정적 타이핑 언어에 비해서 느린 편이다.

### proptotype

> 프로토 타입이란

자바스크립트는 프로토타입 기반 언어이다.
프로토타입 기반 프로그래밍은 객체지향 프로그래밍의 한 형태인데, 클래스가 없고, 클래스 기반 언어에서 상속을 사용하는 것과 다르게, 객체를 프로토타입으로 하여서 복제의 과정을 통해서 객체의 동작 방식을 다시 사용할 수 있다.

prototype 단어의 뜻은 객체의 원형을 뜻한다.

```js
// 아래 두 코드는 같다.
function Person() {}
var Person = new Function();
```

```js
function Person(name, first, second) {
  this.name = name;
  this.first = first;
  this.second = second;
}

Person.prototype.sum = function () {};
```

위 코드를 살펴보자.
위 코드는 Person 객체를 생성하였으므로 Person과 Person의 prototype, 2개의 객체가 생성된다.

1. Person
2. Person's prototype

Person은 prototype 프로퍼티를 가지고 있으며 이것은 Person's prototype을 기리킨다.
Person's prototype의 constructor는 Person을 기리킨다.

그리고 Person's prototype은 sum이라는 프로퍼티도 가지고 있다.

이 상태에서 kim, lee라는 새로운 객체를 생성하면

```js
var kim = new Person("kim", 10, 20);
var lee = new Person("lee", 20, 30);
```

kim이라는 객체가 생성되고 kim은 "**proto**"라는 프로퍼티를 가지며, 이것은 Person's prototype을 가리킨다.
lee도 마찬가지 이다.

이때 kim.sum()을 수행하면, kim에서 sum이라는 프로퍼티를 찾고, 그것이 없으면 "**proto**"로 프로토타입으로 이동하여 sum이라는 프로퍼티가 존재하는지 확인한다.

즉, "**proto**"는 모든 객체가 가지고 있는 속성이고 prototype은 함수 객체만의 가지고 있는 프로퍼티이며, 함수 객체가 생성자로 사용될때 부모역할을하는 객체를 가리킨다.

### attributes-vs-property

> 속성과 프로퍼티

- 속성(attr)
  attr는 html문서에서 엘리먼트에 추가적인 정보를 넣을 때 사용되는 요소이다.

- property
  프로퍼티란 html DOM안에서 attr를 가리키는 표현이다.

왜 attribute와 property를 구별하는 걸까?

attr는 html dom/file안에서, property는 html DOM tree안에서 존재한다.

이것이 뜻하는 바는 attr는 정적으로 변하지 않고, property는 동적으로 그 값이 변할 수 있다는 것을 내포한다.
예를 들자면 사용자가 체크박스에 체크를 하면, attr의 상태는 편하지 않지만, property의 상태는 checked로 변하게 된다.

즉, attr는 속성 자체이고, property는 속성값을 다루는 용도로 사용하게 된다.

제이쿼리에서는 어떻게 분리하고 있을까?

```js
<checkbox id="my-checkbox" type="checkbox" checked />;

var $checkbox = $("#my-checkbox");

alert($checkbox.attr("checked")); // checked 속성의 값을 표시

alert($checkbox.prop("checked")); // checked 프로파티값을 표시
```

prop은 checked의 값인 true를 반환하고, attr는 속성값 자체인 checked를 반환하는 것을 알 수 있다.

### debounce-throttling

> 디바운스

디바운스는 어떤 이벤트가 여러번 발생할 때, 처음 또는 마지막 이벤트만이 실행되도록 만드는 개념이다.

```js
let debounce = null;

const func = (e) => {
  if (debounce) {
    clearTimeout(debounce);
  }

  debounce = setTimeout(() => 동작, 시간);
};
```

> 쓰로틀링

쓰로틀링은 어떤 이변트가 여러번 발생할 때, 일정 시간 동안 함번만 실행되도록 만드는 개념이다.

```js
let throttling = null;

const func = (e) => {
  if (!throttling) {
    throttling = setTimeout(() => {
      clearTimeout(throttling);
      동작;
    }, 시간);
  }
};
```

### focusout-blur

> 차이점

focusout은 의미 그대로 엘리먼트가 포커스를 잃었을 때 발생되는 이벤트이다.

하지만 blur도 포커스를 잃었을 때 발생되는 이벤트이다.

기능은 같지만 차이점은 버블링 여부이다.

focusout은 다른 이벤트들 처럼 버블링이 일어나고, blur는 버블링이 일어나지 않는다.

보통
focusin - focusout
focus - blur 이렇게 짝을 이루어서 분류된다.
