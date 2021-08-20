## 정의

CSRF는 Cross Site Request Forgery의 약자이다.

사용자가 자신의 의지와는 무관하게 공격자가 의도한 행위를 특정 웹사이트에 요청하게 하는 공격을 뜻한다.

이는 쿠키를 사용하면 보안에 강하다라는 주장을 무색하게 할 정도로 쿠키를 이용해서 쉽게 취약점 공격이 가능하다.

원래는 XSS 공격이 사용자가 특정 웹사이트를 신용하는 점을 노린것이라면, 사이트간 요청 위조는 특정 웹사이트가 사용자의 웹 브라우저를 신용하는 상태를 노린것이다.

일단 사용자가 웹 사이트에 로그인한 상태에서 사이트간 요청 위조 공격 코드가 삽입된 페이지를 열면, 공격 대상이 되는 웹사이트는 위조된 공격 명령이 믿을 수 있는 사용자로부터 발송된 것으로 판단하게 되어서 공격에 노출된다.

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile8.uf.tistory.com%2Fimage%2F9956434D5B7038E70B894D"/>

## 방법

공격 방법은 다음과 같다.

1. 공격자는 게시판에 관리자가 관심을 가질 수 있는 제목으로 CSRF 스크립트가 포함된 게시물을 등록한다.
2. 관리자는 확인이 필요한 게시물로 파악하여 CSRF 스크립트가 포함된 게시물을 확인한다.
3. 게시물을 읽은 관리자는 CSRF 스크립트가 포함된 것을 알지 못한 채, 게시물을 확인한다.
   하지만, 관리자의 권한으로 공격자가 원하는 CSRF 스크립트 요청이 발생한다.
4. 공격자가 원하는 CSRF 스크립트 결과가 발생하여, 관리자 및 사용자의 피해가 발생한다.

## 예시

예시는 다음과 같다.

1. img태그를 이용한 방법
   사용자는 아래와같은 html이 포함된 악의적인 사이트/이메일을 열람할 시 자신도 모르게 요청을 보내게 할 수 있다.

```html
<img src="https://mysite.com/user?action=set-pw&pw=1234" width="0" height="0" />
```

2. form을 이용한 방법
   사용자는 아래와 같은 form이 포함된 악의적인 사이트를 열람할 시, 자동으로 페이스북에 광고성 글을 작성하게 할 수 있다.

```html
<form action="http://facebook.com/api/content" method="post">
  <input type="hidden" name="body" value="여기 가입하면 돈 10만원 드립니다." />
  <input type="submit" value="Click Me" />
</form>
<script>
  document.forms[0].submit();
</script>
```

2-1. form을 이용한 방법
사용자는 아래와 같은 form이 포함된 악의적인 사이트를 열람할 시, 자동으로 해커 계정으로 로그인하는 요청을 보내게 된다.

```html
<form method="POST" action="http://honest.site/login">
  <input type="text" name="user" value="h4ck3r" />
  <input type="password" name="pass" value="passw0rd" />
</form>
<script>
  document.forms[0].submit();
</script>
```

## 방어

1. CORS
   CORS를 이용해서 사이트 간 요청을 불가능하게 만든다.

2. referer 헤더 설정
   요청을 한 페이지의 정보가 담긴 referer 헤더 속성을 검증하여 차단하는 방법

3. csrf token
   핸덤한 값을 사용자의 세션에 저장하여 사용자의 모든 요청에 대해서 서버 쪽에서 검증하는 방법
   요청을 받을 때마다, 세션에 저장된 토큰값과 요청 파라미터에서 전달되는 토큰값이 같은지 검증한다.

4. double submit cookie
   웹 브라우저읜 Same Origin 정책으로 인해서, 자바스크립트에서 타 도메인의 쿠기 값을 확인/수정하지 못한다는 것을 이용한다.

   스크립트 단에서 요청 시 난수 값을 생서앟여 쿠키에 저장하고 동일한 난수 값을 요청 파라미터에도 저장하여 서버에 전송한다.
   서버단에서는 쿠키의 토큰값과 파라미터의 토큰값이 일치하는지만 검사하면 된다.

5. 일단은 XSS를 막자.
   XSS를 막지 못한다면 위 방법으로 CSRF를 방어할 수 있다고 장담할 수 없다.

https://swk3169.tistory.com/24
https://velog.io/@shroad1802/CSRF
