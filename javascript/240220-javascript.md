# TODAY I LEARNED

## 복습

### 웹 컴포넌트란

- 캡슐화되고 웹 앱에 사용할 수 있는 재사용 가능한 커스텀 엘리먼트.

**custom element**

- UI에서 원하는대로 사용할 수 있는 사용자 정의 요소 및 해당 동작을 정의할 수 있는 javascript api 세트

**shadow dom**

- 메인 dom으로부터 독립적으로 렌더링되는 element를 추가하고 제어하기 위한 Javascript api 집합.
- 엘리멘트의 기능을 private하게 유지할 수 있어 다른 element와 충돌없이 script와 style을 작성할 수 있음.

**HTML 템플릿**

- `<template>`과 `<slot>`은 렌더링 페이지에 나타나지 않는 마크업 템플릿을 작성할 수 있게 해줌

#### 웹 컴포넌트 구현 접근법

1. 웹 컴포넌트 기능을 명시하는 클래스 생성
2. 새로운 커스텀 엘리먼트 등록
CustomELementRegistry.define()으로 등록함.
3. 필요한 경우 ELement.attachShadow()로 shadow DOM을 커스텀 엘리먼트에 추가함.
일반적인 DOM 메소드로 자식 엘리먼트, 이벤트 리스너 등을 shadow DOM에 추가함
4. 필요한 경우 <template>과 <slot>으로 HTML 템플릿을 정의함.

