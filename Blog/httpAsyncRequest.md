## **AJAX(Asynchronous JavaScript And XML)**

- 비동기 자바스크립트와 XML
- XML(Extensible Markup Language): W3C 권고 범용 마크업 언어, 데이터 내용을 정의할때 사용
- 비동기 http 통신 기술
- 서버와 통신하기 위해 XMLHttpRequest 객체를 사용하는 것
- JSON, XML, HTML , 일반 텍스트 형식 등을 포함한 다양한 포맷을 주고 받을수 있다.
- AJAX의 비동기성을 통해 전체 페이지가 아닌 일부분만 업데이트 할수 있게 해준다.

## **AJAX 특징**

- 페이지 새로고침 없이 서버에 요청
- 서버로부터 데이터를 받고 작업을 수행

## **Fetch**

- ES6 부터 도입된 HTTP 비동기 통신 내장 API
- XMLHttpRequest 와 비슷하지만, 좀더 강력하고 유연한 조작이 가능함.
- Promise 객체 형태 반환

## **Axios**

- 브라우저, Node.js를 위한 Promis API 를 활용하는 HTTP 비동기 통신 라이브러리(외장 라이브러리)
- Promise 객체 형태 반환
- 크로스 브라우징 최적화(브라우저 호환성 뛰어남)
- 모듈 설치 필수

### **AJAX 와 Fetch 차이**

- 사용법 차이
  - fetch: 내장 api라고 설치 없이 바로 사용
    - axios
      - 라이브러리 환경(React, Node.js): NPM 설치
    - 일반 브라우저 환경: CDN 설치
- 에러처리 차이
  - fetch: try에서 response.ok 로 에러를 잡아 catch로 throw해줌
    - axios: http error를 catch에서 바로 error.response로 잡음 -> 성공과 실페에 대한 케이스가 섞여있지 않아 더 가독성 좋은 코드로 작성할수 있음
- http 통신 문법 차이

```jsx
//fetch
    async request(endPoint) {
        try{
            const res = await fetch(`${entryPiont}${endPoint}`);
            console.log(res)
            if(!res.ok){
                throw new Error('http Error');
            }
            return await res.json();
        }
        catch(e) {
            throw new Error(`무언가 잘못되었습니다. ${e.message}`)
        }
    }
```

```jsx
// axios
    async request(endPoint) {
        try {
            const res = await axios.get(`${entryPiont}${endPoint}`)
            return res.data;
        }
        catch(error){
        if(error.response) {
            console.log(error.response.data);
            console.log(error.response.status);
            console.log(error.response.headers);
        }
        else if(error.request) {
            console.log(error.request);
        }
        else {
            console.log('Error', error.message)
        }
        console.log(error.config);
        }
    }
```

### **AJAX 와 Fetch, 어떤 것을 사용해야 할까?**

- 별도의 설치를 하지 않거나, axios의 업데이트를 따라가지 못하는 프레임워크를 사용하는 경우에는 fetch를 쓰고, 안정화된 프레임워크나 좀 더 다양한 기능을 좀더 가독성 좋은 코드로 작성하고 싶으면 axios 사용

### 참조링크

https://developer.mozilla.org/ko/docs/Web/Guide/AJAX/Getting_Started
https://developer.mozilla.org/ko/docs/Web/API/Fetch_API/Using_Fetch
https://xn--xy1bk56a.run/axios/
