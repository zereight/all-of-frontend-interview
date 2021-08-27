JSX.Element
ReactChild
ReactChildren
ReactNode
ReactElement

이것들은 타입스크립트에서 리액트 컴포넌트의 타입을 정해주는 것들이다.

관계는 다음과 같다.
<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https://blog.kakaocdn.net/dn/6zVOF/btqEk1y48AS/Jbzo3JU5BjVF0pNaQXia71/img.png"/>

> ReactNode

ReactNode는 만능이다.
코드는 아래와 같다.

```ts
type ReactNode =
  | ReactChild
  | ReactFragment
  | ReactPortal
  | boolean
  | null
  | undefined;
```

string도 되고, 포탈도 되고, 프래그먼트도 되고, 여러 컴포넌트도된다.

> ReactChild

코드는 아래와 같다.

```ts
type ReactChild = ReactElement | ReactText;
```

리액트 컴포넌트 + 숫자 + 문자열을 뜻한다.

> ReactElement

코드는 아래와 같다.

```ts
interface ReactElement<
  P = any,
  T extends string | JSXElementConstructor<any> =
    | string
    | JSXElementConstructor<any>
> {
  type: T;
  props: P;
  key: Key | null;
}
```

리액트에서 createElement를 했을때 반환되는 객체구조와 동일하다.

> ReactText

코드는 아래와 같다.

```ts
type ReactText = string | number;
```

문자열과 숫자를 뜻한다.

> ReactChildren

코드는 아래와 같다.

```ts
interface ReactChildren {
  map<T, C>(
    children: C | C[],
    fn: (child: C, index: number) => T
  ): C extends null | undefined
    ? C
    : Array<Exclude<T, boolean | null | undefined>>;
  forEach<C>(children: C | C[], fn: (child: C, index: number) => void): void;
  count(children: any): number;
  only<C>(children: C): C extends any[] ? never : C;
  toArray(
    children: ReactNode | ReactNode[]
  ): Array<Exclude<ReactNode, boolean | null | undefined>>;
}
```

> JSX.Element

코드는 아래와 같다.

```ts
declare global {
    namespace JSX {
        interface Element extends React.ReactElement<any, any> { }
```

즉 JSX.Element는 ReactElement와 같다고 볼 수 있다.

---

이렇듯 React의 컴포넌트 Type에는 다양하고 복잡한 타입들이 존재한다.
그중에서 가장 편하게 사용할 수 있는 것은 `ReactNode`이다.

사실 children props값으로 어떤 것이든 들어올 수 있게 하겠다는 의미로 타입을 대부분 `ReactNode`로 두었는데,
사용하다 보면 어떤 컴포넌트의 children은 string 또는 undefined가 되면 안되는 경우, 또는 무조건 `string`으로 들어오는 경우가 생겼다.

이런 부분은 타입 추론이 잘되도록 구체적으로 차근차근 리팩터링 해주는 것이 옳은것 같다.
