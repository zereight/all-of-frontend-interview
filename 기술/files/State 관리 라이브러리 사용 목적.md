## ***State 관리 라이브러리 사용 목적은 무엇인가***

- https://woowabros.github.io/experience/2019/01/02/kimcj-react-mobx.html

  

- 다중 계층 컴포넌트에서 데이터와 메소드 접근의 복잡성 해결
  여러개의 Component 가 조합되어 페이지가 구성된다고 할 때, 
  Component간 상호작용 (State, Props)와 메서드의 접근이 까다롭게 된다.

  SPA가 없던 시절에는 서버렌더링 페이지에서 jquery로 dom을 조작하고 함수를 호출할 때에는 Global Scope에서 대부분 이루어져서 크게 문제가 없었다.

  그러나 기능 단위의 Component로 이루어진 최근의 SPA 프레임워크에서는 부모자식의 관게로 Scope가 이루어져있기 때문에, 각 Component간 State와 메서드 접근이 복잡해질 수 있다.

  이를 해결하기 위해서 State를 Global한 Store영역에서 관리하는 방법을 사용하여 state와 메서드의 접근이 용이하게 된다.

  또한, 계층이 깊어질 수록, 전역 상태 관리 라이브러리를 사용하지 않게 되면, 하위 계층의 컴포넌트에 prop을 내려주는 역할만하는 컴포넌트가 증가할 수 있다.



- 컴포넌트에 집중된 비즈니스 로직의 분리

  ​	State 관리 없이, React Component로만 개발하게 되면, 거의 대부분의 비즈니스 로직이 Component에만 집중되게 될 것이고, 스파게티 코드가 완성되어질 것이다.

  하지만 State 상태관리 라이브러리를 사용하게 되면, Component는 Controller에 해당하는 역할을 하게 두고, 나머지 로직은 적절히 분리하여 아키텍처를 구성할 수 있는 이점이 있다.

  

