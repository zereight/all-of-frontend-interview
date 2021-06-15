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



