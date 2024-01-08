# TODAY I LEARNED

## Learned

### 키보드 이벤트

- 키보드로 한글을 입력하면 브라우저는 입력된 한글을 처리하는 과정이 필요합니다.
- 특히, input요소에서 엔터키나 탭키 처럼 입력을 완료하는 키를 누르거나 혹은 keydown, keyup의 이벤트를 발생시키면 그 이벤트가 두 번 처리되는 현상이 나타납니다.
- 이는 한글 뿐만이 아니라 중국어나 일본어에서도 발생합니다.
- 이러한 CJK문자(한글,중국,일본어)는 브라우저에서 처리하는 과정이 한 단계가 더 필요하기 때문에 두 번의 결과가 출력됩니다.
- 이런 중간 처리과정을 event.isComposing 을 통하여 알 수 있습니다.

#### 예시 코드

```javascript
// main.js

// Keyboard Events

// keydown : 키를 누를 때
// keyup : 키를 땔 때

const inputEl = document.querySelector('input');

inputEl.addEventListener('keydown', event => {
  if (event.key === 'Enter') {
    console.log(event.isComposing);
    console.log(event.target.value); // 한글을 입력하면 두 번 처리됩니다.
  }
});
```

```javascript
// 더 나은 코드
inputEl.addEventListener('keydown', event => {
  if (event.key === 'Enter' && !event.isComposing) {
    console.log(event.isComposing);
    console.log(event.target.value); // 이제 한글을 입력해도 한 번만 처리 됩니다.
  }
});
```

#### 정리

- 키보드 이벤트를 다룰 때, 엔터나 탭키처럼 입력을 완료하는 코드과 한글 입력을 같이 사용한다면, 이벤트의 isComposing 속성을 같이 로직으로 처리하는 것이 필요합니다.

