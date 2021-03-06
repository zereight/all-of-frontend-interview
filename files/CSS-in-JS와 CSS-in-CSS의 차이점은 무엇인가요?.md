> CSS-in-JS와 CSS-in-CSS의 차이점은 무엇인가요?



1. CSS-in-JS

CSS-in-JS는 자바스크립트로 CSS 요소들을 관리하는 것으로 styled-component같은 것들이 대표적인 라이브러리 입니다.

자바스크립트로 CSS를 관리하므로, 스타일 요소들을 선언적으로 표현할 수 있게 되고, 컴포넌트 단위로 스타일을 고려할 수 있어서 스타일의 유지보수 및 관리가 쉬워집니다.

또한, webpack의 트리 셰이킹을 통해서 사용하지 않는 스타일 코드들이 제거되어질 수 있어서 성능의 향상을 가져옵니다.

또한, css자체로 테스팅을 할 수 있게 된다는 장점이 있습니다.



하지만, 원래는 브라우저를 렌더링할때, 스타일요소와 스크립트가 병렬적으로 행해졌는데, 이제는 모든 스타일 코드가 스크립트 안에 들어가 있으므로, 스크립트가 방대해지고 스타일이 적용되지 않은 html뼈대인 FOUC(flash of unstyled content)가 나타나서 좋지 않은 사용자 경험을 줄 수 있습니다.



2. CSS-in-CSS

일반적인 CSS사용법으로, CSS-in-CSS와 반대로 브라우저 렌더링 과정에서 스크립트랑 병렬적으로 다운로드 및 트리에 적용이되고, FOUC가 발생하지 않습니다.

하지만 일반적으로 사용하지 않는 스타일 시트까지 로드되어질 수 있고, 스타일 수정을 위해서는 자바스크립트 영역을 벗어나서 스타일시트 파일에서 찾아서 수정해야 한다는 단점이 있습니다.