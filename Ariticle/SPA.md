# [10분 테코톡] 주모의 SPA

## MPA

- 두개 이상의 페이지로 구성된 애플리케이션
- 사용자의 클릭과 같은 사용자 인터랙션이 발생할때 앱이 다시 새로고침되는 전통적인 방식
- 렌더링 방식으로 서버 사이드 렌더링을 채택한다.

## SSR

- 서버로 부터 완전하게 만들어진 html 파일을 받아와 페이지 전체를 렌더링하는 방식
- 방식
- 클라이언트에서 초기 화면을 로드하기 위해서 서버에 요청 보냄
- 서버는 html로 화면에 표시하는데 필요한 완전한 리소스를 응답합니다.
- 사용자 인터랙션시 클라이업트는 서버에 요청
- 서버는 html로 화면에 표시하는데 필요한 완전한 리소스를 응답
- 전체 요소들을 모조리 서버로 부터 다시 다운받아옴
- 이런 이유로 앱이 다시 시작되고 화면이 깜빡인 후에 표시

### MPA with SSR 장점

- SEO(검색 엔진 최적화)에 유리 →검색엔진이 웹을 크롤링하면서 페이지에 컨텐츠 색인을 생성하는 과정
- 화면을 구성하는 각각의 페이지가 있기 때문에 SEO 유리
- 빠른 초기 로딩 → 서버로 부터 화면에 렌더하기 위한 필수적인 요소를 먼저 가져오기 때문에 설명할 클라이언트 사이드 렌더링보다 초기 로딩 속도가 빠르다..

### 단점

- 불편한 사용자 경험
- 서버 부하 증가 → 페이지를 요청할때마다 서버에서 페이지를 구성하는 모든 리소스를 준비해서 응답함으로 서버 부담이 증가

## SPA

- 하나의 페이지로 구성된 애플리케이션
- 클라이언트 사이드 렌더링 채택
- 클라이언트 사이드 렌더링이란

## CSR

- 사용자의 요청에 따라 필요한 부분만 응답받아 렌더링하는 방식
- 클라이언트에서 초기 화면을 로드하기 위해 서버 요청 보냄
- 그럼 서버는 화면을 표시하는데 필요한 완전한 리소스를 응답
- 모든 js 파일을 다운 받아야 되서 초기 로딩이 더 오래 걸림
- 전체 페이지가 새로고침 되지 않고 부분적으로 렌더링 된다.

### 장점

- 빠른 속도, 서버 부하 감소 → 부분 적으로 바뀐 데이터만 가져옴으로 빠른 속도를 보임, 서버의 부담 줄임
- 사용자 친화적 - 페이지 안의 컨텐츠를 클릭하여 다음 단계로 전환하는 과정에서 링크가 없이 때문에 깜빡임 없이 부드러운 이동 경을 경험

### 단점

- SEO(검색엔진최적화)에 불리 → 사용자와 상호작용 후에 페이지 내용을 로드하기 때문에 웹 클롤러가 페이지를 색인화 하려고 하면 내용의 빈 페이지처럼 보이게 됩니다.
- 느린 초기 로딩 속도

## SPA에서 SSR 채택 못하나요??

- no,

## 어떤식으로 개발을 해야 할까요??

- 클라이언트 사이드 렌더링 방식을 채택하여 개발한다고 했을때, 모든 부분을 클라이언트 사이드 렌더링 방식으로 구현해야하는 것은 아님
- 애플리케이션을 구성하는 부분에 따라 단순 정보 제공과 같은 부분은 서버사이드 렌더링으로 ,
- 동적인 변화가 필요한 부분은 클라이언트 사이드 렌더링 방식으로 개발하는 것이 좋다.
