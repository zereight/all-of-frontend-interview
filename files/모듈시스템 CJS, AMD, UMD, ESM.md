원래 자바스크립트는 html 파일 상에서 호출되면, 호출된 모든 자바스크립트들이 1개의 파일로 통합되었다.

그로 인해서 변수명이 같은경우 등의 사이드 이펙트가 필연적으로 발생할 수 밖에 없었다.

또한 필요한 로직들을 언제든지 사용하기 위해서 일단 어딘가에 선언을 해놓아야 했고, 웹이 복잡해지고 규모가 커짐에 따라서 다양한 불편한점들이 생기게 되었다.

아마 그래서 나온것이 CJS, AMD, UMD, ESM과 같은 모듈 시스템일 것이다.

이러한 모듈은 각각의 자바스크립트의 스코프를 겹치지 않게 해주고, 원하는 코드에서 import해와서 사용할 수 있도록 도와준다.

근데 이 모듈 시스템의 종류가 여러개다.

제목처럼 4개나 있다.

왜 이렇게 4개나 존재해서 우리들에게 혼란을 주는 것일까?

한번 살펴보자

## CJS (CommonJS)

http://www.commonjs.org/

CommonJS는 말 그대로 common 즉, 자바스크립트를 브라우저에서 뿐만 아니라 범용적인 언어로 사용할 수 있도록 하겠다는 의지가 담겨있는 라이브러리이다.

CommonJS에서 사용하는 문법은 다음과 같다.

```js
var lib = require("package/lib");

function foo(){
    lib.log("hello world!");
}

export.foobar = foo;
```

그리고 CommonJS는 아래 코드처럼 동기로 동작하는 특징을 가진다.

```js
var foo = require("foo");
var bar = require("bar");

foo.log("foo");
bar.log("bar");
```

즉, CommonJS는 동기적인 특징으로 서버사이드에서 사용하기 용이한 문법이다.
(게다가 CommonJS의 첫 이름은 ServerJS였다고 한다.)

그래서 백엔드에서 쓰이는 Nodejs가 이 CommonJS 문법을 채택하여 사용하고 있다.

## AMD

CommonJS는 모든 파일이 로컬 디스크에 있을때, 필요한 시점에서 바로 불러올 수 있는 상황을 전제로 한다.
즉, 동기적인 동작이 가능한 서버사이드 자바스크립트 환경을 전제로 하는 것이다.

하지만, 브라우저에서 이런 방식은 필요한 모듈이 모두 다운로드될때까지 아무것도 할 수 없는 상태가 되어서 치명적일 수 있다.

AMD는 Asynchronous Module Definition의 약자로써 비동기적인 특성을 좀더 강조하고 있다.
즉, AMD는 비동기적이 특징으로 클라이언트 사이드 개발에 적합하다. (브라우저)

문법은 다음과 같다.

```js
define(["package/lib"], function (lib) {
  function foo() {
    lib.log("hello world!");
  }

  return {
    foobar: foo,
  };
});

require(["package/myModule"], function (myModule) {
  myModule.foobar();
});
```

## UMD

지금껏 AMD와 CommonJS 이렇게 2개의 그룹으로 나누어지다보니, 서로 호환이 되지 않는 문제가 발생하게 된다.

이것을 해결하기 위해 나온것이 UMD이다.

UMD는 디자인 패턴이라고 부르는 것에 더 적합하고, AMD와 CommonJS, window에 추가하는 방식까지 모두 가능한 모듈을 작성하는 방식이다.

**즉, 문법이라기 모단 여러 모듈 시스템을 동작가능하게 하는 패턴이다.**

Webpack, rollup같은 번들러에서 fallback으로 많이 사용된다.

AMD는 `define`을 사용하고, CommonJS는 `module.exports`를 사용한다.
이 차이를 이용하여 UMD를 만들 수 있다.

어떻게 할 수 있냐하면, 2개의 부분으로 나누면 된다.

- IIFE: 이 함수는 전역범위와 모듈을 선언하는 함수. 이렇게 2개의 파라미터를 가진다.
- 모듈을 생성하는 익명 함수: 이 함수가 IIFE의 2번째 파라미터로 전달된다.

```js
(function (root, factory) {
  if (typeof define === "function" && define.amd) {
    // AMD
    define(["exports", "b"], factory);
  } else if (
    typeof exports === "object" &&
    typeof exports.nodeName !== "string"
  ) {
    // CommonJS
    factory(exports, require("b"));
  } else {
    // Browser globals
    factory((root.commonJsStrict = {}), root.b);
  }
})(this, function (exports, b) {
  //...

  exports.action = function () {};
});
```

위 코드를 보면 `exports`와 `module`이 존재하면 CommonJS 방식으로, `define`이 함수이고 `define.amd`가 존재하면 AMD 방식으로 한다.
둘다 아니라면 window 객체에 모듈을 내보낸다.

이렇게하면 AMD와 CommonJS를 모두 사용가능하게 되어서 어떤 라이브러리를 제작할때 AMD모드나 CommonJS모드 이렇게 2가지 버전으로 굳이 만들 필요가 없게 된다.

## ESM

ES6에 자바스크립트 모듈 기능이 추가되면서 채택된, ECMAScript Module로, 표준 모듈 문법이라고 보면된다.

이제 아래와 같이 코드를 사용할 수 있다.

```js
import lib from "package/lib";

function foo() {
    lib.log("hello world!");
}

export {
    foobar: foo
};
```

최신 브라우저에서 대부분 지원되는 문법이고, 이전의 모듈 시스템들의 장점들을 채택했다.
(CommonJS의 문법일부와 AMD의 비동기 로드를 가져옴)

**그리고 가장 중요한건 Tree-shaking이 가능하다는 것이다.!**

## Q. UMD와 ESM의 차이는 뭔가요?

UMD는 문법이라기 보단, cjs와 amd를 사용가능하게 해주는 일종의 패턴이다.
ESM는 그 자체 문법을 제공한다.

## Q. 왜 ESM만 tree-shaking이 되나요?

ESM은 모듈 로더를 비동기 환경에서 실행한다.
먼저 가져온 스크립트를 바로 실행하지 않고, import, export구문을 찾아서 스크립트를 파싱한다.
그 다음 ESM 모듈 로더는 가져온 스크립트를 비동기로 다운로드하여 파싱하고, 더이상 import할 것이 없어질때까지 import를 찾고, 의존성 그래프를 그릴 수 있다.

이 ESM 모듈 로더가 그리는 의존성 그래프로, tree-shaking기능이 제공되는것 같다.
