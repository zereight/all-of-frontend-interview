# POST vs PUT



다시 짚고 넘어가자.

> RESTful API란?

REST라는 것이 자원을 URI로 표현하고, 자원에 대한 행위를 HTTP 메서드(GET, POST, PUT, DELETE)로 표현하는 것이고,

RESTful API는 위와 같은 스타일을 따르는 API라고 할 수 있다.



> POST vs PUT

자원에 대한 행위를 나타내는 4가지 메서드는 CRUD라고 할 수 있다.

(Create, Read, Update, Delete)



여기서 POST는 Create에 매칭,
PUT은 Update에 매칭된다.

즉, RESTful API를 사용하면, 자원에 대한 생성은 POST가 담당하고, 자원에 대한 수정은 PUT이 담당하는 것이다.



> PUT vs PATCH

PATCH도 수정을 담당하는 메서드이다.

그럼 PUT도 수정인데, 이 둘은 어떤 차이가 있을까?



PATCH는 수정만 담당하며 리소스의 일부분만 수정할 때 사용하고,

PUT은 리소스의 모든 속성을 수정하기 위해서 사용한다.



만약

```json
{
  id: 1,
  name: "kim",
  age: 25
}
```

라는 객체가 있을 경우,

name만 변경하고 싶다? 

그러면 PATCH로 

```json
{
  name: "park"
}
```

을 보내주면 된다.



그런데 PUT으로 위와 같은 데이터를 보내주면, 원래 가지고 있던 id, age 프로퍼티가 사라진다.

왜냐하면 PUT은 리소스의 모든 속성을 수정하기 때문이다.

잘 알아두자.

