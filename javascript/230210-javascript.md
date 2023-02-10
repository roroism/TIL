# TODAY I LEARNED

## Learned

### For of Loop

for...of 명령문은 반복가능한 객체 (Array, Map, Set, String, TypedArray, arguments 객체, NodeList 등을 포함)에 대해서 반복하고 각 개별 속성값에 대해 실행되는 문이 있는 사용자 정의 반복 후크를 호출하는 루프를 생성합니다.
먼저..

#### for 문을 사용할 경우 예시..

```javascript
const friends = ["nico", "lynn", "ha", "hu"];

for (let i = 0; i < friends.length; i++) {
	console.log(`i love my friend ${friends[i]}`);
}
```

전체 array반복을 할 경우에는 for 보다는 for of 구문이 더 간결합니다.

#### forEach를 사용할 경우 예시..

```javascript
const friends = ["nico", "lynn", "ha", "hu"];

const addHeart = (c, i, a) => console.log(c, i, a);
// 첫번째 인자 : item, 두번째 인자 : index, 세번째 인자 : 현재 array

friends.forEach(addHeart);
```

#### for of 를 사용할 경우...

```javascript
const friends = ["nico", "lynn", "ha", "hu"];

for (const friend of friends) {
	console.log(friend);
}
// 출력
// nico
// lynn
// ha
// hu
```

일반 for문을 사용할 때보다 더 간결해졌습니다.

##### 특징

1. For of 에서는 const로 선언할 지, let으로 선언할 지 선택할 수 있습니다. forEach에서는 안됨.

2. For of는 array에서만 동작하는 것이 아니라, iterable한 모든 것에서 동작합니다. (iterable하다 = 루프가 가능하다) 그래서 String, NodeList 등 에서도 동작합니다.(NodeList는 getElementsByClassName과 같은 함수의 결과물을 말합니다.) 아래 예시

```javascript
for (const letter of "Helloo this is very looooooong") {
	console.log(letter);
}
// 출력
// H
// e
// l
// l
// ......

// error
// forEach는 array에서만 사용 가능.
//"Helloo this is very looooooong".forEach()
```

3. 가장 좋은 점은 루프를 멈출 수도 있다는 점입니다. 아래 예시

```javascript
const friends = ["nico", "lynn", "Japan Guy", "Autumn", "Dal", "Mark", "Pipe", "Theo"];
// 위 Array를 루프하여 console.log를 출력하는 것은 forEach로도 할 수 있습니다.
// 하지만 특정한 값을 찾은 다음에 멈추려고 한다면 forEach로는 할 수 없습니다.
// 루프를 멈추고 싶다면 for of를 사용하면 됩니다.

for (const friend of friends) {
	if (friend === "Dal") {
		break;
	} else {
		console.log(friend);
	}
}
```

