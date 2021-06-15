## ***Flux는 MVC의 어떤 문제를 해결했을까?***

<del>글이 다 날아 갔다.</del>

https://beomy.tistory.com/44

- MVC의 문제점
  ![Facebook에서 이야기 하는 MVC의 단점](https://blog.kakaocdn.net/dn/ALrHe/btqBTMSuHfN/ZlW9i9ET34e90APgCRChk1/img.png)

  페이스북에서는 MVC의 가장 큰 단점이 양방향 데이터 흐름이라고 표현하고 있습니다.

  위 MVC 패턴에서 Controller는 Model의 데이터를 조회하거나 업데이트 하는 역할을 수행하는데, Model이 업데이트 되면 View는 그것을 화면에 반영합니다.

  View는 Model도 업데이트 할 수도 있으며, Model이 업데이트 되어 View가 따라서 업데이트 되고, 업데이트 된 View가 다시 다른 Model을 업데이트 한다면 다시 View의 업데이트가 나타나고 ....

  이런 양방향 데이터 흐름은 새로운 기능이 추가되거나할 때에, 시스템 복잡도가 기하급수적으로 증가시킬 수 있고, 예측 불가능한 코드를 만들게 됩니다.



- Flux는 어떻게 해결했을까
  Flux는 양방향 데이터 흐름을 해결하기 위해서 단방향 데이터 흐름으로 설계되었습니다.

  ![Flux](https://blog.kakaocdn.net/dn/lmfPW/btqBQnTPgIs/Z1jmHHdNcOTNiu93kQ9gMk/img.png)

  데이터 흐름은 위와 같이, Dispatcher에서 Store로, Store에서 View로, View는 Action을 통해서 다시 Dispatcher로 데이터가 흐르게 된다.

  이런 단방향 데이터 흐름을 취함으로써 데이터 변화를 훨씬 예측하기 쉽게 만들 수 있습니다

  

- Flux의 구성요소

  1. DIspatcher

     Dispatcher는 모든 Flux 데이터 흐름을 관리하는 허브역할을 하고, 1개의 인스턴스만 존재합니다.

     Action이 발생되면 Dispatcher로 전달되고, 전달된 Action을 보고, 전달된 콜백함수를 실행하여 Store에 데이터를 전달합니다.

  2. Store

     어플리케이션의 모든 상태 변경은 Store에 의해 결정이 됩니다.
     Dispatcher로 부터 메시지를 수신 받기 위해서는 Dispatcher에 콜백함수를 등록해야 합니다. (listen)

     Store가 변경되면 View에 변경되었다는 사실을 알려주기 위함입니다.

     또한, Store는 싱글톤으로 관리됩니다.

  3. View

     VIew는 화면에 나타내는 것 뿐만 아니라, 자식 View로 데이터를 흘러보내주는 view-controller 역할도 함께 합니다.

  4. Action

     Dispatcher에서 콜백함수가 실행되면 Store가 업데이트 되게 되는데, 이 콜백 함수를 실행 할 때, 데이터가 담겨있는 객체가 인자로 전달된다. 

     그 객체 인자가 바로 Action이다.

