## ***React의 구성요소***

- React란?

  Javascript Web FrontEnd Redering 라이브러리 중 하나이다.

  > 보통 Single Page Application Framework가 대부분의 기능을 포함하고 있는 반면에, 
  > React는 Framework가 아니라, View Rendering하는 것이 주 기능이며,
  > 나머지 기타 기능 (router등)은 서드파티 라이브러리를 추가적으로 사용해야 한다.



- Component

  React에서 데이터를 화면에 렌더링하는 가장 기본이 되는 단위이다.

  React.Component를 상속하는 Class Component와
  함수 형태의 Function Component가 존재한다.

  React는 작은 단위 부터 큰 단위의 Component 조합으로 구성되며, 각각을 적절히 조합하여 Page를 구성하여 개발한다.

  

- State

  React Component에서 변경가능한 데이터를 State라고 부른다.
  

- Props

  자식 컴포넌트가 부모 컴포넌트로 부터 Paremeter로 받아오는 값을 말하며 변경할 수 없다.
  

- 불변성

  React에서 렌더링을 할 때 판단하는 방법은 State가 변경되었을 때 인데,

  변경 전/후 State를 서로 비교할 때 복잡도가 높은 객체의 경우, 자식 프로퍼티까지 비교하는 것보다 효율적인 방법으로 State의 레퍼런스가 변경되었을때 변경된 것으로 간주하고 렌더링을 한다.

  이런 경우 기존 State 값을 직접 변경하는 것이 아니라, 기존 State값을 바탕으로 하여 새로 생성된 객체의 레퍼런스를 setState 메서드를 통하여 변경하는데 불변성을 유지한다고 한다.

