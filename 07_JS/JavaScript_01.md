# Javascript



## Intro

- 브라우저 화면을 동적으로 만들기 위한
- 브라우저를 조작할 수 있는 유일한 언어



### 브라우저

- 웹 서버에서 이동하며 클라이언트와 서버간 양방향으로 통신하고
- HTML 문서나 파일을 출력하는 GUI 기반의 소프트웨어
- 인터넷의 컨텐츠를 검색 및 열람
- 웹 브라우저 라고도 한다
- 구글 크롬, 모질라 파이어폭스, 마이크로소프트 엣지, 오페라, 사파리



### History

1. 핵심 인물
   1. 팀 버너스리
      1. WWW, URL, HTTP, HTML 최초 설계자
      2. 웹의 아버지
   2. 브랜던 아이크
      1. Javascript 최초 설계자
      2. 모질라 재단 공동 설립자
      3. 코드네임 피닉스 프로젝트 진행 (파이어폭스의 전신)
2. JS 의 탄생
   1. 1994 년 당시, 넷스케이프 커뮤니케이션스 사의 Netscape Navigator 브라우저가 점유율 80% 이상 독점
   2. 재직중이던 브랜던 아이크가 HTML을 동적으로 동작하기 위한 회사 내부 프로젝트 진행 중 JS 개발
   3. 이름 변천사 Mocha >> LiveScript >> JavaScript (1995)
   4. 1995년, 경쟁사 마이크로소프트에서 자체 커스텀을 통해 Jscript 를 만들어 IE 1.0 에 탑재하며 1차 브라우저 전쟁의 시작
3. 제 1차 브라우저 전쟁
   1. 넷스케이프 vs MS
   2. MS 가 1997년 IE 4 를 발표하며 시장 장악
      1. 윈도우의 시장 점유율 90%
      2. MS 의 공격적인 마케팅
   3. MS 의 승리로 끝나며 2001 년 부터 IE 점유율 90% 상회
   4. 1998년 넷스케이프에서 나온 브랜던 아이크는 모질라 재단 설립
4. 제 2차 브라우저 전쟁
   1. MS vs Google
   2. 2008년 Google 의 Chrome 브라우저 발표
   3. 2011 년 파이어폭스 점유율 돌파 후 2012 년 전세계 점유율 1위
   4. 승리 요인
      1. 압도적인 속도
      2. 강력한 개발자 도구 제공
      3. 웹 표준
5. 파편화와 표준화
   1. 수 많은 브라우저에서 자체 자바스크립트 언어 사용
   2. 크로스 브라우징 이슈
      1. 브라우저 마다 렌더링에 사용하는 엔진이 다르기 때문
      2. W3C 에서 채택된 표준 웹 기술을 채택해 서로 다른 브라우저에서 다르게 구현되는 기술을 비슷하게 만들어 웹페이지를 제작하는 방법론
   3. 제1차 브라우저 전쟁 이후 문제가 된 언어의 **파편화**를 해결하기 위해 크롬의 등장 이후 각 브라우저 및 재단은 **표준화 **시도
6. 현재의 JS
   1. 2015년 ES2015(ES6) 탄생
      1. Next gen of JS
      2. JS 의 고질적인 문제들을 해결
      3. 현재는 대부분의 표준이 ES6+
7. Vanilla JavaScript
   1. 크로스 브라우징, 간편한 활용 등을 위해 많은 라이브러리 등장
   2. 최근 표준화된 브라우저, ES6 이후의 다양한 도구의 등장으로 순수 자바스크립트 활용의 증대



## DOM

> Document Object Model



- 브라우저에서 할 수 있는 일
  - DOM 조작
    - window.document
  - BOM 조작
    - 브라우저 조작
  - JavaScript Core
    - Data Structure(object, array), conditional expression, iteration



### DOM?

- HTML, XML 등과 같은 문서를 다루기 위한 언어 독립적인 문서 모델 인터페이스
- 문서를 구조화하고 구조화된 구성 요소를 하나의 객체로 취급하여 다루는 논리적 트리 구조
- 단순한 속성 접근, 메서드 활용 뿐만 아니라 프로그래밍 언어적 특성을 활용한 조작 가능
- 주요 객체
  - window 
    - DOM 을 표현하는 최상위 객체
  - document
    - 페이지 콘텐츠의 Entry Point
    - < body> 등과 같은 다른 요소 포함
  - navigator, location, history, screen



#### DOM 해석

- Parsing 
  - 구문 분석, 해석
  - 브라우저가 문자열을 해석하여 DOM Tree로 만드는 과정



### BOM?

- Browser Object Model
- 자바스크립트가 브라우저와 소통하기 위한 모델
- 브라우저의 창이나 프레임을 추상화해서 프로그래밍적으로 제어
  - 버튼, URL 입력창, 타이틀 바 등 브라우저 윈도우 및 웹페이지 일부분을 제어



### DOM 조작

