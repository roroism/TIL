# TODAY I LEARNED

## Learned

### 양식과 포커스 이벤트

- focus : 요소가 포커스를 얻었을 때
- blur : 요소가 포커스를 잃었을 때
- input : 값이 변경되었을 때
- change : 상태가 변경되었을 때
- submit : 제출 버튼을 선택했을 때
- reset : 리셋 버튼을 선택했을 때

#### 예시 코드

```html
  <!-- ... -->
  <style>
    form {
      padding: 10px;
      border: 4px solid transparent;
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
    }
    form.active {
      border-color: orange;
    }
  </style>
</head>
<body>
  <form>
    <input type="text" placeholder="ID" />
    <input type="password" placeholder="PW" />
    <button type="submit">제출</button>
    <button type="reset">초기화</button>
  </form>
</body>
<!-- ... -->
```

```javascript
// main.js
// Focus & Form Events

const formEl = document.querySelector('form');
const inputEls = document.querySelectorAll('input');

inputEls.forEach(el => {
  el.addEventListener('focus', () => {
    formEl.classList.add('active');
  });
  el.addEventListener('blur', () => {
    formEl.classList.remove('active');
  });
  el.addEventListener('change', event => {
    console.log(event.target.value);
  });
});

formEl.addEventListener('submit', event => {
  event.preventDefault();
  const data = {
    id: event.target[0].value,
    pw: event.target[1].value,
  }
  console.log('제출!', data);
});

formEl.addEventListener('reset', event => {
  console.log('리셋!');
});
```

#### 정리

- 이벤트
    - input : 값이 변경되었을 때(키보드를 입력할 때마다 동작합니다.)
    - change : 상태가 변경되었을 때(모든 값 입력을 끝내고 다른 요소로 포커스를 이동했을 때 동작합니다). 즉, 엘리먼트의 상태가 변경되었을 때 동작합니다.
- 제출 버튼(type='submit'인 버튼)을 클릭하면 form에 submit이라는 이벤트가 발생합니다.
- form요소에서는 submit 이벤트가 발생하면 페이작 새로고침되는 것이 기본동작입니다.
    - 페이지를 새로고침하는 기본 동작을 막기위해 event.preventDefault();를 사용합니다.

