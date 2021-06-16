## ProtoType 이란?

[출처](https://medium.com/@bluesh55/javascript-prototype-이해하기-f8e67c286b67)

자바스크립트는 프로토타입 기반 언어이다.



> Class vs Prototype

Class는 OOP를 지향하는 개념이다.

근데, 자바스크립트도 객체지향언어다.

하지만 자바스크립트에는 원래 Class라는 것이 없었다. (지금은 버전이 업그레이드 되면서 나옴. 그래도 Prototype기반언어이다!)

그 Class를 대체할 수 있는 개념이 바로 Prototype이다.



Class의 핵심 기능중 하나가 **상속**인데, Prototype을 이용해서 이 상속을 흉내낼 수도 있었다.



> 언제 쓰나요?

아래 코드를 봅시다.

```js
function Person(){
  this.eyes = 2;
  this.nose = 1;
}

const kim = new Person();
const park = new Person();
```

위 코드는 kim, park이라는 변수에 Person의 인스턴스를 할당하고 있습니다.

Person이라는 것은 eyes를 2, nose를 1로 공통적으로 갖고 있는데, 이것이 각 인스턴스마다 생성되면서,

인스턴스를 100개 만들면 200개의 변수가 메모리에 생겨나게 될 것입니다.



하지만 Prototype을 사용하면 어떻게 될까요?

```js
function Person() {}

Person.prototype.eyes = 2;
Person.prototype.nose = 1;

const kim = new Person();
const park = new Person()
```



위와 같이 사용할 수 있을 것입니다.

Person.prototype 이라는 객체가 어디 존재하고 거기에 어떤 프로퍼티들을 할당해 놓은 것인데요.

이제부터는 kim, park은 Person.prototype이라는 메모리 공간에서 eyes, nose를 참조하여 사용할 수 있습니다. (공유한다는 뜻)

이제 객체를 100개 생성해도 eyes, nose 변수의 개수는 여전히 2개인 것이죠.



> Prototype Link와 Prototype Object

Prototype을 이해했다고 말하려면 위 2가지 개념을 자유롭게 사용할 수 있어야 합니다.

**Prototype Object**

객체는 언제나 함수로 생성된다.

```js
function Person(){} // <= 이게 함수이다.

const personObject = new Person(); // 함수로 객체를 생성했다!
```



아닌 경우도 있다구요?

```js
const obj = {}; // 봐요! 함수가 아닌데 객체를 생성했잖아요!

const obj = new Object(); // 사실은 이렇게 동작합니다.
```



그 외에도 Object처럼 Function, Array 등도 모두 함수로 정의되어 있습니다.



*그럼 이 함수들이 정의될때 무슨일이 일어날까요?*

1. 해당 함수에 생성자 자격 부여

   Constructor 자격이 부여되면, new를 통해서 객체를 만들어낼 수 있게 됩니다.

   ```js
   new Object();
   ```

2. 해당 함수의 Prototype Object 생성 & 연결

   그러니까 함수를 정의하면 Prototype Object가 함께 생성된다는 것입니다.

   ![img](https://miro.medium.com/max/1778/1*PZe_YnLftVZwT1dNs1Iu0A.png)

   위 그림처럼 Person이라는 함수를 만드니까

   Person Prototype Object라는 것이 만들어진것을 알 수 있습니다.


   그리고 생성된 함수는 prototype이라는 속성을 가지고 Person Prototype Object와 연결됩니다.

   Person Prototype Object도 하나의 객체이고 constructor를 가지고 있습니다.
   그리고 이 constructor는 Person Prototype Object와 함께 생성되었던 Person 함수를 가리킵니다 ㅎㅎ

   

   
   


   또한, Person Prototype Object는 proto라는 속성도 가지고 있는데요. 이것이 바로 Prototype Link입니다.

   ```js
   function Person(){}
   
   Person.prototype.eyes = 2;
   Person.prototype.nose = 1;
   
   const kim = new Person();
   const park = new Person();
   
   console.log(kim.eyes);
   ```

   위와 같은 예제가 있다고 해봅시다.

   Kim, park에는 eyes, nose가 없고 Person.prototype을 통해서 값을 읽어올 수 있었는데요.

   그것이 바로 Prototype Link (proto)의 역할입니다.

   kim에 eyes가 없는 것을 확인하고, proto는 자신의 기원이 되는 함수의 Prototype Object를 가리킵니다.

   즉, kim의 proto는 Person Prototype Object를 가리키고 있는 것이죠.

   proto를 통해서 prototype object에 접근을 해서 eyes와 nose를 읽어온 것입니다!

   ![img](https://miro.medium.com/max/1654/1*jMTxqTYDZGhykJQoimmb0A.png)

   만약 이 prototype chain을 타고 상위로 가는데, 계속 해당 속성값이 없다? 그러면 최종적으로 undefined를 반환하게 됩니다.



> prototype과 proto의 차이점은 무엇인가요?

아까도 말했듯이 prototype은 "함수"가 가지고 있습니다.

하지만 proto는 "모든 객체"가 가지고 있는 속성입니다.

왜냐하면 모든 객체는 자신을 만든 함수의 Prototype Object를 기억하고 있어야 하기 때문이지요.