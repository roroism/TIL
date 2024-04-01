# TODAY I LEARNED

## Learned

### 특정 브라우저 전용 프로퍼티

- `-moz-border-radius`, `-webkit-border-radius` 같이 브라우저 관련 접두사가 붙은 프로퍼티(browser-prefixed property) 역시 카멜 표기법을 사용하여 값을 설정할 수 있습니다.
- 대시(-)는 대문자를 의미합니다.

예시

```javascript
button.style.MozBorderRadius = '5px';
button.style.WebkitBorderRadius = '5px';
```

