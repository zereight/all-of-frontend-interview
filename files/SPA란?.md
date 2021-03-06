## SPA란?

Single Page Application의 약자이다.

말 그대로 페이지가 1개인 어플리케이션이다.

전통적인 어플리케이션 구조는 유저가 요청할 때 마다 페이지가 새로고침되며, 페이지를 로딩 할 때 마다, 서버로부터 리소스를 전달받아 해석 후 렌더링을 합니다. HTML 파일, 혹은 템플릿 엔진 등을 사용해서 어플리케이션의 View가 어떻게 보여질지도 서버에서 담당했었습니다.

요즘 시대에는 웹에서 제공되는 정보가 정말 많아서 속도적인 측면에서 문제가 있었고, 
이를 해소하기 위해서 캐싱과 압축을 해서 서비스가 제공되었다.

렌더링하는 것을 서버쪽에서 담당한다는 것은, 그 만큼 렌더링을 위한 서버 자원이 사용되는 것이고, 불필요한 트래픽도 낭비됨을 의미한다.

그래서 React같은 라이브러리 혹은 프레임워크를 사용해서 뷰 렌더링을 유저의 브라우저가 담당하도록 하고, 어플을 브라우저에 로드한 다음에 정말 필요한 데이터만 전달받아서 보여준다.



싱글 페이지라고 해서, 한 종류의 화면만 있는 것도 아니다.
블로그 같은 경우에는 홈, 포스트, 목록, 글쓰기 등의 화면이 있을 것이다.
그리고 그 화면에 대한 주소도 있어야 한다.
주소가 있어야 유저들이 북마크도 할 수 있고 서비스를 사용자들에게 광고할 수 있다.

여기서, 다른 주소에 따라 다른 뷰를 보여주는 것을 라우팅이라고 한다!

리액트 자체에는 이 기능이 내장되어 있지 않기 때문에, 직접 브라우저의 API를 사용하고 상태를 설정해서 다른 뷰를 보여주어야 한다.



그럼 단점은?

앱의 규모가 커지면, js파일 사이즈가 너무 커진다는 것에 있다.
유저가 실제로 방문하지 않을 수도 있는 페이지의 렌더링 스크립트도 불러오기 때문이다.
(그래서 code splitting을 사용한다.)

SEO 문제가 있다.
