# TODAY I LEARNED

## Learned

### WeakSet

weak sets은 sets와 같은 듯 다릅니다.

```javascript
const weakSet = new WeakSet();
```

weak sets의 차이점은 오로지 object만(Array도 가능) 저장가능합니다. (numbers, text 저장 안됨.)
```javascript
const weakSet = new WeakSet();
// waekSet.add(1); // 에러
weakSet.add({hi: true}); // 가능
```

또 다른 차이점은 weak sets에서 size, entries, properties 등을 사용할 수 없습니다. 가지고 있는 것은 add, delete, has 밖에 없습니다. normal set 에서는 add, clear, delete, entries, forEach, has, keys, size, values 등을 사용할 수 있습니다.

즉, weakset은 Object와 함께 동작하기 때문에 api를 조금 덜 가지고 있습니다.

그리고 waek이라는 단어에 주목해 본다면, weakset에 넣은 모든 것들은 약하게 붙들려 있습니다.(weakly held) 만약에 waek set에 넣은 object를 가르키는 것이 없다면, 이것은 메모리로부터 지워집니다.

```javascript
const weakSet = new WeakSet();
const sexy = {
    im: true
};

weakSet.add(sexy);
```

위에서 sexy object는 sexy라는 변수가 set 내부의 object를 가르키고 있기 때문에 지워지지 않습니다.

하지만..

```javascript
const weakSet = new WeakSet();
waekSet.add({hello: true});
```

{hello: true}는 Sets 내부에서 생성된 object입니다. set 밖에 어떤 것도 이 object를 가리키지 않습니다. 다시말해서 {hello: true} 에 대한 어떤 참조도 존재하지 않습니다.

여기서 Garbage collector가 오게 되면 어떻게 될까요? 참조 되지 않는 {hello: true} object를 메모리에서 해제 합니다.
Garbage collector가 정확히 언제 동작할지는 모릅니다.
하지만 우리가 웹브라우저 개발자 모드에서 강제로 동작하게 할 수 있습니다.

```javascript
const weakSet = new WeakSet();
waekSet.add({hello: true});

console.log(weakSet);
// 결과 
// WeakSet{{hello: true}}

// Garbage Collector 동작
console.log(weakSet);
// 결과 
// WeakSet {}
```

#### 결과

weakSet의 usecase는 매우 적습니다.
weakSet에 넣은 object가 어디서도 참조되지 않는다면, Garbage collector가 메모리에서 해당 object를 해제합니다.

