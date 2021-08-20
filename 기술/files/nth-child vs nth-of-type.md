nth-child과 nth-of-type이 있고,

first-child와 first-of-type이 있고,

last-child와 last-of-type이 있다.

비교를 해보면,

nth-child(n)

: 부모 엘리먼트의 모든 자식 엘리먼트중 n번째

nth-of-type(n)

: 부모 엘리먼트의 특정 자식 엘리먼트 중 n번째

즉, span:nth-child(2)를 하면 모든 자식에서의 2번째 자식이다.

태그가 아무 상관이 없는 것이다.

하지만 span:nth-of-type(2)를 하면 자식들 중에 span인 녀석들 중 2번쨰인것이다.

즉, 특정 태그를 지정할 수 있다.

그래서 좀더 구체적으로 대상을 특정할 수 있는 nth-of-type을 권장하는 것 같다.

nth-child는 DOM 구조의 변화에 영향을 많이 받기도 할것이다. (nth-of-type에 비해서 상대적으로)

참고. https://firerope.tistory.com/5
