# 10분테코톡 지그의 Virtual DOM

## 1. 브라우저의 동작

### 브라우저 렌더링 과정

1. 돔 트리 생성 → 렌더 엔진이 html을 파싱하여 돔 노드로 이루어진 트리 생성
2. 렌더 트리 생성 → css 파일과 inline 스타일을 파싱, DOM + CSSOM = 렌더 트리를 생성
3. Layout (reflow) → 각 노드들의 스크린에서의 좌표에 따라 위치 결정
4. Paint(repaint) → 실제 화면에 그리기

- 여기서 문제는 어떤 인터랙션에 돔에 변화가 발생하면 렌더트리가 그때마다 재생성됨.
- 변화가 발생하면 모든 요소들의 스타일을 다시 계산하고 Layout 즉, reflow과정을 거치고,
- 다시 repaint하는 과정까지 반복합니다.

### DOM 조작의 비효율성

- ex) 유저가 어떤 포스트에 좋아요를 누르거나, 담아둔 장바구니 목록에서 상품을 하나 삭제하거나,
- 담아준 장바구니 목록에서 상품을 하나 삭제하거나, 어딘가에 댓글을 남기면, 전체 노드들이 처음부터 다시 그려지는 것이었습니다.
- 딱 봐도 불필요한 과정이 반복 됨... → 돔을 조작하는 소모적인 비용
- 웹에서 돔 조작은 매우 중요하지만, 시간이 많이 드는 소모적인 과정으로 여겨졌습니다.

## 2. Virtual DOM의 등장

### Virtual DOM의 등장

- 더군다나 최근에서 SPA이 많아지면서 돔 트리를 즉각적으로 많이 변경할 일이 생겼다.
- 전체 페이지를 서버에서 매번 보내주는 것이 아니라,
- 브라우저단에서 자바스크립트가 관리하기 때문에 돔 조작을 더욱 효율적으로 할수 있게끔 돔 조작 최적화 필요
- 그래서 등장한 것이 → virtual DOM 이다.

### Virtual DOM의 동작원리

- virtual DOM 은 기존 돔의 친구이자 어떤 복사본
- 다른 표현으로는 virtual DOM은 html DOM의 추상화 버전

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c250201f-08ce-42a6-93c1-1f255abd926e/스크린샷_2021-07-31_오후_8.21.33.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c250201f-08ce-42a6-93c1-1f255abd926e/스크린샷_2021-07-31_오후_8.21.33.png)

- 실제 DOM object와 같은 속성들을 가지고 있지만, 실제 돔이 갖고 있는 api는 같고 있지 않다.
- 데이터가 변경되면 전체 ui는 virtual DOM에 렌더링 됩니다.
- 그리고 이전 virtual DOM 에 있던 내용과 업데이트 후에 내용을 비교하여 바뀐 부분만 실제 DOM에 적용시킵니다.
- 즉, virtual dom에 변경사항이 반영되면 원본 돔에 필요한 변화만 반영되어서,
- 전체 real 돔을 바꾸지 않도고 필요한 ui의 업데이트를 적용할수있다.
- virtual dom이 어떻게 생겼길래 이러한 동작이 가능할까여??

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1ad70df1-bf91-4df9-85ad-fade7aa7c9b6/스크린샷_2021-07-31_오후_8.32.45.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1ad70df1-bf91-4df9-85ad-fade7aa7c9b6/스크린샷_2021-07-31_오후_8.32.45.png)

- virtual dom은 html 객체에 기반한 자바스크립트 객체로 표현할수 있다.
- 어떤 html 코드가 있을때, 사실은 이런 js 객체로 표현된다는것
- 그리고 이러한 처리는 실제 돔이 아닌 메모리상에서 동작하기 때문에 훨씬 더 빠르게 동작한다.
- 그리고 vd tree는 실제 렌더링 되지 않기 때문에 연산비용이 적다.
- 요소가 30개가 바뀌었다고 레이아웃을 30개씩 새로 하는 것이 아니라,
- 모든 변화를 하나로 묶어서 딱 한번만 실행시킵니다.
- 이렇게 연산횟수를 줄일수 있기 때문에 실제 dom 리렌더링에 비해서 효율적
- 사실 virtual dom 이 하는 건 dom fragment의 변화를 묶어서 적용한 다음 기존 dom에 던져주는 과정
- virtual dom은 이 과정을 자동화 , 추상화 해놓은 것에 불과하다
- 리액트는 virtual dom을 이용하는 대표적인 js 라이브러리다.
- 리액트 공식문서에서는 virtual dom을 다음과 같이
- ui의 가상적인 표현을 메모리에 저장하고 리액트돔과 같은 라이브러리에 의해 실제 돔과 동기화하는 개념
- —> 재조정

## 3. React의 Virtual DOM

### JSX

각 컴포넌트에서 리턴 되는 react element를 jsx문법으로 작성하는 것 입니다.

