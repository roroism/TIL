# TODAY I LEARNED

## Learned

### TransitionEnd 이벤트와 AnimationEnd 이벤트

- CSS3에서는 transition, animate 속성을 부여하여 애니메이션 효과를 줄 수 있습니다.
- 이벤트 리스너에 이벤트를 등록함으로써 transition, animate 애니메이션 효과가 완료된 후 이벤트를 호출할 수 있습니다.

#### TransitionEnd

- transitionend는 transition 효과가 완료된 후 이벤트를 발생시킵니다.

```javascript
const dom = document.getElementById('dom');
dom.addEventListener('transitionend', function() {
  console.debug('transitoinend');
});
```

#### AnimationEnd

- animationend는 animate 효과가 완료된 후 이벤트를 발생시킵니다.

```javascript
const dom = document.getElementById('dom');
dom.addEventListener('animationend', function() {
  console.debug('animationend');
});
```

