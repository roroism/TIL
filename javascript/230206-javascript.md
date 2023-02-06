# TODAY I LEARNED

## Learned

### Value Shorthands

변수명 단축
변수 이름이 같다면 단축속성명을 사용할 수 있습니다.

### Swapping and Skipping

자주 쓰는 몇가지 트릭

#### variable swapping

서로 다른 변수의 값을 교환합니다.

```javascript
let mon = "Sat";
let sat = "Mon";

[sat, mon] = [mon, sat];

console.log(mon, sat);
// 출력
// Mon, Sat
```

#### Skipping

array에서 필요한 index만 변수로 할당할 수 있습니다.

```javascript
const days = ["mon", "tue", "wed", "thu", "fri"];
const [, , , thu, fri] = days;

console.log(thu, fri);
```

### Introduction to Spread

Spread 구문
Spread 구문을 사용하면 배열, 문자열, 객체 등 반복 가능한 객체 (Iterable Object)를 개별 요소로 분리할 수 있습니다.

```javascript
const arr1 = [0, 1, 2];
const arr2 = [3, 4, 5];
arr1 = [...arr1, ...arr2]; // arr1 은 이제 [0, 1, 2, 3, 4, 5]
```

