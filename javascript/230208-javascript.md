# TODAY I LEARNED

## Learned

### Rest Parameters

이를 가장 잘 설명할 방법은 끝도없는 parameter를 전달받는 함수를 만들어 보는 것입니다.(infinity parameters)

```javascript
const infiniteArgs = (...kimchi) => console.log(kimchi);

infiniteArgs("1", 2, true, "lalala", [1, 2, 3, 4]);

// 출력
// ["1", 2, true, "lalala", Array(4)]
```

이것이 rest 구문입니다.
rest는 모든 값을 하나의 변수로 축소(contract)시켜줍니다.
값들의 list를 취한다음에 하나의 변수 안에 넣어버립니다.

rest 구문을 아래처럼 유용하게 활용할 수 있습니다.

```javascript
const bestFriendMaker = (firstOne, ...rest) => {
	console.log(`My best friend is ${firstOne}`);
	console.log(rest);
};

bestFriendMaker("nico", "lynn", "dall", "japan guy");
// 출력
// My best friend is nico
// ["lynn", "dall", "japan guy"]
```

## 정리

- Spread : (변수를) 확장
- Rest : (변수를) 축소

둘 다 변수 앞에 ... 를 붙이며,
parameter 부분에 들어가게 되면 rest라고 부름.
* Rest는 Array 를 만든다.

