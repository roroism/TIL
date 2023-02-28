# TODAY I LEARNED

## Learned

### padStart and padEnd

1. padStart
https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/padStart
padStart() 메서드는 현재 문자열의 시작을 다른 문자열로 채워, 주어진 길이를 만족하는 새로운 문자열을 반환합니다. 채워넣기는 대상 문자열의 시작(좌측)부터 적용됩니다.

2. padEnd
https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/padEnd
padEnd() 메서드는 현재 문자열에 다른 문자열을 채워, 주어진 길이를 만족하는 새로운 문자열을 반환합니다. 채워넣기는 대상 문자열의 끝(우측)부터 적용됩니다.

#### 예시

```javascript
let hours = 12;
let minutes = 3;
let seconds = 2;

console.log(`${hours}h:${minutes}m:${seconds}s`);
// 12h:3m:2s
// 원하는 출력
// 12h:03m:02s

minutes = String(minutes).padStart(2, "0");
console.log(`${hours}h:${minutes}m:${seconds}s`);
// 12h:03m:02s
```

```javascript
"5".padStart(5, "xxxxx");
// "xxxx5"

"5".padEnd(5, "xxxxx");
// "5xxxx"

"1".padStart(2, "0").padEnd(3, "s");
// "01s"
```

참고로 결과를 반환할 뿐 원본 값은 변화시키지 않습니다.

### trim, trimStart trimEnd

trim : 비어있는 공간을 없애줍니다. (단어 사이의 공백 제외)

```javascript
"          hello".trimStart();
// "hello"

"          hello                ".trimEnd();
// "          hello"

"          hello                ".trim();
// "hello"
```

.trim()은 원본 string 자체를 수정하지 않습니다.

