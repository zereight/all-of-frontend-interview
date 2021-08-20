# 왜 React render가 2번이나 되는 걸까? (feat. React.StrictMode는 무엇일까?)



가끔씩 `console.log` 를 통해 값을 출력해보는데, 2번씩 값이 호출되는 경우가 있을 것이다.

이는 `React.StrictMode`때문이다.



[공식문서](https://ko.reactjs.org/docs/strict-mode.html)



StrictMode는 어플리케이션 내의 잠재적인 문제를 알아내기 위한 도구이다.

Fragment와 같이 UI를 렌더링 하지는 않고, 부가적인 검사와 경고를 활성화 한다.



참고로, **Strict mode는 개발 모드에서만 활성화되기 때문에, 프로덕션 코드에서는 영향을 주지 않는다.**



보통 CRA로 생성하면 App위에 생겨있는데, 꼭 여기 있을 필요는 없고, 자손컴포넌트 어디서든 삽입할 수 있다.



> Strict mode를 하면 다음과 같은 문제들을 찾아낼 수 있습니다.

- 안전하지 않은 생명주기를 사용하는 컴포넌트 발견
- 레거시인 "문자열 ref" 사용에 대한 경고
- 권장되지 않는 findDOMNode 사용에 대한 경고 (DOM노드에 ref를 바로 지정하는 메서드)
- 예상치 못한 부작용 검사
- 레거시 context API 검사 (레거시 아니면 괜찮)

