# TODAY I LEARNED

## Learned

### at()

```javascript
const arr = ["a", "b", "c", "d"];

console.log(arr.at(2)); // c
console.log(arr[2]); // c
// 여기까지는 기존의 arr[2] 나 arr.at(2) 는 차이가 없습니다.
```

기존의 arr[2] 나 arr.at(2) 는 차이가 없습니다.
만약 배열에서 0부터 시작하는 인덱스의 항목을 찾고 싶다면, 이 둘은 다른점이 없습니다.

하지만, 끝에서부터 item을 찾고 싶다면 at 메서드가 빛을 발합니다.
at() 은 끝에서부터도 item을 찾을 수 있게 해줍니다.

```javascript
console.log(arr.at(-1)); // d
console.log(arr[-1]); // undefined

console.log(arr.at(-3)); // b
```

at()은 음수 인덱스를 사용해서 끝에서부터 찾을 수 있게 해줍니다.

Javascript에서는 일반적인 방법으로는 끝에서부터 찾을 수 없습니다. at()이 이것을 가능하게 해줍니다.

### Object hasOwn

Object.hasOwn은 object가 property를 가지고 있는지 확인합니다.

Object.hasOwn 이전에 기존에 사용한 Object.hasOwnProperty에 대해 먼저 확인해 봅니다.

```javascript
const user = {
    name: "nico",
    isAdmin: "hi"
};

console.log(user.hasOwnProperty("isAdmin")); // true
```

기존의 hasOwnProperty는 조사하려는 객체에서 hasOwnProperty메서드를 호출하여 인자로 조사하려는 속성이름을 넘겼지만,
Object.hasOwn 은 Object.hasOwn(객체, "확인하려는 속성 이름"); 으로 나타냅니다.
Object.hasOwn(obj, propKey)

```javascript
const user = {
    name: "nico",
    isAdmin: "hi"
};

console.log(user.hasOwnProperty("isAdmin")); // true
console.log(Object.hasOwn(user, "isAdmin")); // true
```

공식문서 중..
> Object.hasOwn() is intended as a replacement for Object.prototype.hasOwnProperty().
> Object.hasOwn()은 Object.prototype.hasOwnProperty()를 대체하기 위한 것입니다.

가능하다면 hasOwnProperty() 보다 Object.hasOwn() 을 사용하는 것을 추천합니다.
이유 공식문서 확인 : https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwn

#### object에 property가 존재하는지 확인하는 작은 트릭

```javascript
console.log("isAdmin" in user); // true
```

### Error cause

개발자의 DX를 위해 만들어졌습니다. (DX : 개발자 경험)
많은 라이브러리나 오픈소스에서 이걸 사용하고 있을 거라고 생각됩니다.

error.cause를 사용하지 않고 기존의 에러 처리를 보면,

```javascript
try {
    2+2;
    throw new Error("DB Connection Failed.");
} catch(e) {
    console.log(e.message);
}

// 출력
// DB Connection Failed.
```

error.cause는 에러에 메세지를 추가할 수 있을 뿐만 아니라, 또 다른 정보를 추가하는 기능도 있습니다.

```javascript
try {
    2+2;
    throw new Error("DB Connection Failed.", {
        cause: "Password is incorrect"
    });
} catch(e) {
    console.log(e.message, e.cause);
}

// 출력
// DB Connection Failed. Password is incorrect
```

위처럼 에러에 대한 추가적인 정보를 제공할 수 있습니다.

그리고 cause가 꼭 문자열일 필요는 없습니다. 객체로 넘겨서 더 많은 정보를 남길 수 있습니다.

```javascript
try {
    2+2;
    throw new Error("DB Connection Failed.", {
        cause: {
            error: "Password is incorrect.",
            value: 1234,
            message: ["too short", "only number not ok."]
        }
    });
} catch(e) {
    console.log(e.cause);
}

// 출력
// { error: "Password is incorrect.", value: 1234, message: Array(2) }
```

