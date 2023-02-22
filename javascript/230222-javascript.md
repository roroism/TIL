# TODAY I LEARNED

## Learned

### Map and Weakmap

map은 set과 비슷하지만, 차이점은 map은 key-value를 사용할 수 있게 해줍니다.
set은 오직 value만 넣을 수 있습니다. map은 마치 key values 저장소 같은 느낌입니다.

```javascript
const map = new Map();
```

#### .set()

Map은 set의 .add() 대신 .set()을 가지고 있습니다.
.set() 에는 argument로 key와 value를 입력합니다.

```javascript
const map = new Map();

map.set("age", 18);
// 출력 : Map(1) {"age" => 18}
map.set("age", 255232);
// 출력 : Map(1) {"age" => 255232}
// 같은 key값에 다시 set을 하면 덮어 씁니다.
```

#### .entries()

iterator 객체를 반환합니다.
```javascript
const map = new Map();

map.set("age", 18);
// 출력 : Map(1) {"age" => 18}
map.entries()
// 출력 : MapIterator {"age" => 18}
```

#### .has() 와 .get()

.has()를 사용하면 속성이 있는지 여부를 boolean으로 반환하고, .get()은 속성이름으로 value값을 얻을 수 있습니다.

```javascript
const map = new Map();

map.set("age", 18);
// 출력 : Map(1) {"age" => 18}
map.entries();
// 출력 : MapIterator {"age" => 18}
map.has("age");
// 출력 : true
map.get("age");
// 출력 : 18
```

#### 정리

WeakMap은 WeakSet과 마찬가지로 object를 사용해야만 하고, object가 참조되지 않거나 참조되지 않는 중이라면 저장된 그 object는 사라집니다.
보통 set을 잘 사용하고 map은 잘 사용하지 않습니다. 하지만 key value storage를 사용하고 싶다면 유용합니다.

