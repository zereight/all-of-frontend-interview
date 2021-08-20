## JSX.ELement

`JSX.Element` 는 1개의 리액트 Element만 허용한다. (string도 X)
만약 `JSX.ELement`로 여러 리액트 Element를 받고 싶다면

```tsx
children: JSX.Element | JSX.Element[];
```

이렇게 써줘야 한다.

## ReactChild

`JSX.Element`의 하위호환으로써, string을 허용하지 않는다.
만약 여러 리액트 Element를 받고 string까지 받고 싶으면 이렇게 수정해줘야한다.

```tsx
children: JSX.Element | JSX.Element[] | string | string[];
```

이제는 이렇게 쓰지말고 `ReactChild`를 쓰면된다.

```tsx
children: ReactChild | ReactChild[];
```

하지만 이것도 여러 리액트 Element를 허용하지 않아서 따로 선언이 필요하다.

## ReactNode

이제는

```tsx
children: ReactChild | ReactChild[];
```

이렇게 쓸 필요없이

```tsx
children: ReactNode;
```

이렇게 쓸 수 있다.
이건 여러 Element도 되고, string도 되고, numbers도 되고, fragments도 되고, portals도 되고.. 다된다!
