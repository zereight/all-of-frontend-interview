## CORS

Cross Origin Resource Sharing
교차 출처 리소스 공유

추가적인 Http 헤더를 사용하여, 한 출처에서 실행 중인 웹 어플리케이션이 다른 출처의 선택한 자원에 접근할 수 있는 권한을 부여하도록 브라우저에 알려주는 방법이다.

> 왜 권한이 설정되어야 하는가?

보안상의 이유로 제한되어야 한다.

> 언제 실행되는가?

리소스가 자신의 출처와 다를 때 교차 출처 HTTP 요청을 실행한다.



> 종류

1. Simple Request
   1. 기본적으로 웹은 다른 출처의 리소스를 요청할 때에는 HTTP 프로토콜을 사용하여 요청을 하는데, 이 때 브라우저는 요청 헤더를 Origin 필드에 요청을 보내는 출처를 담아서 전송한다.
   2. 서버는 요청에 대한 응답을 하는데, 응다 헤더에 Access-Control-Allow-Origin 이라는 값에 '이 리소스를 접근핳는 것이 허용된 출처'를 내려준다.
      이후 응답을 받은 브라우저는 자신이 보냈던 요청의 Origin과 서버가 보내준 응답의 Access-Control-Allow-Origin을 비교해서 이 응답이 유효한 응답인지 아닌지를 결정한다.

   

   동작 조건

   1. 요청의 메서드는 GET, HEAD, POST 중 하나여야 한다.
   2. `Accept`, `Accept-Language`, `Content-Language`, `Content-Type`, `DPR`, `Downlink`, `Save-Data`, `Viewport-Width`, `Width` 외의 헤더를 사용하면 안된다.
   3. 만약 `Content-Type`을 사용하는 경우에는 `application/x-www-form-urlencoded`, `mutipart/form-data`, `text/plain` 만 허용된다.


   1,2번 조건은 뭐 문나하게 기본적으로 만날 수 있는 경우들이다.
   하지만 3번은 오늘날 요청에서는 `text/xml`이나 `application/json` 타입을 가지도록 설계되기 떄문에 조건을 충족시키기 쉽지 않다.



2. Preflight Request

   요청을 한번에 보내는 것이 아니라, 예비 요청과 본 요청으로 나누어서 서버로 전송하는 방식이다.

   본 요청을 보내기 전에 미리 예비로 보내는 요청을 Preflight라고 하고, http 메서드에 `OPTIONS`메서드를 사용한다.

   

   왜 예비요청을 보내는가?

   👉 예비 요청을 함으로써 본 요청을 보내기 전 브라우저 스스로가 요청을 보내느 것에 대한 안전성을 확보하기 위한 목적.

   서버는 이 예비 요청에 대한 응답으로, 현재 자신이 어떤 것들을 허용하고, 어떤 것들을 금지하고 있는지에 대한 정보를 응답 헤더에 담아서 브라우저에게 다시 보내준다.

   + 단순히 Origins에 대한 정보 뿐만 아니라, 나중에 보낼 수 있는 본 요청에 대한 다른 정보들도 보낸다함.

   

3. Credentialed Request

   credentials 옵션을 사용하여, 인증정보를 담아서 보내는 방식

   좀더 보안을 강화하고 싶을 때 사용한다!

   

   credentials는 다음과 같은 3가지 옵션을 가진다.

   	1. `smae-origin`: 같은 출처 간 요청에만 인증 정보를 담을 수 있다.
    	2. `include`: 모든 요청에 인증 정보를 담을 수 있다.
    	3. `omit`: 모든 요청에 인증 정보를 담지 않는다.

   

   이 방법을 사용하면 

   - `Access-Control-Allow-Origin: *` 이면 안되고, 구체적인 URL을 명시해야함
   - `Access-Control-Allow-Credentials: true` 로 설정되어 있어야함



CORS를 해결할 수 있는 방법은 [여기](https://evan-moon.github.io/2020/05/21/about-cors/#credentialed-request)를 참고하세요.