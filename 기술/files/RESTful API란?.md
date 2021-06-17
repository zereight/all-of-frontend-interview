# REST란?

[출처](https://gmlwjd9405.github.io/2018/09/21/rest-and-restful.html)



> Representational State Transfer

자원을 이름으로 구분하여 해당 자원의 상태를 주고 받는 모든 것을 의미한다.



즉, 자원의 표현에 의한 상태전달을 하는 통신 방식을 일컫는다.



구체적으로 말하자면, 
HTTP URI를 통해서 자원을 명시하고, HTTP 방식(GET, POST, PUT, DELETE) 를 통해서 해당 자원에 대한 CRUD 작업을 적용하는 것이다.



> 장점

- HTTP 프로토콜의 인프라를 그대로 사용해서, REST API 사용을 위한 별도의 인프라를 구축할 필요가 없다.
- HTTP 프로토콜의 표준을 따르는 모든 플랫폼에서 사용가능하다.
- 서버와 클라이언트의 역할을 명확하게 분리한다.

> 단점

- 사용할 수 있는 메서드가 4가지 밖에 없다. 
- 구형 브라우저가 아직 제대로 지원해주지 못하는 부분이 있다. (PUT, DELETE 등)



> 필요성

- 어플리케이션의 분리와 통합
- 최근의 서버 프로그램은 다양한 브라우저와 기기 등에서 통신을 할 수 있어야 한다.



> 특징

- 서버-클라이언트 구조
- 무상태 (http니까)
- 캐시처리가능 (http라서)
- 계층화
- 인터페이스 일관성



# REST API란?

Representational State Transfer API



API (Application Programming Interface)란

- 데이터와 기능의 집합을 제공하여 프로그램간 상호작용을 촉진하며, 서로 정보를 교환가능하도록 하는 것.



REST API란

- REST 기반으로 서비스 API를 구현한 것



설계 규칙

- URI는 정보의 자원을 표현해야 한다.
- 자원에 대한 행위는 Http 메서드로 표현한다.
  - URI에 Http 메서드가 들어가면 안된다.
  - URI에 행위에 대한 동사 표현이 들어가면 안된다. (CRUD기능 이름이 포함되면 안됨)
- `/`는 계층 관계를 나타내는데 사용한다.
- URI 마지막 문자로 ``/`` 를 포함하지 않는다.
- `-`는 URI의 가독성을 높이는데 사용한다.
- `_`는 URI에 사용하지 않는다.
  - 밑줄은 보기 어렵거나 문자가 가려지기도해서 가독성이 떨어진다고 한다.
- URI 경로에는 소문자가 적합하다.
- 파일 확장자는 URI에 포함하지 않는다.
  - Accept header를 사용하여 처리한다.

예시

![img](https://gmlwjd9405.github.io/images/network/restapi-example.png)



# RESTful이란?

REST라는 아키텍처를 구현하는 웹 서비스를 나타내기 위해서 사용되는 용어.

"REST 답게" 라는 뜻 
혹은
REST API를 제공하는 웹서비스

*RESTful하지 못한경우*

- CRUD 기능을 모두 POST로만 처리하는 API
- route에 자원, id 외의 정보가 들어가는 경우