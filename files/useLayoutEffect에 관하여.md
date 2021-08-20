<div style="text-align:center">
<img src="https://raw.githubusercontent.com/donavon/hook-flow/master/hook-flow.png" />
</div>

https://github.com/donavon/hook-flow/blob/master/hook-flow.pdf

위 그림은 리액트의 훅을 표시한것이다.

## 마운트 단계

마운트 단계에서는 Lazy Initializer가 동작한다.
이것은 useState( () => 1); 처럼 useState의 인자로 콜백함수를 넘겨서 초기화하는 것을 뜻한다.
이렇게하면 useState(1)가 함수 호출시 매번 초기화되는 것과 달리, 마운트 시점에 딱 1번만 초기화할 수 있다.

## 업데이트 단계

업데이트라 함은 당연히 상태값에 따른 Render가 수행될것이다.
근데, 이는 아마 Virtual DOM의 Render일 것이다.

실제 DOM의 렌더는 `Browser paints screen` 단계에서 일어난다.

## 2개의 Effect

근데 그림에서 Virtual DOM이 업데이트 되고 난 후에, 2개의 Effect를 찾아볼 수 있다.

1개는 `Browser paints screen` 이전에 동작하고,
나머지 하나는 `Browser paints screen` 이후에 동작한다.

전자를 `useLayoutEffect`로 호출할 수 있고,
후자를 `useEffect`로 호출할 수 있다.

즉, `Browser paints screen` 이전에 동작시킬 Effect는 `useLayoutEffect`에 넣고
아니면 널리 사용되는 `useEffect`에 넣어서 사용하면 된다.
