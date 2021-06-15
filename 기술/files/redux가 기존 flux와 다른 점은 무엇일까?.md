## ***redux가 기존 flux와 다른 점은 무엇일까?***

https://taegon.kim/archives/5288

페이스북은 Flux 아키텍처를 발표한 후에 Flux에 대한 구현체도 공개했는데,

그 때에는 dispatcher만 구현되어 있어서 Flux 프레임워크라고 부르기엔 다소 무리가 있었다.

그 때 많은 구현체들이 나타났는데 그것이 바로 redux이다.

Redux는 다른 구현체와 비교해서 사용법이 단순하고, ES2015도 잘 지원하고, 용량도 2kb로 상당히 작은 편이다. Flux를 만든 개발자들도 칭찬을 할 정도로 Flux원칙을 충실히 지켰다고 한다.

원래 페이스북이 고안한 Flux에서는 Action Creator가 dispatcher를 호출하는 작업도 했으나, 만에 하나라도 있을 수 있는 부작용을 없애기 위해서 action만 만드는 역할만 담당하도록 redux에서 개선되었다.

Redux는 dispatcher를 명시적으로 생성하지 않고도 Flux를 구현할 수 있도록 작성되어서, dispatcher를 생략할 수 있다. (store의 dispathcer를 사용하면 됨)

Redux는 Flux에는 없는 개념인 Reducer를 고안했다.
Action은 어떤일이 일어났는지 알려주지만, 어플의 상태를 어떻게 바꾸어야 할지는 알려주지 않는다. Redux 프레임워크에서는 Reducer가 이 역할을 담당한다.
=> flux의 store객체를 업데이트하는 콜백함수와 역할이 비슷

