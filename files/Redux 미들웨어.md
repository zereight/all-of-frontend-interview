## Redux 미들웨어

리덕스 미들웨어는 리덕스가 지니고 있는 핵심 기능이다.

Context API 또는 Mobx를 사용하는 것과 차별화가 되는 부분이기도 하다.



미들웨어를 사용하면 액션이 dispatch된 다음, reducer에서 해당 액션을 받아와서 업데이트 하기 전에 추가적인 작업을 할 수 있다.

보통 다음과 같은 용도로 사용된다.

1. 특정 조건에 따라 액션이 무시되게 만들기
2. 로깅
3. 특정 액션이 발생했을 때에 다른 액션이 발생되도록 하기
4. 특정 액션이 발생했을 때에 js함수를 실행시키기

보통 redux 미들웨어에서 사용하는 주된 용도는 비동기 작업입니다.

물론 비동기 작업을 Promise등을 활용하여 접근하여도 무방합니다. 그냥 syntax sugar입니다.

이러한 비동기를 처리하는 middleware가 [나온이유](https://stackoverflow.com/questions/34570758/why-do-we-need-middleware-for-async-flow-in-redux)는 그와 관련된 js 함수들을 action과 분리해놓을 수 있는 효과를 낼 수 있습니다. (관심사 분리)