# CSR에서 SEO는 어떻게 해결할 수 있는가?

[출처](https://mygumi.tistory.com/385)

메타 태그 사용으로 해결할 수 있다.

title태그와 meta 태그를 활용한다.

```html
<html>
  <title>타이틀</title>
  <meta name="title" content="" />
  <meta name="description" content="" />
  <meta property="og:url" content="" />
  <meta property="og:type" content="website" />
  <meta property="og:title" content="" />
  <meta property="og:description" content="" />
  <meta property="og:image" content="" />
</html>
```



위와 같은 태그들을 통해서, 검색엔진 노출이안 공유할 때 원하는 정보를 인식하여 노출할 수 있게 된다.



React에서도 이를 위한 react-helmet, react-snap같은 라이브러리들이 존재한다.



하지만, SSR보다는 매끄럽지 못하긴하다고 한다.