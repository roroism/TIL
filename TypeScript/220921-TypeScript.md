# TODAY I LEARNED

## Learned

### Call Signatures

프로퍼티로 호출 가능한 것을 설명하려면 객체 타입에 Call Signature을 작성할 수 있습니다.
Call Signatures는 다음과 같이 함수의 매개 변수(parameter)와 반환 타입을 지정합니다.

```tsx
type PizzaFunction = {
pizza: string;
(args: number): boolean;
};

function hello(fn: PizzaFunction) {
console.log(fn.pizza, fn(6));
}
```