- DOM 조작 순서

  - 선택 (select)
  - 변경 (manipulation)

  ![Node properties: type, tag and contents](https://javascript.info/article/basic-dom-node-properties/dom-class-hierarchy.svg)



#### DOM 선택 - 선택 관련 메서드

- `Document.querySelector()`
  - 제공한 선택자와 일치하는 element 하나 선택
  - 제공한 CSS selector 를 만족하는 첫 번째 element 객체 반환 (없으면 null)
- `Document.querySelectorAll()`
  - 제공한 선택자와 일치하는 여러 element 선택
  - 매칭할 하나 이상의 셀렉터를 포함하는 유효한 CSS selector 를 인자(문자열)로 받음
  - 지정된 셀렉터에 일치하는 NodeList 반환
- `getElementById()`
- `getElementByTagName()`
- `getElementsByClassName()`



#### 선택 메서드별 반환 타입

- 단일 element
  - getElementById()
  - `querySelector()`
- HTMLCollection
  - getElementByTagName()
  - getElementByClassName()
- NodeList
  - `querySelectorAll()`



#### HTML Collection & NodeList

> 배열과 같이 각 항목을 접근하기 위한 인덱스 제공
>
> 유사 배열



- HTML Collection
  - name, id 속성으로 각 항목들에 접근 가능
- NodeList
  - **인덱스 번호**로만 각 항목들에 접근 가능
  - 단 HTML Collection 과 달리 배열에서 사용하는 for each 함수 및 다양한 메서드 사용 가능
- 둘다 Live Collection 으로 DOM 의 변경 사항을 실시간 반영하지만
- **querySelectorAll() 에 의해 반환되는 NodeList 는 Static Collection**



#### Collection

- Live Collection
  - 문서가 바뀔 때 실시간으로 업데이트
  - 변경사항을 실시간으로 collection 에 반영
  - HTML Collection, Node List
- static Collection
  - DOM 이 변경되어도 collection 내용에는 영향을 주지 않음
  - query Selector All 의 반환인 Node List



#### DOM 변경 - 변경 관련 메서드

- `Document.createElement()`
- `ParentNode.append()`
  - 특정 부모 노드의 자식 노드 리스트 중 마지막 자식 다음에 Node 객체나 ComString 추가 (반환 값 없음)
  - **여러 개**의 Node 객체, DOM String 을 추가할 수 있다 
- `Node.appendChild()`
  - **한 노드**를 특정 부모 노드의 자식 노드 리스트 중 마지막 자식으로 삽입 (**Node 만 추가 가능**)
  - 만약 주어진 노드가 이미 문서에 존재하는 다른 노드를 참조한다면 새로운 위치로 이동
- `ChildNode.remove()`
  - 이를 포함하는 트리로부터 특정 객체를 제거
- `Node.removeChild()`
  - DOM 에서 자식 노드를 제거하고 제거 된 노드를 **반환**
  - Node 는 인자로 들어가는 자식 노드의 부모 노드
  - 부모 노드를 알 때 지정된(특정된) 자식 요소를 제거 (부모 선택 + 자식 선택 후 조작)



#### DOM 변경 - 변경 관련 메서드 (속성)

- `Node.innerText`
  - 노드와 그 자손의 텍스트 콘텐츠(DOMString) 를 표현 : 해당 요소 내부의 Raw Text
  - 사람이 읽을 수 있는 요소만 남김
  - 줄바꿈을 인식하고 숨겨진 내용을 무시하는 등 최종적으로 스타일링이 적용된 모습
- `Element.innerHTML`
  - 요소(element) 내에 포함된 HTML 마크업 반환
  - XSS 공격에 취약점이 있으므로 사용 주의
- `Element.setAttribute(name, value)`
  - 지정된 요소의 값을 설정
  - 속성이 이미 존재하면 업데이트, 존재하지 않으면 지정된 이름과 값으로 추가
- `Element.getAttribute()`
  - 해당 요소의 지정된 값 반환
  - 주어진 속성이 존재하지 않는다면 null 이나 "" 반환
  - 인자는 값을 얻고자 하는 속성의 이름





## Event

- 네트워크 활동 혹은 사용자와의 상호작용 같은 사건의 발생을 알리기 위한 객체
- 이벤트는 마우스를 클릭하거나 키보드를 누르는 등 사용자 행동에 의해 발생 할 수도 있고
- 특정 메서드를 호출하여 프로그래밍적으로도 만들어 낼 수 있다
- 이벤트 처리기 (Event-handlers)
  - EventTarget.`addEventListener()`
  - 해당 메서드를 통해 다양한 요소에 이벤트를 붙일 수 있다
  - `removeEventListener()` 를 통해 이벤트 제거 가능하다



- Event 기반 인터페이스
  - AnimationEvent, ClipboardEvent, DragEvent
- UIEvent
  - 간단한 사용자 인터페이스 이벤트
  - Event 의 상속을 받음
  - MouseEvent, KeyboardEvent, InputEvent, FocusEvent 등의 부모 객체 역할

https://developer.mozilla.org/en-US/docs/Web/API/UIEvent



## Event handler

- EventTarget.addEventListener()
- 지정한 이벤트가 대상에 전달될 때 마다 호출할 함수를 설정
- 이벤트를 지원하는 모든 객체 대상으로 지정 가능 (최상위 객체이므로)
  - Element
  - Document
  - Window
- `target.addEventListener(type, listener[, option])`
  - **type**: 반응할 특정 이벤트 유형 (대소문자 구분 문자열)
  - **listener**: 지정된 타입의 이벤트가 발생 했을 때 알림을 받는 객체
    - 이벤트가 발생했을 때 할 일, 함수
    - EventListener 의 인터페이스 혹은
    - JS function 객체 (콜백 함수) 여야 한다
    - 콜백 함수란, 나중에 호출되는 함수를 말한다
    - 개발자가 함수의 인자로 콜백 함수를 등록하고
    - 어떤 이벤트가 발생했거나 특정 시점에 도달했을 때 시스템에서 호출하는 함수를 말한다.
    
    

```javascript
const myBtn = document.querySelector("#my-button")
myBtn.addEventListener("click", alertMessage)
```



특정 이벤트가 발생하면, 할 일을 등록하자

https://developer.mozilla.org/en-US/docs/Web/Events





### prevent Default()

- 현재 이벤트의 기본 동작을 중단시킨다.

- 태그의 기본 동작

  - a 태그는 클릭 시 페이지 이동이 기본
  - form 태그는 폼 데이터 전송이 기본

- 이벤트의 전파를 막지 않고 이벤트의 기본 동작만 중단한다

  

```javascript
// 클릭 이벤트 자체는 발생하지만 체크박스에 체크가 되지는 않는다.
const checkBox = document.querySelector("#my-checkbox")
    checkBox.addEventListener("click", function(){
      event.preventDefault()
    })

```



**언제 쓰나요?**





## ECMA 6



### ECMA?

- 정보 통신에 대한 표준을 제정하는 비영리 표준화 기구
- ECMAScript 는 ECMA 에서 ECMA-262 규격에 따라 정의한 언어
- ECMAScript6 는 6번째 표준 명세



### 세미콜론

- 자바스크립트는 세미콜론을 선택적으로 사용가능
- 세미콜론이 없을 경우, ASI 에 의해 자동으로 세미콜론이 삽입된다



### 코딩 스타일 가이드

- 합의된 원칙과 일관성
- 코드의 품질에 직결되는 중요한 요소
- 가독성, 유지 보수, 팀원과의 커뮤니케이션 등 개발 과정 전체에 영향을 미친다
  - Airbnb Javascript Style Guide (중심)
  - Google Javascript Style Guide
  - standardJS

https://github.com/airbnb/javascript





## 변수와 식별자 개념

### 식별자 정의와 특징

- 식별자는 변수를 구분할 수 있는 변수명
- 반드시 문자, 달러 또는 밑줄로 시작
- 대소문자 구분 하며 클래스 명 외에는 모두 소문자로 시작
- 예약어 사용 불가능



### 식별자 작성 스타일

- 카멜 케이스 (camelCase, lower-camel-case)
  - 변수, 객체, 함수에 사용
- 파스칼 케이스(PascalCase, upper-camel-case)
  - 클래스, 생성자
- 대문자 스네이크 케이스(SNAKE_CASE)
  - 모든 단어 대문자, 단어 사이에 언더스코어
  - 상수 (constants) 사용
  - 변경될 가능성이 없는 값



### 변수 선언 키워드 (let, const)

#### let

- 재할당 할 수 있는 변수 선언 시 
- 변수 재선언 불가능
- 블록 스코프
- 재할당 O, 재선언 X

#### const

- 재할당 할 수 없는 변수 선언 시 사용
- 변수 재선언 불가능
- 블록 스코프
  - if, for, 함수 등의 중괄호 내부를 가리킴
  - 블록 스코프를 가지는 변수는 블록 바깥에서 접근 불가능
- 재할당 X, 재선언 X



##### 선언, 할당, 초기화

- 선언 (Declaration) 
  - 변수를 생성하는 행위 또는 시점
- 할당 (Assignment)
  - 선언된 변수에 값을 저장하는 행위 또는 시점
- 초기화(Initialization)
  - 선언된 변수에 처음으로 값을 저장하는 행위 또는 시점



##### var

- ES6 이전에 변수를 선언할 때 사용되던 키워드
- var 로 선언한 변수는 재선언 및 재할당 모두 가능
- 호이스팅 되는 특성 때문에 const, let  사용 권장
  - 변수를 선언 이전에 참조할 수 있는 현상
  - 선언을 끌어올려 변수 선언 이전의 위치에서 접근 시 undefined 반환
- 함수 스코프
  - 함수의 중괄호 내부를 가리킴
  - 함수 스코프를 가지는 변수는 함수 바깥에서 접근 불가능

