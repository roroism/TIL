# TODAY I LEARNED

## Learned

### Hash Tables

Hash Tables 은 Key Value System 을 이용하여 자료를 정리합니다.
`{key : value}`

#### Hash Tables 와 Array (배열) 의 비교

1. 배열

```javascript
menu = [
	{ name: "coffee", price: 10 },
	{ name: "burger", price: 15 },
	{ name: "tea", price: 5 },
	{ name: "pizza", price: 10 },
	{ name: "juice", price: 5 },
];
```

1. 배열
pizza를 찾으려면 Linear Search (선형 검색)을 하면 됨.
각각의 아이템을 처음부터 접근하여 찾아 갑니다.
이건 시간이 너무 오래 걸립니다.

그래서 이 때! Hash Tables 를 이용합니다.
이것을 Hash Tables 로 정리한다면?

2. Hash Tables
pizza를 찾으려면 pizza를 키로 찾습니다.
```javascript
menu = {
	coffee: 10,
	burger: 15,
	tea: 5,
	pizza: 10,
	juice: 5,
};
```
`menu["pizza"] // = 10`

#### 시간복잡도

1. 배열
O(N)
Linear Time (선형 시간)
아이템이 많을수록 찾는 시간이 오래걸립니다.

2. Hash Tables
O(1)
Constant Time (상수 시간)
어떤 메뉴의 값을 찾더라도 소요되는 건 딱 1개 스텝입니다.
아이템을 추가할때도 삭제할때도 마찬가지로 O(1) 입니다.

Array 랑 비교 했을 때 매우 빠릅니다.

#### 좀 더 복잡한 Hash Tables 다루기

key 와 value 중 value만 저장하는 테크닉을 보겠습니다.
```javascript
나라들 = {
	"그리스" : true,
	"네덜란드" : true,
	"태국" : true,
	"한국" : true,
	"터키" : true,
	"이탈리아" : true,
}
```
이렇게 하면 태국이 리스트에 있는지 찾는 데 딱 1번의 스텝만 필요합니다.
```javascript
나라들["태국"]; // true
나라들["서울"] // undefined
```

#### Hash Tables 의 원리

내부에는 array 같은 구조가 있습니다.
하지만 array와 다르게 빠른 이유는 Hash Function (해시 함수) 때문입니다.
Hash Function은 저장하고 싶은 key를 숫자로 바꿉니다. 그 숫자는 바로 array의 index가 됩니다.

#### 정리

Hash Tables은 Array처럼 리스트가 있지만 시간복잡도는 O(1) 인 것입니다.
하지만 Hash Tables의 시간복잡도가 언제나 상수 시간인 것은 아닙니다. 왜냐하면  Collision(해시 충돌)이 있을 수 있고, 그 경우에는 선형 검색을 하기 때문입니다.
javascript 에서는 Hash Tables을 object로 구현합니다.

