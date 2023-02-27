# TODAY I LEARNED

## Learned

### Optional Chaining

optional chaining 연산자 (?.) 는 체인의 각 참조가 유효한지 명시적으로 검증하지 않고, 연결된 객체 체인 내에 깊숙이 위치한 속성 값을 읽을 수 있다.

?. 연산자는 . 체이닝 연산자와 유사하게 작동하지만, 만약 참조가 nullish (null 또는 undefined)이라면, 에러가 발생하는 것 대신에 표현식의 리턴 값은 undefined로 단락된다. 함수 호출에서 사용될 때, 만약 주어진 함수가 존재하지 않는다면, undefined를 리턴한다.

API 작업을 할 때 유용합니다. API를 통해서 가져온 데이터가
예상한 것을 (API 등이) 가지고 있는지 아닌지 확신할 수 없을 때 사용한다.

```javascript
const me = {
    name: "nico",
    profile: {
        email: "@something.com"
    }
}

console.log(me.profile.email);
// @something.com
```

가져오려는 속성에 접근하여 해당 값을 읽어올 수 있습니다.
하지만, 만약 해당 속성이 없는 데이터가 왔다면?

```javascript
const lynn = {
    name: "lynn",
}

console.log(lynn.profile.email);
// error
```

에러가 발생합니다.
이 같은 경우를 위해서 optional chaining 연산자가 존재합니다.

```javascript
console.log(lynn?.profile?.email);
```

optional chainging 연산자를 사용하지 않고, 표현한다면 아래처럼 매우 복잡하고 길게 작성해주어야합니다.

```javascript
console.log(lynn && lynn.profile && lynn.profile.email);
```

정리한다면,
어떤 object가 우리가 예상한 것을 가지고 있는지 아닌지 확신할 수 없을 때 사용하면 좋습니다.
대부분 API를 사용하는 대부분의 작업에서 사용될 것입니다.

### padStart and padEnd

1. padStart
padStart() 메서드는 현재 문자열의 시작을 다른 문자열로 채워, 주어진 길이를 만족하는 새로운 문자열을 반환합니다. 채워넣기는 대상 문자열의 시작(좌측)부터 적용됩니다.

2. padEnd
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

