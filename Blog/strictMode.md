# "use strict";

## Strict mode

- ES5에서 소개된 Javascript의 엄격모드는 Javascript의 제한된 버전을 선택하여 암묵적인 느슨한 모든(sloppy mode)를 해제하기 위한 방법.
- 브라우저에 따라 부분적으로 지원하거나, 아예 지원하지 않는다.

### 등장배경

- ES5 등장전까지는 기존의 기능을 변경하지 않으면서 새로운 기능이 추가되어왔다.
- 이전에 작성했던 코드가 망가지지 않는다는 장점이 있었지만, 언어의 불완전한 부분이 남아있게됨
- 이런 이유로, ES5에서 새로운 기능이 추가되고 기존 기능중 일부가 변경됨
- 기존 기능중 변경된 부분이 그 이전의 코드에서 문제가 생기지 않도록, ES5 기본 모드에서 활성화 되지 않도록 설계
- 대신 "use strict"; 구문을 작성해서 엄격모드를 활성화 했을때만 적용 되도록함.

## 엄격모드 적용하기

"use strict" → 구문을 작성

- 전체 스크립트 적용 → 최상단에 작성
- 함수에 적용

```jsx
function strict() {
'use strict";
// 함수 최상단에 작성
}
```

- 모듈에 적용

```jsx
function strict() {
  // 모듈이기때문에 기본적으로 엄격
}
export default strict;
```

## 엄격한 모드 변경

### 실수를 에러로

```jsx
"use strict";
a = 7; // 변수 선언 안해주었을때
var undefined = 5; // 쓸수 없는 프로퍼티에 할당해주었을때
delete Object.prototype; // 삭제할수 없는 프로퍼티를 삭제하려할때

// 중복 인수명
function abc(a, a, b) {
  "use strict";
  return a + a + b;
}

var sum = 01 + 2 + 3; // 구문에러
flase.true = ""; // 원시값에 프로퍼티 설정하는 것
```

### 변수 사용 단순화

- JS 엔진 최적화 작업을 어렵게 만드는 실수를 바로 잡는다.

### Javascript '보안'

- 보안된 자바스크립트를 작성하기 쉽게 해준다. —> 함수의 this는 강제로 객체가 되지 않는다.
- 자동박싱은 성능비용 뿐 아니라 전역객체가 브라우저에 노출되는 것은 보안상 위험하다.
- —> 전역객체들은 JS 환경의 "보안" 기능에 접근하는 것 제공

- 참조
  [https://ko.javascript.info/strict-mode](https://ko.javascript.info/strict-mode)

[https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Strict_mode](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Strict_mode)