마치 그냥 html태크들처럼 생겼지만 jsx는 자바스크립트의 확장 문법이다.

이렇게 간단한 jsx를 컴포넌트에서 리턴시키면

바벨은 jsx를 react,createElement() 호출로 컴파일

## React의 Virtual DOM

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2753e2a5-f1ef-45d3-9635-cfbe519b1803/스크린샷_2021-07-31_오후_8.44.16.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2753e2a5-f1ef-45d3-9635-cfbe519b1803/스크린샷_2021-07-31_오후_8.44.16.png)

react.createElement는 내부적으로 다음과 같이 표현됨.

앞에서 본 virtual 돔 객체 구성현태와 비슥하다.

react element는 돔 요소의 가상 버전으로 가볍고,

상태를 가지지 않으며, 불변성 유지한다.

light & immutable & stateless

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/54d40a76-9be9-4e08-b63c-38623859d5c8/스크린샷_2021-07-31_오후_8.45.13.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/54d40a76-9be9-4e08-b63c-38623859d5c8/스크린샷_2021-07-31_오후_8.45.13.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6b566402-0ab2-4225-86e4-fffa71719e03/스크린샷_2021-07-31_오후_8.48.21.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6b566402-0ab2-4225-86e4-fffa71719e03/스크린샷_2021-07-31_오후_8.48.21.png)

render에 의해서 비로소 실제 dom요소가 된다.

리액트은 이 객체를 읽어들이고, 이를 사용해서 dom을 구성하고 항상 최신상태로 유지

이 react element는 변경이 불가하기 때문에

한번 요소를 만들었다면 데이터가 변했다고 해서 그 자식이나 속성을 맘대로 변경할수 없다.

각 요소는 해당 순간의 ui를 스냅샷형태로 보여주기만 할 뿐입니다.

그렇면 ui를 업데이트 할수 있는 유일한 방법은 새로운 요소를 만들어 reactDom.render() 로 전송하는 것 뿐이다.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fa1188e4-75a3-4334-87fd-ee76dba97512/스크린샷_2021-07-31_오후_8.54.22.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fa1188e4-75a3-4334-87fd-ee76dba97512/스크린샷_2021-07-31_오후_8.54.22.png)

하나의 컴포넌트를 바꿔주고 싶은것 뿐인데 아예 새로운 element를 렌더 해야 되는 것처럼 보인다.

하지만 이때 리액트는 virtualdoom 이용

### diffing 알고리즘

- 모든 리액트 돔 오브젝트는 그에 대응하는 virtual dom object가 있다.
- virtual dom object는 dom object를 대신한다.
- 각각 하나하나에 매핑된다.
- 데이터가 업뎃되면 react.createElement를 통해 jsx element를 렌더링한다.
- 이때 모든 각각의 virtual dom object 업뎃됨.
- virtual dom 은 빠르게 업데이트 되서 비용이 많이 들지 않는다.

- 그리고 vd 업뎃되면 react는 virtual dom을 업데이트 이전에 virtual dom 스냅샷과 비교하여
- 정확히 어떤 virtual dom 이 바뀌었지는 검사한다.
- 이 과정은 Diffing 알고리즘이라고 부른다.

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/aeccce9d-6e18-436a-8bc7-985a8a7593fe/스크린샷_2021-07-31_오후_9.02.46.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/aeccce9d-6e18-436a-8bc7-985a8a7593fe/스크린샷_2021-07-31_오후_9.02.46.png)

어떤 재조정 과정에 해당

element의 속성값만 변한 경우에는 속성값만 업데이트 하고,

해당 엘리먼트에 태그나 컴포넌트가 변경된 경우라면,

해당 노드를 포함한 하위의 모든 노드들을 언마운트

즉 제거한 뒤에 새로운 virtual dom 으로 대체합니다.

이런 변경이나 업데이트가 모두 마무리 된 이후에 딱 한번은 실제 돔에 이 결과를 업데이트 한다.

### react virtual 돔

1. 플러스 버튼 누르면 이미지 태그 추가 되고 바뀐 데이터에 따라 전체 가상 돔이 업데이트 된다
2. 그리고 내부적으로 자바스크립트 객체로 생성된 가상돔이 업데이트 이전의 시점과 어떤 부분이 달라졌는지 비교한다.
3. 여기서 달라졋다고 파악된 부분. 즉, 새로운 이미지 태그만 리얼 돔 트리에 렌더링된다.
4. 리얼돔에서 변화가 스크린에 그려지낟.

### 무조건 가상 돔이 좋나요??

정보 제공만 하는 웹페이지라면 인터택션이 발생해지 않기 때문에 일반 돔 성능이 더 좋을수 도 있다.

spa 로 제작된 큰 규모의 웹 페이지에서는 가상돔을 사용해서 브라우저의 연산 양을 줄여서 성능 개선할수 있다.
