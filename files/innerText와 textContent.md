# innerText와 textContent의 차이점

보통 element의 텍스트를 읽거나 수정할시에는 innerText와 textContent를 사용한다.

둘다 텍스트를 추가할 수 있고, 텍스트 값을 반환한다는 공통점이 있기 때문이다.

그럼 차이점은 무엇인가?

- `textContent`가 `innerText`보다 먼저 나와서 IE와 호환이 잘됩니다.

- `textContent`는 `innerText`가 사용자에게 보이는 값 위주로 반환하는 것과 달리, 가지고 있는 텍스트값을 그대로 반환합니다. html코드에서 아무리 엔터를 많이해도 엔터는 1번 적용된것처럼 나타나는데, `textContent`는 그 엔터가 모두 반영되어서 출력되고, `innerText`는 엔터가 1번만 적용된것처럼 반환되는 것입니다.

즉, `display:none`이 적용된 요소가 있다면, `textContent`는 그것을 반환하고 `innerText`는 사람이 읽을 수 있는 부분만 반환하기 때문에 해당 부분을 출력하지 않습니다.

이 말 또한, `textContent`는 style을 포함한 모든 요소를 그냥 반환하고, `innerText`는 보여줘야할, 또는 보여주지 말아야할 CSS를 한번 더 고려하기 때문에 "최신 계산값을 반영하기 위해" 리플로우를 발생시킨다고 [MDN](https://developer.mozilla.org/ko/docs/Web/API/Node/textContent)에 나와 있습니다.

- 가장 중요한 문제가 있는데, div태그에 contenteditable을 사용하여 텍스트를 입력할 시, `innerText`는 &gt와 같은 html 문자가 잔존하게 된다. 이는 Chrome에서는 문제가 없으나, safari나 firefox에서 나타나는 일종의 버그이다. 그렇기 때문에 왠만하면 `innerText`보단 `textContent`를 사용하는 것이 성능면이나 버그안정성 및 호환성 면에서 나을 것이다.

[내가 경험한 버그](https://github.com/woowacourse-teams/2021-darass/issues/522)
