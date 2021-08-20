# Variable Environment, Lexical Environment



실행 컨텍스트(EC)가 생성이 될 때, Variable Environment(VE), Lexical Enviroment(LE)가 동시에 생성된다.

둘은 변수의 식별자 또는 함수를 저장하는 Enviroment Record, 
Outer Enviroment를 참조하는 outerLexicalEnviroment Reference가 있다는 공통점이 있다.



#### Variable Enviroment

- Environment Record: 현재 실행 컨텍스트 내에서 호이스팅이 되는 var, 함수 선언문 등을 저장.
- outerLexicalEnviroment Reference: Outer Environment를 참조.



#### Lexical Enviroment

- Environment Record: let, const로 선언된 변수, 함수표현식 등을 저장
- outerLexicalEnviroment Reference: **Variable Environment**를 참조



아래 코드를 살펴보자

```js
function foo(){
  var name = 'doby';
  let gender = 'male';
  if(name === 'doby'){
    const city = 'seoul';
    var varTest = 'varTest';
    console.log(name, gender, city);
  }
}

foo();
```



![img](https://media.vlpt.us/images/proshy/post/b6a65236-a471-4eef-8f52-71eaf20ed7b6/image.png)



위를 보면, if안의 블럭도 따로 LE를 가지고 있는 것을 알 수 있다. (블럭도 하나의 Lexical Environment를 가진다는 뜻) 

(하지만 블럭안의 var은 호이스팅되어서 Variable Environment에 존재)

그리고 그 Outer Environment는 `foo`의 Lexical Evironement를 참조하고 있다.



Ref

https://velog.io/@proshy/JSVariable-environment-vs-Lexical-environment

https://cabulous.medium.com/javascript-execution-context-lexical-environment-and-block-scope-part-3-fc2551c92ce0

