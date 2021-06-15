## ***Flux 패턴에서 다양한 구현 라이브러리가 있는 이유는 무엇일까? (flux, redux, mobx, recoil 등)***



https://www.npmtrends.com/flux-vs-mobx-vs-redux-vs-reflux

https://stackoverflow.com/questions/32461229/why-use-redux-over-facebook-flux

[![Flux vs Redux](https://i.stack.imgur.com/HbS0b.jpg)](https://i.stack.imgur.com/HbS0b.jpg)

모두다 flux의 철학을 기반으로 하고 있으며,

flux에서의 기능들을 보완하여 출현하게 된 라이브러리이다.

https://lannex.github.io/blog/2020/redux-mobx/

https://woowabros.github.io/experience/2019/01/02/kimcj-react-mobx.html

- MobX

  Mobx는 redux와 비슷한 종류의 State관리 라이브러리이다.

  ![mobx-data-flow-diagram](https://woowabros.github.io/img/2019-01-02/mobx-data-flow.jpg)

  

  데이터 흐름은 위와같이, Componenet가 Store에서 데이터를 요청하고,

  Store는 데이터를 받아오고

  Component에게 전달해주고 렌더링한다는 원리이다.

  

  Mobx는 렌더링할 State를 관찰대상으로 지정하고, State를 변경하면 React Component Render 메서드로 리렌더링되는 것을 기본으로 깔고 간다.

  

  또한, Java Spring Framework와 유사한 Layer 아키텍처를 지니고 있어서, 실제로 그런식으로 Layer를 분리하여 아키텍처를 구성한다.

  ![mobx-spring-layer-table](https://woowabros.github.io/img/2019-01-02/mobx-spring-layer.png)

  

  

  - 특징

    - 객체 지향적이다. (캡슐화)

      ES6에서 추가된 Class를 이름뿐인 Class가 아니고 객체지향적으로 사용하고 개발하는 것을 권장한다.

    - 서버개발자들에게 친숙하다.

      Java Spring Framework와 유사한 아키텍처구조를 지향하고 있어서, 서버개발자들에게 보다 친숙하고 낮은 러닝커브를 제공한다.

    - Decorator

      (java의 어노테이션과 유사하다고 생각하면 됨.)

      Redux에서 React Component와 state를 연결하기 위한 mapStateToProps, mapDispatchToProps, bindActionCreator 등등의 보일러 플레이트가 사라져서 깔끔한 코드가 생성된다.

      Mobx Configuration 설정으로 State를 오직 메서드를 통하여 변경할 수 있도록 Private하게 관리할 수 있다.

    - 여러 개의 store를 가질 수 있다.

    - 불변성을 더이상 신경 쓰지 않아도 된다. 상태로 class로 캡슐화가 잘 되어있기 때문인듯.

    - 함수형 프로그래밍 원칙이 별로 적용되지 않았다. class위주로 구현됨

    - 다른 라이브러리의 필요성이 낮아짐 (redux처럼 비동기 동작 등을 위한 thunk 미들웨어가 불필요하다.)

    - 버전 별로 차이가 심하다. (특정 브라우저를 지원 안하는 버젼도 있다)

    - 레퍼런스가 부족하다.

    - Dev Tool이 별로다.

- Redux
  - 하나의 store를 가진다.
  - store의 데이터는 불변이다
  - 상태를 컴포넌트 구조의 바깥에 두고, 스토어를 중간자로 두고 상태를 업데이트 하거나 새로운 상태를 전달 받을 수 있음.
  - redux를 위한 보일러플레이트가 존재해서 러닝커브가 높은 편임
  - 틀이 정해져 있어서 안정성이 높아질 수 있다.
  - flux 아키텍처를 라이브러리로 구현한 것이 바로 redux이다.
  - dev tool 지원이 잘되어 있다.

- Recoil

  - 사용법은 아래 링크를 통해 참고하자.
    https://deview.kr/data/deview/session/attach/Recoil_왕위를_계승중.pdf
  - atom과 selector가 주 개념임.

  - 장점

    \- React와 굉장히 잘 연계됩니다.
     \- 사용법이 직관적이고 단순합니다.

  - 단점

    \- Hooks를 통해서만 사용할 수 있습니다.
     \- 프로덕션 레벨에서 사용하기엔 아직 약간의 부담이 있습니다. - 현재는 디버깅 도구의 지원이 미미합니다.



요약!

https://deview.kr/data/deview/session/attach/Recoil_왕위를_계승중.pdf

1. Context API등 상태 관리 라이브러리가 존재하지 않던 시절이 있었고,
2. Flux 아키텍처가 등장했고 사람들은 그것을 사용했다.
3. Flux 아키텍처를 라이브러리화한 redux와 mobx가 동시대에 출시되었다.
4. redux가 react 상태관리 시대를 평정하게 되었다.
   (뇌피셜)
   이긴 이유로는 hook의 등장으로 함수 컴포넌트가 class보다 우세하게 되었고
   dev tool을 잘 지원하고 있으며
   레퍼런스가 많고
   틀이 딱딱 정해져있어서 안정성이 높았기 때문으로 생각한다.
5. recoil이 등장했다.
   redux보다 직관적이고 코드의 양도 적어서 각광을 받게됨.
   개발자들은 쉽고 단순한것을 좋아하기 때문
   하지만 나온지 얼마되지 않아서 redux에 몸싸움으로 밀린다. 

