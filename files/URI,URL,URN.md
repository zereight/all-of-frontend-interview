# URI vs URL vs URN

![img](https://media.vlpt.us/images/jch9537/post/51dcc312-8ecb-4048-80df-cbde40865e7a/image.png)



## URI

> 정의

Uniform Resource Identifiler

통합 자원 식별자



인터넷에 있는 자원을 나타내는 유일한 주소이다.

URI의 존재는 인터넷에서 요구되는 기본조건으로서 인터넷 프로토콜에 항상 붙어다닌다.



URI 하위개념으로 URL, URN 등이 있다.



## URL

Uniform Resource Locator

네트워크 상에서 사원이 어디있는지를 알려주기 위한 규약이다.

즉, 컴퓨터 네트워크와 검색 매커니즘에서의 위치를 지정하는, 웹 리소스에 대한 참조이다.

흔히 웹 사이트 주소로 알고 있지만, URL은 웹 사이트 주소뿐만 아니라, 컴퓨터 네트워크상의 자원을 모두 나타낼 수 있다.

그 주소에 접속하려면 URL에 맞는 프로토콜을 알야야 하고, 그와 동일한 프로토콜로 접속해야 한다.





## URN

Uniform Resource Name

통합 자원 이름





> 예시

![img](https://media.vlpt.us/images/jch9537/post/88b0c8ac-5870-4cbc-b613-7dd39f510f31/image.png)



http://opentutorials.org:3000/main?id=HTML&page=12

이라는 주소가 있다고 가정해보자.

`http://opentutorials.org:3000/main` 여기까지는 URL, URI이다.

`http://opentutorials.org:3000/main?id=HTML&page=12` 이것은 URI라고 할 수 있으며, URL은 아니다.

위 차이를 알겠는가?



URL은 자원의 위치를 나타내 주는 것이고,

URI는 자원의 식별자인데 `?id=HTML&page=12` 이 부분은 위치를 나타내는 것이 아니라 id값이 HTML이고 page가 12인 것을 나타내주는 식별자이기 때문이다.



