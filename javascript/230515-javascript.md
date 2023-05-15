# TODAY I LEARNED

## Review

### Set

- set을 사용하면 어떤 타입의 value든 고유한 value로 저자할 수 있게 해줍니다.
- 그래서 중복된 값을 저장하지 못하게 하려는 매커니즘이 필요한 경우 사용할 수 있습니다.

```javascript
const sexySet = new Set([1, 2, 3, 4, 5, 6, 7, 7, 7, 7, 8]);

console.log(setxySet);
// {1, 2, 3, 4, 5, 6, 7, 8}
```

#### Set의 유용한 함수들

- .has()
- .delete()
- .clear()
- .add()
- .size()

#### WeakSet

- weak sets은 sets와 같은 듯 다릅니다.
- weak sets의 차이점은 오로지 object만(Array도 가능) 저장가능합니다. (numbers, text 저장 안됨.)
- 가지고 있는 함수는 add, delete, has 밖에 없습니다.
- waek이라는 단어에 주목해 본다면, weakset에 넣은 모든 것들은 약하게 붙들려 있습니다.(weakly held) 만약에 waek set에 넣은 object를 가르키는 것이 없다면, 이것은 메모리로부터 지워집니다.

### Map

- map은 set과 비슷하지만, 차이점은 map은 key-value를 사용할 수 있게 해줍니다.
- set은 오직 value만 넣을 수 있습니다. map은 마치 key values 저장소 같은 느낌입니다.

#### Map의 유용한 함수들

- .set()
- .entries()
- .has() 와 .get()

### 정리

- 보통 set을 잘 사용하고 map은 잘 사용하지 않습니다. 하지만 key value storage를 사용하고 싶다면 유용합니다.

