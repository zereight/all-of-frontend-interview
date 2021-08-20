# CSR은 왜 SEO 문제가 발생하는가?

[참고](https://mygumi.tistory.com/385)

일단 SEO 문제가 없는 SSR방식을 살펴보자.

![img](https://blog.kakaocdn.net/dn/ts0Sk/btqUsdyL6lc/65YBOq5UHB4gOkkGp3qLN0/img.png)



SSR으로 구성하게 되면, 매번 새로운 HTML 파일을 응답하여 이를 바탕으로 매번 새로운 페이지를 그린다.



반면에 CSR은

![img](https://blog.kakaocdn.net/dn/b4qu11/btqUtW4mBMJ/8dypbbVycZmWGaaeiRggrk/img.png)

여러개의 페이지로 존재하고 보이더라도, 내부적으로는 1개의 HTML파일이다.

클라이언트가 서버에 Ajax요청을 통해서 데이터를 받아와서 렌더링을 하기 때문에, 크롤러 입장에서는 root 페이지의 html 정보만을 수집하게 되기 때문이다.

모든 페이지가 하나의 HTML 파일 정보만을 바라보고 있기 때문에, 검색서비스 노출 및 SNS 공유 기능등이 원하는 대로 동작할 수 없다.



그런데 구글 검색엔진은 스크립트를 실행하고 비동기 요청에 의한 처리까지 분석할 수 있어서 CSR 사이트도 SEO가 가능하다. 갓ㅡ글
(https://hyunseob.github.io/2019/05/26/google-io-2019-day-3/)

