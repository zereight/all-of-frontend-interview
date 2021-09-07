# React에서 $$typeof 심볼은 무엇인가?



react element를 console.log로 찍어보면 `$$typeof` 라는 심볼이 있는것을 한번쯤은 보았을 것이다.

보통 아래와 같은 객체로 찍힌다.

```jsx
{ 
  type: 'div', 
  props: { bgcolor: '#ffa7c4', children: 'hi', }, 
  key: null, 
  ref: null,
  $$typeof: Symbol.for('react.element'), 
}
```



jsx로 문법을 작성하게 되면, React에서는 `React.createElement(type, props, children)` 라는 메서드를 이용하여 변환되게 되는데,

이 `React.createElement` 함수가 `$$typeof` 프로퍼티를 추가해준다.



그 이유는 XSS 공격을 막기위해 `React` 에서 조치를 취한것이다.

물론, React자체가 특정 문자들을 escaping 해주어서 XSS에 완전히 취약하지는 않지만

`$$typeof`는 최악의 상황을 대비해서 생겼다고 할 수 있다.



최악의 상황이라하면 서버가 잠시 해킹당했을때를 예로 들 수 있겠다.

보통 데이터를 불러올때, 서버에서 불러온 데이터를 그대로 프론트엔드에서 그대로 렌더링한다.

서버가 해킹을 당해서 프론트엔드 단에 JSON형태로 응답을 내려준다고 생각해보자.

```jsx
{ 
  type: 'div', 
	props: { dangerouslySetInnerHTML: { __html: "악의적으로 삽입된 스크립트"; }, }, 
  key: null, 
  ref: null,
}
```

React입장에서는 해당 JSON을 `React.createElement`에 넣어서 렌더링하려고 할 것이다.



그래서 리액트는 꼼수를 부린것이다.

`JSON.stringify` 함수를 써본적이 있다면, 여기에 Date나 Symbol형의 프로퍼티를 넣었을때 undefined가 나오는 것을 알 수 있다.

그래서 `React.createElement` 는 일부러 Symbol타입의 프로퍼티를 넣어서, 서버로부터 악의적인 JSON이 날아오는 경우에 undefined로 만들어서 렌더링을 거부해버린다.