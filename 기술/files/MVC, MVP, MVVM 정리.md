## *MVC, MVP, MVVM 비교*

모두 1가지의 철학에서 파생되었다. 

https://beomy.tistory.com/43

"각각의 역할을 나누어 코드를 관리함으로써 유지보수와 개발 효율을 높이자"

- MVC
  MVC 패턴은 Modal, View, Controller를 합친 용어이다.

  - 구조
    ![MVC](https://blog.kakaocdn.net/dn/7IE8f/btqBRvw9sFF/AGLRdsOLuvNZ9okmGOlkx1/img.png)

  Model: 어플리케이션에서 사용되는 데이터와 그 데이터를 처리하는 부분

  View: 사용자에게 보여지는 UI 부분

  Controller: 사용자의 입력을 받고 처리하는 부분


  - 동작
    1. 사용자의 Action이 Contoller에 들어온다.
    2. Controller에서는 사용자의 Action를 확인하고 Model을 업데이트 한다.
    3. Controller에서 Model을 나타내줄 View를 선택한다.
    4. View는 Model을 이용하여 화면을 나타낸다.
       
  - View는 어떻게 업데이트 되는가?
    - VIew가 Model을 이용하여 직접 업데이트 하기
    - Model에서 View에게 Notify해서 업데이트 하기
    - View가 Polling으로 주기적으로 Model의 변경을 감지하여 업데이트 하기
      
  - 특징

    - Controller는 여러개의 view를 선택할 수 있는 1:n 구조이다.
    - Controller는 view를 선택할 뿐, 직접 업데이트 하진 않습니다. 
    - view는 Controller를 알지 못합니다.
      
  - 장점

    - 가장 단순한 패턴이다.
    - 보편적으로 사용되는 디자인 패턴이다.
      
  - 단점

    - View와 Model 사이의 의존성이 높다.
    - View, Model의 높은 의존성은 어플리케이션이 커질수록 복잡해지고 유지보수가 어렵게 된다.



- MVP

  MVP 패턴은 Model + View + Presenter 를 합친 용어이다.

  Model과 View는 MVC 패턴과 동일하고, Controller 대신 Presenter가 존재한다.

  - 구조

    - ![MVP](https://blog.kakaocdn.net/dn/clZlsT/btqBTLzeUCL/IDA8Ga6Yarndgr88g9Nkhk/img.png)
    - Model: 어플리케이션에서 사용되는 데이터와 그 데이터를 처리하는 부분이다.
    - View: 사용자에게 보여지는 UI
    - Presenter: View에서 요청한 정보로 Model을 가공하여 View에 전달해 주는 부분이다.
      View와 Model을 붙여주는 접착제 역할을 한다.

  - 동작

    1. 사용자의 Action이 View를 통해 들어온다.
    2. View는 데이터를 Presenter에 요청한다.
    3. Presenter는 Model에게 데이터를 요청한다.
    4. Model은 Presenter로부터 받은 요청에 대해 데이터로 응답한다.
    5. Presenter는 View에게 데이터를 다시 전달한다.
    6. View는 Presenter가 응답한 데이터를 이용해서 화면에 그린다.
       

  - 특징

    Presenter는 View와 Model의 인스턴스를 가지고 있고, 둘을 연결하는 접착제 역할을 한다.

    Presenter와 View는 1:1 관계로 존재한다.
    

  - 장점

    MVP 패턴의 장점은 View와 Model의 의존성이 없다는 것이다.
    MVP 패턴은 MVC 패턴의 단점이었던 View, Model의 의존성을 해결했다. 

    Presenter를 통해서만 데이터를 전달받기 때문에!
    

  - 단점

    View, Model의 의존성은 해결되었지만, View와 Presenter사이의 의존성이 커졌다.

    결국, 어플리케이션이 복잡해질수록 View, Presenter 사이의 의존성이 강해진다는 단점이 생긴다.

  

  

- MVVM

  MVVM 패턴은 Model, View, View Model을 합친 용어이다

  (Model과 View는 다른 패턴과 동일하다.)

  - 구조
    ![MVVM](https://blog.kakaocdn.net/dn/CiXz0/btqBQ1iMiVT/staXr7UO95opKgXEU01EY0/img.png)

    Model: 어플리케이션에서 사용되는 데이터와 그 데이터를 처리하는 부분

    VIew: 사용자에게서 보여지는 UI부분

    View Model: View를 표현하기 위해 만든 View를 위한 Model이다. View를 나타내주기 위한 Model이자 View를 나타내기 위한 데이터 처리를 하는 부분인 것이다.
    

  - 동작

    1. 사용자의 Action이 View를 통해 들어온다.
    2. View에 Action이 들어오면 View Model에 Action을 전달한다.
    3. View Model은 Model에게 데이터를 요청한다.
    4. Model은 View Model에게 요청받은 데이터를 응답한다.
    5. View Model은 응답 받은 데이터를 가공하여 저장한다.
    6. View는 View Model과 Data Binding하여 화면을 나타낸다.
       

  - 특징

    MVVM 패턴은 Command 패턴과 Data Binding 이 2가지 패턴을 구현되었다.

    Command 패턴, Data Binding을 이용하여 View, View Model사이의 의존성을 없앤것이다.

    그래서 View Model과 View는 1:n 관계이다.

    

  - 장점

    MVVM 패턴은 View와 Model 사이의 의존성이 없다.

    또한 Command 패턴과 Data binding을 이용하여 View, View model 사이의 의존성 또한 없앤 디자인 패턴이라서, 각각의 부분이 독립적이기 때문에 모듈화 하여 개발할 수 있다.

    

  - 단점
    MVVM패턴의 단점은 View Model의 설계가 쉽지 않다는 것이다.

    

  

  

  

  ​	