# TODAY I LEARNED

## Learned

### 조건부 object

속성을 조건부로 추가하기.(optional object property)

lastName 속성 자체(key)를 조건부로 추가할 때, spread가 매우 유용하게 쓰일 수 있습니다.

```javascript
const lastName = prompt("Last name : ");
const user = {
username: "nico",
age: 24,
...(lastName !== "" && { lastName }),
// lastName: lastName !== "" ? lastName : undefined,
};

console.log(user);
// 출력
// lastName에 무언가를 입력했을 경우 : 해당 객체에 lastName속성 및 할당 값 생성
// lastName에 아무것도 입력하지 않았을 경우 : 해당 객체에 lastName 속성 생성하지 않음.
```

이 때, lastName을 {}로 감싸주어야 하는 것에 주의해야합니다. (spread로 전개하려면 데이터가 object이어야 하므로)

