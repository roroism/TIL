# TODAY I LEARNED

## Learned

### 클로저(Closure)

- 함수가 선언될 때의 유효범위(렉시컬 범위)를 기억하고 있다가,
- 함수가 외부에서 호출될 때 그 유효범위의 특정 변수를 참조할 수 있는 개념을 말합니다.

#### 개념 이해

**예시 코드 1**

```javascript
function createCount() {
  let a = 0;
  return function () {
    return a += 1;
  }
}

const count = createCount();

console.log(count()); // 1
console.log(count()); // 2
console.log(count()); // 3
```

- createCount(외부 함수)의 내부의 함수를 클로저 함수라고 합니다.
- 클로저 함수가 a를 참조하므로 외부 함수가 종료되어도, 변수a는 사라지지 않고 a의 값은 계속 유지되어 저장됩니다.
- 그래서 count()를 호출할 때 마다 return 값이 0이 아닌, 이전 a 값을 참조하여 계산된 결과를 리턴합니다.

위 코드는 마치 아래 코드처럼 전체 영역에서 a를 선언하여 사용하는 것과 같은 결과를 보여줍니다.

```javascript
let a = 0;

function createCount() {
  return function () {
    return a += 1;
  }
}

const count = createCount();

console.log(count()); // 1
console.log(count()); // 2
console.log(count()); // 3
```

하지만 위처럼 전체 영역에서 선언하여 사용하게 된다면,

- 일단 재사용이 어렵고,
- createCount라는 함수와 변수 a를 따로 관리해야 합니다.

**예시 코드2**

```javascript
function createCount() {
  let a = 0;
  return function () {
    return a += 1;
  }
}

const count1 = createCount();

console.log(count1()); // 1
console.log(count1()); // 2
console.log(count1()); // 3

const count2 = createCount();

console.log(count2()); // 1
console.log(count2()); // 2
```

createCount()를 한번 더 호출하여 변수count2에 할당하여 사용하면 count1과 count2는 각각 다른 변수를 사용하게 됩니다. 여기서 알 수 있듯이 createCount는 일종의 '함수 공장' 과 같은 역할을 보여줍니다.

이처럼 클로저를 사용하여 createCount라는 함수를 관리하게 된다면, 필요에 따라서 createCount를 호출할 때 마다, 함수 내부에서 a변수를 계속 활용할 수 있습니다.

#### 실습 예시

index.html

```html
<body>
  <h1>Hello world!</h1>
  <h2>Hello world!</h2>
</body>
```

main.js

```javascript
const h1El = document.querySelector('h1');
const h2El = document.querySelector('h2');

// 별도의 상태 관리가 필요!
let h1IsRed = false;
let h2IsRed = false;

h1El.addEventListener('click', event => {
  h1IsRed = !h1IsRed;
  h1El.style.color = h1IsRed ? 'red' : 'black';
});

h2El.addEventListener('click', event => {
  h2IsRed = !h2IsRed;
  h2El.style.color = h2IsRed ? 'red' : 'black';
});
```

위처럼 반복되는 로직과 별도로 관리되는 상태값을 클로저를 이용하여 아래처럼 바꿀 수 있습니다.

main.js

```javascript
const h1El = document.querySelector('h1');
const h2El = document.querySelector('h2');

// 별도의 상태 관리가 필요!
// let h1IsRed = false;
// let h2IsRed = false;

// h1El.addEventListener('click', event => {
//   h1IsRed = !h1IsRed;
//   h1El.style.color = h1IsRed ? 'red' : 'black';
// });

// h2El.addEventListener('click', event => {
//   h2IsRed = !h2IsRed;
//   h2El.style.color = h2IsRed ? 'red' : 'black';
// });

// 하나의 함수로 정리!
const createToggleHandler = () => {
  let isRed = false;
  return event => {
    isRed = !isRed;
    event.target.style.color = isRed ? 'red' : 'black';
  }
};
h1El = addEventListener('click', createToggleHandler());
h2El = addEventListener('click', createToggleHandler());
```

