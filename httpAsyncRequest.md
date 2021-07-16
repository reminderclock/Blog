# AJAX와 fetch, axios와의 차이는?

## AJAX(Asynchronous JavaScript And XML)

- 비동기 자바스크립트와 XML
- XML(Extensible Markup Language): W3C 권고 범용 마크업 언어, 데이터 내용을 정의할때 사용
- 서버와 통신하기 위해 XMLHttpRequest 객체를 사용
- JSON, XML, HTML , 일반 텍스트 형식 등을 포함한 다양한 포맷을 주고 받을수 있다.
- AJAX의 비동기성을 통해 전체 페이지가 아닌 일부분만 업데이트 할수 있게 해준다.
- 서버와의 통신을 위해 XMLHttpRequest 객체를 사용

## AJAX 특징

- 페이지 새로고침 없이 서버에 요청
- 서버로부터 데이터를 받고 작업을 수행

## Fetch

- ES6 부터 도입된 HTTP 비동기 통신 내장 API
- XMLHttpRequest 와 비슷하지만, 좀더 강력하고 유연한 조작이 가능함.
- Promise 객체 형태 반환

### AJAX 와 Fetch 차이

- Fetch() 로 부터 반환되는 Promise 객체는 HTTP error 상태를 reject 하지 않는다.
- Ok 상태가 flase인 resolve 반환
- 네트워크 장애나 요청이 완료되지 못한 상태 reject 반환
- 보통 fetch는 쿠키를 보내거나 받지 않는다. 쿠키를 전송하기 위해서는 자격증명(credentials) 옵션을 반드시 설정

## **Axios**

- 브라우저, Node.js를 위한 Promis API 를 활용하는 HTTP 비동기 통신 라이브러리(외장 라이브러리)
- Promise 객체 형태 반환
- 크로스 브라우징 최적화(브라우저 호환성 뛰어남)
- 모듈 설치 필수

## AJAX vs Iframe

1. ajax는 요청의 상태를 읽을수 있다.
2. iframe 에서 액세스할수 없는 페이지 헤더에 엑세스할수 있다.
3. Ajax는 여러 비동기 요청을 처리할수 있다.
4. Iframe 은 요청당 iframe을 생성하고 나중에 삭제할수 있도록 모두 추적해야 하므로 iframe을 사용하면 좀더 까다롭다.
5. 존재하는 라이브러리는 ajax의 장점으로 가득차있으며 더 큰 커뮤니티 지원 기반이 있다.
6. 페이지의 스타일 지정은 ajax를 통해 로드된 콘텐츠에만 적용된다. iframe을 통해 콘텐츠를 로드할때 거기에 스타일을 포함 시켜야 한다.
7. Iframe: 하나의 웹페이지에 두개(또는 그 이상)의 웹페이지를 별도로 표시하는 방법
8. 아이프레임: 사이트 외부에서 로드되는 또 다른 페이지

https://www.notion.so/AJAX-fetch-axios-85556a4319a74957b11e7d18fc72fb04
