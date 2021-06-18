# React Router의 render와 component 차이



[출처](https://mingcoder.me/2019/12/04/Programming/React/react-router-component-vs-render/)



React에서는 `Route` 를 사용해서 라우팅을 할 수 있다.

Route 태그에서 내가 원하는 URI로 이동하게 되면, 어떤 컴포넌트를 렌더링할 것인가를 정할 수 있다.

예를 들면 아래와 같이 구현이 가능하다.

```jsx
<Route path="/dashboard" component="{Dashboard}" />
```

여기서 `<Dashboard>`에 prop을 넘기고 싶다면 아래와 같이 구현이 가능하다.

```jsx
<Route 
  path="/dashboard" 
  component={() => <Dashboard isAuthed="{true}" />} 
  />
```



근데 위 코드는, 이미 존재하는 컴포넌트를 재활용하는 것이 아니라, 
해당 컴포넌트를 렌더링할 때마다 unmount 후 새로운 컴포넌트를 마운팅하는 것이기 때문에, component에 function을 넘기는 것을 추천하지 않는다고 한다.



그래서 나온것이 `render`이다.

```jsx
<Route 
  path="/dashboard" 
  render={props => <Dashboard {...props} isAuthed="{true}" />} />
```



render를 사용하면 불필요하게 컴포넌트가 재마운트되지 않는다.

