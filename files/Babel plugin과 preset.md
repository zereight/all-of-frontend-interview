# Babel plugin과 preset



babel의 plugin은 실제로 코드를 변환시키는 기능을 담당한다.

예를 들어서 ES6의 화살표 함수 문법을 사용했다면, 이를 변환 시키기 위해서

`@babel/plugin-transform-arrow-function` 라이브러리가 필요하고, 
블럭 스코프를 사용헀다면, `@babel/plugin-transform-block-scoping` 라이브러리의 설치가 필요하다.

그런데 [여기](https://babeljs.io/docs/en/plugins-list) 를 보면 plugin이 굉장히 많다.

이것을 전부 설치해야할까? 그러면 번거롭고 내가 어떤 플러그인을 찾아야 하는지도 힘들 것이다.



그래서 **preset**이 등장하게 된다.

preset은 목적에 따라 plugin들을 모아놓은 라이브러리이다.

preset도 여러가지가 있는데, 그 중에서도 `@babel/preset-env` 라이브러리는 targets 옵션을 통해서 어떤 브라우저에도 유연하게 대응할 수 있기 때문에 가장 자주 쓰인다.

preset과 관련된 자세한 사항은 [여기](https://babeljs.io/docs/en/babel-preset-env)에서 참고하자.



Ref

https://velog.io/@code-bebop/babel과-webpack