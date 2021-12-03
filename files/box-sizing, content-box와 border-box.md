## box-sizing에서 content-box, border-box 차이점은 무엇인가?

box-sizing 속성은 CSS의 테두리 영역 크기를 결정한다.

- content-box: css width와 height를 컨텐츠 영역에만 적용한다.
  border, padding, margin은 따로 계산되어서 전체 영역이 설정값보다 커질 수 있다.

- border-box: css width와 height를 전체 영역에 적용한다.
  border, padding, margin을 모두 합산하기 때문에 컨텐츠 영역이 설정값보다 적어질 수 있다.

즉, 컨텐츠의 크기 = 전체크기 - border - padding - margin 이다.

- 참고
  https://dasima.xyz/css-box-sizing-content-box-vs-border-box/
