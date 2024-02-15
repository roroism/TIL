# TODAY I LEARNED

## 복습

### toLocaleDateString

`Date.prototype.toLocaleDateString()`

- options의 값은 "numeric"과 "long"을 사용합니다. "numeric"은 숫자 표기, "long"은 문자 표기입니다.

#### 사용 예

```javascript
const today = new Date();
  const dateString = today.toLocaleDateString("ko-KR", {
    year: "numeric",
    month: "long",
    day: "numeric",
  });
```

**출력**
`2022년 8월 24일`

