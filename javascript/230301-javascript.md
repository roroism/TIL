# TODAY I LEARNED

## Learned

### Object entries, Object values,Object fromEntries

object는 javascript의 데이터 타입입니다.
object는 create, assign, freeze 같은 메소드를 가지고 있습니다.

참고 : Object.freeze() : object를 바꾸지 못하게 합니다.

#### Object values(), Object entries()

values는 객체의 값들을 배열로 return합니다.
entries는 객체의 key와 값을 return합니다. 배열의 배열로 return합니다.

```javascript
const person = {
    name: "nico",
    age: 12
}

// 객체의 값들을 알고 싶을 경우
Object.values(person);
// (2) ["nico", 12]

// entries
Object.entries(person);
// (2) [Array(2), Array(2)]
// 0: (2) ["name", "nico"]
// 1: (2) ["age", 12]
```

위처럼 key값의 이름과 값이 배열의 형태로 들어있습니다.

##### 사용예

```javascript
Object.entries(person).forEach(item => console.log(item[0], item[1]));
// 출력
// name nico
// age 12
```

#### Object.fromEntries()

배열의 배열에서부터(Object.entries 결과물의 구조) Object를 만들어줍니다.

```javascript
Object.fromEntries([["name", "nico"], ["age", 12], ["f", "k"], ["hello", true]]);
// {name: "nico", age: 12, f: "k", hello: true}
```

