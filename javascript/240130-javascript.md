# TODAY I LEARNED

## 복습

### 재귀

- 재귀 (Recursive)
- 함수 안에서 함수 자기 자신을 다시 호출해서 사용하는 방법을 의미합니다.

```javascript
// 재귀 함수.
// 아래 함수는 무한 동작합니다.
const a = () => {
  console.log('A');
  a();
}

a();
```

재귀는 기본적으로 무한 동작하기 때문에, 필요에 따라서 멈춰줄 수 있어야 합니다.

```javascript
// 재귀 함수.
let i = 0;
const a = () => {
  console.log('A');
  i += 1;
  if (i < 4) {
    a();
  }
}

a();

// 출력결과
// A
// A
// A
// A
```

**예제**

```javascript
const userA = { name: 'A', parent: null };
const userB = { name: 'B', parent: userA };
const userC = { name: 'B', parent: userB };
const userD = { name: 'B', parent: userC };

const getRootUser = user => {
  if (user.parent) {
    return getRootUser(user.parent);
  }
  return user;
}

console.log(getRootUser(userD)); // { name: 'A', parent: null }
console.log(getRootUser(userC)); // { name: 'A', parent: null }
console.log(getRootUser(userB)); // { name: 'A', parent: null }
console.log(getRootUser(userA)); // { name: 'A', parent: null }
```

재귀 함수는 무한으로 반복 실행하면서 특정 조건을 찾을 수 있는 구조이기 때문에 종종 아주 유용하게 사용할 수 있습니다.

