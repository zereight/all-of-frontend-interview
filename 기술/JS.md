[함수에 대해 아는 대로 말해보세요.](#what-is-function)

[일급 객체란 무엇인가요?](#first-class-object)

[함수 표현식, 함수 선언식이란 무엇인가요?](#function-expresstion)

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
