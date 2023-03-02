# TODAY I LEARNED

## Learned

### Array.sort

배열을 정렬해줍니다.
새로운 배열로 반환하지 않고, 원 데이터를 변경합니다.

공식문서
https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/sort

compareFunction(a, b)가 0보다 작으면, a 가 b 보다 작다는 의미입니다. `(a<b)` 즉, a가 먼저옵니다.
a, b 가 같으면 0을 반환합니다.
0보다 크면 a가 b보다 큽니다. `(a>b)` b를 a보다 낮은 인덱스로 소트합니다.

참고로 비교 함수는 무조건 무엇이라도 반환해야 합니다.

```javascript
const fruits = ["apple", "strawberry", "avocado"];



const sortFruitByLength = (fruitA, fruitB) => {
    return fruitA.length - fruitB.length
    // 예시
    // strawberry글자수 - avocado글자수
    // 10 - 7 = 3
}

console.log(fruits.sort(sortFruitByLength));
// ['apple', 'avocado', 'strawberry']
```

#### 유용한 사용법

객체가 배열의 item인 경우..

```javascript
const people = [
    {
        name: "nico",
        age: 12
    },
    {
        name: "lynn",
        age: 22
    }
];



const orderPeopleByAge = (personA, personB) => {
    return personA.age - personB.age
}

console.log(people.sort(orderPeopleByAge));
// [ { name: 'nico', age: 12 }, { name: 'lynn', age: 22 } ]
```

### Promise allSettled

promise.allSettled는 promise.all 과는 다릅니다.
promise.all은 모든 비동기 함수가 성공해야 resolve를 실행하고, 하나라도 실패하면 reject되지만,
promise.allSettled는 모든 promise가 성공할 필요는 없습니다.

1. promise.all

```javascript
const p = Promise.all([
    fetch("https://yts.mx/api/v2/list_movies.json"),
    fetch("https://yts.mx/api/v2/list_movies.json"),
    fetch("https://yts.mx/api/v2/list_movies.json"),
    fetch("https://yts.mx/api/v2/list_movies.json"),
])
.then(response => console.log("success!", response))
.catch(e => console.log("my error:", e));

// 모두 성공시
// success! [ Response {}, Response {}, Response {}, Response {} ]

// 하나라도 실패시
// error: 에러메세지
```

2. promise.allSettled

```javascript
const p = Promise.allSettled([
    fetch("https://yts.mx/api/v2/list_movies.json"),
    fetch("https://yts.mx/api/v2/list_movies.json"),
    fetch("https://yts.mx/api/v2/list_movies.json"),
    fetch("https://yts.mx/api/v2/list_movies.json"),
])
.then(response => console.log("success!", response))
.catch(e => console.log("my error:", e));

// 모든 비동기 처리가 완료되면
// success! [ 
// { status: 'fulfilled', value: Response {} }, 
// { status: 'fulfilled', value: Response {} }, 
// { status: 'fulfilled', value: Response {} }, 
// { status: 'fulfilled', value: Response {} } ]
// 실패한 비동기는 status를 'rejected'로 출력하고, 
// value속성 대신 reason 속성과 에러내용이 추가됩니다.

// 실패한 비동기의 출력 객체 예시
// { status: 'rejected', reason: 에러메세지 }
```

성공시 출력값이 all 과는 다르게 Object로 출력됩니다.
이 출력값으로 유추해보면 promise.allSettled 은 모든 promise가 성공하지 않아도 되는 이유입니다. (에러가 있든 없든 resolve 됩니다.) 모두성공했는지는 상관없이 단지 모든 promise가 끝나기를 기다려서 resolve 하고, 에러가 발생한 비동기만 status의 값을 fulfilled가 아닌 rejected로 출력합니다.

#### 정리

Promise.allSettled
모든 promise가 잘 작동하는지 확인할 필요가 없으면 all 대신에 allSettled 을 사용하면 됩니다.
어느것이 잘 동작하고 어느 것이 동작하지 않는지 확인할 때 사용하면 유용합니다.

Promise.all
모든 promise가 동시에 동작하는지 확인하는 것이 중요하다면 all을 사용합니다.

