아래 아티클을 참고했다.

https://yhancsx.github.io/js/tree-shaking/

Javascript Tree Shaking

front-end 최적화 방안 중 하나인 tree shaking에 대해 공부해 보자.

yhancsx.github.io

https://blog.neufund.org/why-we-have-banned-default-exports-and-you-should-do-the-same-d51fdc2cf2ad

Why we have banned default exports in Javascript and you should do the same

ES2015 was the most important improvement to Javascript in years. Among many great features it brought brand new module system — Ecma…

blog.neufund.org

1. export default

- 하나의 파일에서 하나의 변수를 export한다.

- import할 때 아무 이름으로나 import 가능하다.

- let, const같은 것을 바로 export default 할 수는 없다.

2. export

- 한 파일 내에서 여러 변수들을 export하는 것이 가능하다.

- import할 때에는 export할때 사용된 변수명을 동일하게 설정해야한다.

- 다른 이름으로 alias할때에는 as를 사용한다.

나는 개인적으로 2번을 선호한다.

다만, 하나의 파일에서 진짜 하나의 변수만 export하고 유일한 경우는 export default를 사용하기도 한다.

왜냐하면 변수의 이름을 변경했을때 그 변수와 관련된 모든 위치에 대해서 이름을 변경하기 용이하기 때문이다.

tree-shaking 관점에서도 다르게 볼 수 있다.

참고로

import components from "components"
import \* as components from "components"
javascript

같은 형태는 tree shaking이 되지 않는다.

웹팩에서 sideEffect: false 등을 해주던가 해야한다.

import {component} from "components"
javascript

하지만 위 코드는 번들시에 필요한 모듈에 대해서만 정보를 가져오므로, tree-shaking이 된다고 할 수 있다.

참고로 esm 으로 작성된 코드가 아니면 (lodash) 그냥 tree-shaking이 되지 않는다.

별도의 plugin을 설치해야한다.
