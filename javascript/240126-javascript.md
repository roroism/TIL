# TODAY I LEARNED

## 복습

### 매개변수 패턴

#### 기본값

```javascript
function sum(a, b) {
  return a + b;
}

console.log(sum(1, 2)); // 3
console.log(sum(7)); // NaN // 두번째 매개변수에는 값이 들어가지 않음


// 기본값 지정
function sum(a, b = 1) {
  return a + b;
}

```

#### 구조 분해 할당(객체)

```javascript
const user = {
  name: 'USER1',
  age: 85,
}

function getName(user) {
  const { name } = user;
  return user.name;
}

console.log(getName(user)); // USER1

// 또는 아래처럼 작성 가능
function getName({ name }) {
  return user.name;
}

// 기본값 지정을 활용 가능
function getEmail({ email = '이메일이 없습니다.'}) {
  return user.email
}

console.log(getEmail(user)); // undefined가 나오지 않고, '이메일이 없습니다.'가 출력됨.
```

#### 구조 분해 할당(배열)

```javascript
const fruits = ['Apple', 'Banana', 'Cherry'];
const numbers = [1, 2, 3, 4, 5, 6, 7];

function getSecondItem([a, b, c]) {
  return b;
}

console.log(getSecondItem(fruits)); // Banana

// 또는 아래처럼 사용하지 않는 매개변수는 생략하여 작성 가능
function getSecondItem2([, b]) {
  return b;
}

console.log(getSecondItem2(numbers)); // 2
```

#### 나머지 매개변수(전개 연산자)

**개념 1**

```javascript
// 들어오는 인수들을 순서대로 받아서 배열로 저장하게 됩니다.
function sum(...rest) {
  console.log(rest);
}

console.log(sum(1, 2)); // [1, 2]
console.log(sum(1, 2, 3, 4)); // [1, 2, 3, 4]
console.log(sum(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)); // [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

**개념 2**

```javascript
// 들어오는 인수들을 순서대로 받아서 배열로 저장하게 됩니다.
// 첫번째 인수(a)와 두번째 인수(b)를 제외한 나머지인수를 rest로 받아서 배열로 저장합니다.
function sum(a, b, ...rest) {
  console.log(rest);
}

console.log(sum(1, 2)); // []
console.log(sum(1, 2, 3, 4)); // [3, 4]
console.log(sum(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)); // [3, 4, 5, 6, 7, 8, 9, 10]
```

**실습 1**

```javascript
// 들어오는 인수들을 순서대로 받아서 배열로 저장하게 됩니다.
// 첫번째 인수(a)와 두번째 인수(b)를 제외한 나머지인수를 rest로 받아서 배열로 저장합니다.
function sum(...rest) {
  rest.reduce(function (acc, cur) {
    return acc + cur
  }, 0);
}

console.log(sum(1, 2)); // 3
console.log(sum(1, 2, 3, 4)); // 10
console.log(sum(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)); // 55
```

**arguments**
- 위처럼 나머지 매개변수를 이용해서 인수를 받지 않아도, 들어오는 모든 인수를 가지고 있는 이미 선언되어있는 객체가 있다.

```javascript
// 들어오는 인수들을 순서대로 받아서 배열로 저장하게 됩니다.
// 첫번째 인수(a)와 두번째 인수(b)를 제외한 나머지인수를 rest로 받아서 배열로 저장합니다.
function sum(...rest) {
  console.log(arguments);
  rest.reduce(function (acc, cur) {
    return acc + cur
  }, 0);
}

console.log(sum(1, 2)); // 3
console.log(sum(1, 2, 3, 4)); // 10
console.log(sum(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)); // 55
```

- arguments는 함수안에서 언제든지 사용할 수 있는 객체입니다.
- arguments는 배열이 아니고 유사배열(Array-Like)이기 때문에 reduce와 같은 배열함수를 사용할 수 없습니다.

