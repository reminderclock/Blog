# 자바스크립트 객체 분류

## 내장 객체(Bulit-in Object)

- 네이티브 객체(Native Object)에서 내장 객체(Bulit-in Object)로 명명법이 변경되었다고 한다.
- ECMAScript으로 정의되어진 객체. 애플리케이션 전역의 공통 기능을 제공
- 애플리케이션의 환경과 관계없이 언제나 사용가능
- 내장 객체를 Global Objects 라고 부르기도 하는데 이것은 전역객체(Global Object) 와는 다른의미
- 내장객체는 전역범위의 여러 객체를 뜻함
- 내장 객체는 다음과 같은 객체, 메소드, 속성을 포함한다
- NaN, undefined, isNaN(), parseInt(), Object, Fuction, Number, Map, Set,Array,JSON, Promise ...

## 호스트 객체(Host Object)

- 호스트 환경 즉, 자바스크립트가 구동되는 환경에서 제공하는 객체를 말한다.
- 브라우저 환경 객체: window(전역객체), DOM, BOM, Ajax, HTML5 APIs ...
- 서버 환경 객체: global(전역객체), http, https, fs, URL, os ...
- 전역객체: 모든 객체의 유일한 최상위 객체를 의미

## 사용자 정의 객체(User-defined Object)

```javascript
var myCar = new Object();
myCar.make = "Ford";
myCar.model = "Mustang";
myCar.year = 1969;
```

## 호스트 객체(Host Objects)와 내장 객체(Built-in Objects)의 차이점은 무엇인가요?

- 호스트 객체는 특정 호스트 환경에서 실행 환경을 완성하기위해 제공되는 객체이고 네이티브객체는 어플리케이션 환경에 상관없이 제공되는 객체이다.
- 내장객체이면서 호스트 객체인 객체는 없다.

### 참고

[Bulit-in Object](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects)

- 객체의 프로퍼티와 메소드에 대해서 설명해보세요

  객체는 프로퍼티들의 모음이며, 프로퍼티는 key와 value로 이루어져 있다.

  이중 value가 함수로이루어져 있는 프로퍼티를 메소르라고 부른다.

  역할:

  - 프로퍼티: 객체에 저장되어있는 data
  - 메소드: 객체가 요청받을수 있는 action

- 함수와 메소드의 차이를 설명해보세요

  메소드는 객체의 구성요소이기 때문에 객체를 통해서 메소드를 실행하지만,

  함수는 자체로 객체이기 때문에 자기자신을 수행합니다.

- 전역공간에서의 this에 대해 설명해보세요

  호스트환경에서의 최상위객체가 전역공간에서의 this입니다.

  브라우저: window

  서버(node.js): global

- 메소드 내부에서 this 와 함수내부에서 this 는 무엇인가요?

  메소드 내부에서의 this는 해당 메소드의 객체를 가르키고

  일반 함수의 this는 전역객체 / 화살표 함수에서의 this는 상위 스코프의 this

- call() 과 apply() 같은 메소드에서 this는 무엇인가요?

함수 호출 관련 메소드
this를 새로 바인딩해서 호출위해 사용

매개변수로 객체를 넣어주면 그 객체, 아무것도 없으면 전역객체
