# Web Programming Assignment

**이름:** 방하영  
**학번:** 22500326  

## Deployment
* **Vercel 배포 URL:** []

## Key Learning
1. **DOM 조작:** JavaScript를 이용해 HTML 요소를 동적으로 생성하고(createElement) 화면에 렌더링하는 방법
2. **Event 처리:** addEventListener를 활용해 클릭 이벤트와 폼 데이터 추가/수정/삭제 동작을 제어하는 방법
3. **Array 메서드 활용:** 데이터베이스 대신 배열(Array)과 filter(), forEach() 등을 사용하여 데이터를 관리하고 상태를 유지하는 방법

## CRUD Service
* **주제:** 독서 관리 서비스 (My Book List)
* **사용 Field (7개):** id, title, author, genre, year, rating, status
* **구현 방법:**
  * **Create:** 입력 폼의 값들을 가져와 객체로 묶은 뒤, `Date.now()`로 고유 ID를 부여하여 `books` 배열에 `push()`
  * **Read:** `books` 배열을 순회하며 `createElement`로 `<li>` 태그를 생성하고, `innerText`로 값을 할당하여 화면에 `render()`
  * **Update:** [수정] 버튼 클릭 시 해당 객체의 데이터를 폼에 불러오고 `editId`에 현재 수정 중인 ID를 저장. 이후 [수정 완료] 버튼을 누르면 배열을 순회하여 조건에 맞는 객체의 값을 갱신
  * **Delete:** [삭제] 버튼 클릭 시 `confirm()`으로 확인 절차를 거친 후, `filter()` 함수를 사용해 해당 ID를 제외한 새 배열로 덮어쓰고 화면을 다시 렌더링

## JavaScript 기능 설명
* `document.querySelector()`: 특정 ID나 클래스 등 선택자와 일치하는 HTML 요소를 자바스크립트로 가져올 때 사용
* `addEventListener()`: 버튼 클릭 등 특정 이벤트가 발생했을 때 실행할 함수를 등록
* `document.createElement()`: 새로운 HTML 태그(li, button 등)를 메모리상에 동적으로 생성
* `appendChild()`: 생성한 HTML 요소를 부모 요소의 자식으로 화면에 추가
* `Array.filter()`: 배열의 요소 중 특정 조건(현재 삭제하려는 ID와 다른 요소)을 만족하는 요소들만 모아 새로운 배열을 반환
* `Date.now()`: 현재 시간 기준 밀리초를 반환하여 데이터 추가 시 고유한 식별자(ID)로 사용

## AI / Search Usage
* **Tool:** ChatGPT
* **Purpose:** CRUD 기능별 로직 구현 및 데이터 유효성 검사(Validation) 코드 작성 참고
* **Used:** Update 상태와 Create 상태를 구분하기 위한 `editId` 변수 활용법, `filter()`를 이용한 Delete 기능 구현 구조, 평점 숫자 범위 제한 Validation 등에 적용
* **What I Learned:** 화면의 DOM만 지우는 것이 아니라, 배열 데이터를 먼저 수정하고 전체를 다시 렌더링(`render()`)하는 방식이 데이터 동기화에 필수적이라는 것을 배움

## Problem & Solution
* **Problem:** [수정 시 입력창에 이전 데이터가 남거나, 빈 값이 배열에 그대로 들어가는 문제가 있었음]
* **Solution:** [조건문(if)과 `trim()`을 사용해 공백 입력을 막고, 데이터 처리(Create/Update)가 끝난 후 입력창의 `value`를 빈 문자열("")로 초기화하여 해결함]

## Reflection
* **새롭게 알게 된 점:** [서버 없이도 배열과 DOM 조작만으로 하나의 완전한 웹 서비스처럼 보이게 만들 수 있다는 점이 흥미로웠음]
* **궁금한 점:** [새로고침 했을 때 기존에 새롭게 추가했던 내용이나 수정 부분이 날아가지 않게 하는 방법을 알고싶음]