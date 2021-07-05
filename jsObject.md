# 자바스크립트 객체 분류

## 내장 객체(Bulit-in Object)

- 네이티브 객체(Native Object)에서 내장 객체(Bulit-in Object)로 명명법이 변경되었다고 한다.
- ECMAScript으로 정의되어진 객체. 애플리케이션 전역의 공통 기능을 제공
- 애플리케이션의 환경과 관계없이 언제나 사용가능
- 네이티브 객체를 Global Objects 라고 부르기도 하는데 이것은 전역걕체(Global Object) 와는 다른의미
- 네이티브 객체는 다음과 같은 객체, 메소드, 속성을 포함한다
- NaN, undefined, isNaN(), parseInt(), Object, Fuction, Number, Map, Set,Array,JSON, Promise ...

## 호스트 객체(Host Object)

- 호스트 환경 즉, 자바스크립트가 구동되는 환경에서 제공하는 객체를 말한다.
- 브라우저 환경 객체: window(전역객체), DOM, BOM, Ajax, HTML5 APIs ...
- 서버 환경 객체: global(전역객체), http, https, fs, URL, os ...
- 전역객체: 모든 객체의 유일한 최상위 객체를 의미

## 호스트 객체(Host Objects)와 내장 객체(Built-in Objects)의 차이점은 무엇인가요?

- 호스트 객체는 특정 호스트 환경에서 실행 환경을 완성하기위해 제공되는 객체이고 네이티브객체는 어플리케이션 환경에 상관없이 제공되는 객체이다.
- 내장객체가 아닌 모든 객체는 호스트 객체이다.
