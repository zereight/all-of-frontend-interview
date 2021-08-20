>  CRA에서 모든 라이브러리가 dependency에 들어가있는 이유는?



저도 궁금해서 찾아봤는데요.

[댄 아브라모브가 말하길](https://github.com/facebook/create-react-app/issues/6180),

CRA는 모든 라이브러리를 bundle된 이후에 사용하기 때문에, devdepedency와 구별이 무의미하다고 생각했고, 혹시나 있을 스크립트 오류를 방지하기 위해 dependency에 모든 라이브러리를 넣었다고 합니다.

node app 같은 경우에는 dev와 구별짓는 것이 의미가 있는데, CRA는 node app이 아니라는 것이다.



"엥? CRA에서도 `npm start` 같은 걸로 실행하는데 뭐가 node app이 아닙니까?"



웅 아니다.

CRA에서 `npm start`는 [react-script](https://velog.io/@rlaqltmxm/create-react-app-살펴보기) 라는 라이브러리를 이용하는데, 요녀석은 webpack으로 `src/index.js` 를 entry로 하는 소스파일들을 **번들링**한다.

원래 node app이었다면, dev에서만 사용할 라이브러리를 production 코드에서는 배포안하고 결정하기 위해 구별한건데,

CRA는 항상 번들링하므로 이건 node app이 아니라 항상 번들링해서 배포하는 형식이고 dev에 넣든 dependency에 넣든 항상 모든 dependency가 사용되어서 구별하는게 사실 의미가 없다는 것이다!

