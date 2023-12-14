# TODAY I LEARNED

## Learned

### Recoil 소개

- React를 위한 상태 관리 라이브러리
- Facebook에서 유지보수 하는 오픈소스 프로젝트

#### 상태 관리가 별도로 필요한 이유

- 컴포넌트 간 데이터를 공유하고 전달해야 할 때, React의 단방향 데이터 특성 상, 부모→자식으로 밖에 전달할 수가 없다. 자식↔자식 간의 공유를 하려면 부모 컴포넌트에 지저분한 로직들을 넣어야 하고, 결과적으로는 유지보수성, 가독성이 떨어짐.
- 부모에서 증손자 컴포넌트로 데이터를 전달해야 할 경우, 부모 → 자식 → 손자 → 증손자로 props를 전달하며 데이터를 공유해야 하는 경우도 많음 (전문 용어로는 props drilling이라고 부름). 자식, 손자 컴포넌트 입장에서는 불필요한 데이터를 받아야 하고, 상태 관리가 점점 복잡해짐..
- 그래서! 전역 상태 저장소 역할을 할 것이 필요!

#### 컨셉

##### Atoms

- **상태의 단위**
- 왜 Atom 이라고 부를까?
    - **Atom = 원자**
    - **최소한**의 **상태 집합만 담자!**
    (e.g. 사용자별 todo list 컴포넌트 = todo atom + user atom)
    - Atom 하나에 앱에서 쓰는 모든 상태를 때려 넣지 말자는 철학!
- 상태 데이터를 담고 있기에, 읽기/쓰기를 할 수 있고, subscribe를 할 수 있다.
    - Atom이 업데이트 되면 이를 구독하고 있는 React 컴포넌트는 새로운 값을 반영하여 다시 렌더링 됨
- 컴포넌트들 사이에 공유되는 상태 값 (a.k.a. source of truth)

```javascript
const todoListState = atom({
    key: 'todoListState',
    default: [],
});
```

- `key` : Atom과 Selector에서 관리하는 상태값을 구분하기 위한 값으로, 어플리케이션 전역적으로 고유 해야 한다. 값은 문자열.

##### Selectors

- **Atom이나 다른 Selector를 입력으로 받아들이는 순수 함수**
- 무슨 말이죠?
    - 최소한의 상태 집합만 Atom에 담다보니, Atom으로 인해 파생되는 데이터는 Selector에 명시한 함수를 통해 계산을 해야 함
    (e.g. todo list *atom* → filtered todo list *selectors*)
- React 컴포넌트는 Selector를 Atom과 같이 구독할 수 있으므로, Selector가 변경되면 컴포넌트들도 다시 렌더링 됨
- Atom과 Selector는 같은 인터페이스를 가지고 있다. 둘 다 상태(state)를 나타낸다
- Selector 함수는 멱등(idempotent)해야 한다. 이유 : Selector 결과값이 캐시가될 수도 있고, 재시작되거나 혹은 수 차례에 걸쳐서 실행될 수 있으므로 중요

> 멱등이란?
> 동일한 인풋이 주어지면, 항상 같은 아웃풋을 낸다는 것

**예시**

```javascript
const filteredTodoListState = selector({
    key: 'filteredTodoListState',
    get: ({get}) => {
        const todoList = get(todoListState)
        return todoList.filter(...)
    }
});
```

- 첫번째 `get` 속성은 계산될 함수.
- 전달되는 `get` 인자를 통해 atoms와 다른 selectors에 접근 가능.
- 다른 atoms나 selectors에 접근하면 자동으로 종속 관계가 생성되므로, 참조했던 다른 atoms나 selectors가 업데이트되면 이 함수도 다시 실행 됨.

##### Hooks

- React에서 제공하는 hook 처럼, Recoil도 hook을 제공

**useRecoilState**
- React 컴포넌트에서 atom을 읽고 쓰기 위한 hook
- React의 `useState`와 사용법은 같지만, 상태(atom)은 컴포넌트 간에 공유된다는 차이점!

**useRecoilValue**
- Atom이나 Selector를 인자로 받아 요청하는 값을 반환
- state를 조작할 필요 없이 값을 읽기만 하면 되는 경우에 사용

#### Recoil로 비동기 쿼리 핸들링 하기

- Selector를 이용해서 가능
- Selector의 get 속성에서, (1) Promise를 리턴하거나, (2) async 함수를 사용하기만 하면 끝!

