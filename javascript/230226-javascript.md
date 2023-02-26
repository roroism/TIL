# TODAY I LEARNED

## Learned

### Nullish coalescing operator

널 병합 연산자 (??) 는 왼쪽 피연산자가 null 또는 undefined일 때 오른쪽 피연산자를 반환하고, 그렇지 않으면 왼쪽 피연산자를 반환하는 논리 연산자이다.

이는 왼쪽 피연산자가 null 또는 undefined 뿐만 아니라 *falsy *값에 해당할 경우 오른쪽 피연산자를 반환하는 논리 연산자 OR (||)와는 대조된다. 다시 말해 만약 어떤 변수 foo에게 *falsy *값( '' 또는 0)을 포함한 값을 제공하기 위해 ||을 사용하는 것을 고려했다면 예기치 않는 동작이 발생할 수 있다. 하단에 더 많은 예제가 있다.

#### 설명

```javascript
const name = 0;

console.log("hello", name);
// hello 0

console.log("hello", name || "anonymous");
// hello anonymous

console.log("hello", name ?? "anonymous");
// hello 0
```

OR (||) 은 변수에 기본값을 줄 때 유용합니다.
하지만 weak point가 있습니다. 실제로 값이 할당되어 있어도 false로 판단합니다.
예를 들어 위 예시코드에서 name 에 0이 할당되어 있어도 OR (||) 는 이 0을 false로 판단합니다.

```javascript
const name = "";

console.log("hello", name);
// hello

console.log("hello", name || "anonymous");
// hello anonymous

console.log("hello", name ?? "anonymous");
// hello
```

빈 문자열도 마찬가지로 OR (||)에서는 false로 판단합니다.

빈 문자열("")이나 0도 쓰이게 하고 싶다면 널 병합 연산자(??)를 사용합니다.

#### falsy한 값

https://developer.mozilla.org/ko/docs/Glossary/Falsy

거짓 같은 값(Falsy, falsey로 쓰이기도 함) 값은 불리언 문맥에서 false로 평가되는 값입니다.

