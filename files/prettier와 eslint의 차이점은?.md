# prettier와 eslint의 차이점은 무엇인가요?



![img](https://miro.medium.com/max/2144/1*brRpWmobr8UlOwo4vVjqfw.png)



eslint는 보통 잘못입력한 문법을 자동으로 수정하기 위해서 사용된다.

prettier는 팀원간의 코딩 컨벤션을 맞추기 위해서 사용된다.



즉, eslint는 포매팅 기능이 포함되어 있기 때문에 eslint와 prettier를 같이 사용하는 경우에는 충돌이 나게 된다.

따라서, eslint 포메팅 기능을 종료시키고 문법 기능만 사용하게 한다.

`eslint-config-prettier`은 eslint에서 prettier의 포매팅과 겹치는 것을 삭제하고
`eslint-plugin-prettier`는 eslint에서 prettier의 포메팅 기능을 추가한다.



일반적으로 사용하는 방식이,

eslint-config-prettier로 eslint의 기존 포메팅 기능을 없애버리고, eslint-plugin-prettier로 prettier의 포매팅 기능을 사용하도록 하는 것이다.



참고

https://simsimjae.medium.com/prettier와-eslint설정하기-타입스크립트-설정-110dc8ab94b6