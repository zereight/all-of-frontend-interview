# 쿠키 SameSite



2020, 02월 내가 쿠키가 뭔지도 몰랐던 시절.

Chrome 브라우저는 쿠키의 SameSite=Lax를 default로 변경했다.



SameSite 정책은 크게 3가지가 있다. (None, Lax, Strict)

- SameSite=None

None은 2020,01까지 사용되던 Default 정책으로 SameSite를 검증하지 않는다. 그래서 A사이트에서 B사이트로 요청을 전송하게 되면, 쿠키를 그냥 전송해버린다.

이제는 None을 하려면 Secure라고 명시해주어야 한다.

- SameSte=Strict

Strict는 쿠키의 SameSite 검사를 강하게 제한하는 정책이다.

소스 도메인과 대상 도메인이 일치해야 쿠키를 포함해서 전송한다.

대상은 요청할 수 있는 모든것이다.

- SameSite=Lax

Lax는 기존 Strict 정책에서 예외처리가 포함된 정책이라고 할 수 있다.

get을 사용하는 `<a href>` 와 `<form method=get>` 을 제외하고는 나머지는 모두 Strict처럼 SameSite가 아니면 쿠키가 차단된다.



https://www.hahwul.com/2020/01/18/samesite-lax/

