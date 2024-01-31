# TODAY I LEARNED

## 복습

### this

- 일반함수와 화살표 함수에서 각각 다른 방식으로 해석이 됩니다.
- 일반 함수의 this는 호출 위치에서 정의.
- 화살표 함수의 this는 자신이 선언된 함수(렉시컬) 범위에서 정의.

#### 예시

##### 일반 함수안에서 this 호출

**this 키워드를 사용.**

```javascript
// 일반 함수의 this는 호출 위치에서 정의.

const user = {
  firstName: 'first',
  lastName: 'last',
  age: 85,
  getFullName: function () {
    this.firstName;
    this.lastName;
    return `${this.firstName} ${this.lastName}`;
  }
}

console.log(user.getFullName()); // first last
```

**user 객체로 수정.**

```javascript
// 일반 함수의 this는 호출 위치에서 정의.

const user = {
  firstName: 'first',
  lastName: 'last',
  age: 85,
  getFullName: function () {
    return `${user.firstName} ${user.lastName}`;
  }
}

console.log(user.getFullName()); // first last
```

- 위 코드에서 일반함수안에서 this를 사용한 것과 user를 사용한 것과 결과 값은 같습니다.
- 즉, this는 user 객체를 가리킵니다.
- '일반 함수의 this는 호출 위치에서 정의.' 된다는 것은 getFullName 함수가 호출되는 곳은 user.getFullName() 이므로 getFullName()을 호출한 앞의 user객체 를 가리킵니다.

##### 화살표 함수안에서 this 호출

**this 키워드를 사용.**

```javascript
// 화살표 함수의 this는 자신이 선언된 함수(렉시컬) 범위에서 정의.

const user = {
  firstName: 'first',
  lastName: 'last',
  age: 85,
  getFullName: () => {
    return `${this.firstName} ${this.lastName}`;
  }
}

console.log(user.getFullName()); // undefined undefined
```

- 자신이 선언된 함수(레시컬) 범위 -> 여기서 '자신'은 getFullName함수를 가리킵니다.
- 즉, 화살표 함수 안의 this는 그 화살표 함수가 선언된, 감싸는 외부 함수 범위 안에서 정의됩니다.
- 하지만, 위 예제에서는 this가 선언된 화살표 함수를 감싸는 외부 함수가 없습니다. 그래서 결과는 undefined가 출력되었습니다.


그럼 이번에는 this가 사용된 화살표 함수를 감싸는 외부 함수를 만들어보겠습니다.

```javascript
// 화살표 함수의 this는 자신이 선언된 함수(렉시컬) 범위에서 정의.

function user() = {
  this.firstName = 'first2';
  this.lastName = 'last2';
  
  return {
    firstName: 'first',
    lastName: 'last',
    age: 85,
    getFullName: () => {
      return `${this.firstName} ${this.lastName}`;
    }
  }
}

const u = user();
console.log(u.getFullName()); // first2 last2
```

- 외부 함수에 정의한 firstName과 lastName이 출력되었습니다.

만약 getFullName의 함수를 다시 일반 함수로 변경한다면?

```javascript
// 화살표 함수의 this는 자신이 선언된 함수(렉시컬) 범위에서 정의.

function user() = {
  this.firstName = 'first2';
  this.lastName = 'last2';
  
  return {
    firstName: 'first',
    lastName: 'last',
    age: 85,
    getFullName: function () {
      return `${this.firstName} ${this.lastName}`;
    }
  }
}

const u = user();
console.log(u.getFullName()); // first last
```

- getFullName()이 호출된 곳 기준이기 때문에 u의 firstName과 lastName이 출력됩니다.

