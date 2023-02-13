# TODAY I LEARNED

## Learned

### Using Promises

#### then

자바스크립트에 promise 가 끝난 이후의 명령어를 전달하려면,
명령이 끝나고 나서 값을 돌려달라고 명령어를 내려야 합니다.

```javascript
const amISexy = new Promise((resolve, reject) => {
	setTimeout(resolve, 3000, "Yes you are");
});

amISexy.then(value => console.log(value));
```

#### catch

promise에 error가 생기면 catch로 잡을 수 있습니다.
먼저 reject로 에러를 발생시켜봅니다.

```javascript
const amISexy = new Promise((resolve, reject) => {
	setTimeout(reject, 3000, "Yes you ugly");
});

amISexy
    .then(result => console.log(value))
    .catch(error => console.log(value));
// 출력
// You are ugly
```

then과 catch는 순서대로 실행되지 않고, 각각 다른 상황에서 실행됩니다. 한 쪽이 실행되면 다른 한 쪽은 실행되지 않습니다.

### Chaining Promises

가끔은 Promise를 chaining으로 사용해야 할 때가 있습니다.
예를 들어 API로 가서 암호화된 data를 받고, 암호화된 data를 풀고, 파일로 저장할 때, 총 then을 3번 사용하고 이를 순서대로 이어주어야 합니다.
모든 then은 서로의 순서가 끝나기만을 기다립니다.

```javascript
const amIsexy = new Promise((resolve, reject) => {
    resolve(2);
});

amIsexy
    .then(number => {
        console.log(number * 2);
    })
    .then(othernumber => {
        console.log(othernumber);
    });
// 결과
// 4
// undefined
```

promise들을 엮고 싶을 때는 이전의 then에서 return 값이 있어야 합니다.
위에서 첫번째 then에서 return이 없기 때문에 undefined를 반환하여 다음 then에 전달되었습니다.

아래처럼 return값을 다음 then에 전달하면..

```javascript
const amIsexy = new Promise((resolve, reject) => {
    resolve(2);
});

amIsexy
    .then(number => {
        console.log(number * 2);
        return number * 2;
    })
    .then(othernumber => {
        console.log(othernumber * 2);
    });
// 결과
// 4
// 8
```

function으로 묶어서 반복하는 경우..

```javascript
const amIdouble = new Promise((resolve, reject) => {
    resolve(2);
});

const timesTwo = (numbertwo) => numbertwo * 2;

amIdouble
    .then(timesTwo)
    .then(timesTwo)
    .then(timesTwo)
    .then(timesTwo)
    .then(lastNumber => console.log(lastNumber));
// 결과
// 64
```

