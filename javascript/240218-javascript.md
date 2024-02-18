# TODAY I LEARNED

## 복습

### Typescript Readonly

```typescript
interface Person8 {
  name: string;
  age?: number;
  readonly gender: string;
}

const p81: Person8 = {
  name: 'Mark',
  gender: 'male',
};

// p81.gender = 'female'; // 에러: readonly 속성은 할당 후 바꿀 수 없습니다.
```

- interface에 readonly를 사용하면 class 에서도 readonly를 받아서 그대로 표현해 줄 수 있기 때문에 유용합니다.

- typescript를 사용하는 가장 큰 이유는 코드에 의도를 담아서 다른 사람들이 코드를 사용하거나 수정하려고 할 때, 무엇이 되고 안되는지에 대한 의사표시를 할 수 있다는 점입니다.

