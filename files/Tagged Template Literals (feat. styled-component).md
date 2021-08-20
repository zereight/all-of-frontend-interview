# Tagged Template Literals (feat. styled-component)



`styled.button''` 문법은 사실 자바스크립트 자체에 있는 문법이다. (백틱사용)

"Tagged Template Literals"라고 불린다. (ES6)

`styled.button''`과 `styled.button()`은 사실 같은 것이며 보이는 것만 다를 뿐이다.



동작 원리가 어떻게 되는지 파악해보자.



```js
const fn = (string, ...value) => {
  console.log(string);
  console.log(value);
}

fn`44${1}22${2}` // [ '44', '22', '' ], [ 1, 2 ]
```

위 처럼 나온다.

string값, ${}값, string값이 반복됨을 알 수 있고, string과 value값이 각각 배열형태로 순선대로 나옴을 알 수 있다.



```js
console.log(`도비${"파노"}하루${"심바"}유조${"곤이"}피터지그루밍${"브콜"}`);

과

print`도비${"파노"}하루${"심바"}유조${"곤이"}피터지그루밍${"브콜"}`;
```

그 원리를 이용하여

위 2개의 출력을 똑같게 만들어보자.

```js
const print = (strings, ...params) => {
  const result = strings.reduce((acc, currentString , index) => {
    return `${acc}${currentString}${params[index]?params[index]:''}`
  },'')
  
  console.log(result);
}


print`도비${"파노"}하루${"심바"}유조${"곤이"}피터지그루밍${"브콜"}`
console.log(`도비${"파노"}하루${"심바"}유조${"곤이"}피터지그루밍${"브콜"}`);
```

똑같게 만들었다!

만들고 보니,
어떤 템플릿 리터럴을 인자로 받을때 사용하면 좋을것 같다는 생각이 든다.

언젠가 쓸 수 있겠지? 기억해두자!



참고

https://mxstbr.blog/2016/11/styled-components-magic-explained/

https://velog.io/@kdo0129/Tagged-Template-Literal