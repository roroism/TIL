# TODAY I LEARNED

## Learned

### Zustand 란?

- 간소화된 Flux 원칙을 사용하는 작고 빠르고 확장 가능한 barebone 상태 관리 솔루션입니다.
- 'Zustand'는 독일어로 'State'를 뜻합니다.
- Zustand는 Jotai 및 React 스프링 개발자가 구축한 빠르고 확장 가능한 상태 관리 솔루션입니다.

barebones 단어의 사전적 의미: 바싹 마른 사람, 말라빠진, 골자(요점)만의, 내용이 빈약한

#### Zustand 특징

- 상용구 코드 감소
- Zustand는 상태 값이 변경될 때만 구성 요소를 렌더링합니다. 구성 요소를 다시 렌더링하지 않고도 상태 변경을 처리할 수 있는 경우가 많습니다.
- 상태 관리는 중앙 집중식이며 단순하게 정의된 작업을 통해 업데이트됩니다. 이 점에서 Redux와 유사하지만 개발자가 상태를 처리하기 위해 Reducer, Action 및 Dispatch를 만들어야 하는 Redux와 달리 Zustand는 훨씬 쉽습니다.
- Hooks를 사용하여 상태를 사용합니다.
- 컨텍스트 제공을 사용할 필요가 없어 깨끗한 코드를 제공하므로 코드가 더 짧고 가독성이 높아집니다.

#### Zustand의 특징과 Redux, useContext 비교시 장점

- Zustand는 useContext 기반으로 만들어졌지만, provider로 래핑을 하지 않는다. 대신 클로저를 이용하여 스토어를 제공한다.
- Zustand 또한 별도의 데이터 페칭 라이브러리를 함께 사용하는 것이 좋다.
- 렌더링 없이 컴포넌트에 변경된 정보를 일시적으로 알릴 수 있다.

1. 크기와 복잡성
Redux는 상태 관리를 위한 매우 강력하고 유연한 도구지만, 설정이나 boilerplate 코드가 많아 프로젝트 규모가 커질수록 코드 양이 늘어날 수 있다.
Zustand는 작은 규모의 프로젝트나 단순한 상태 관리에 더 적합하며, Redux보다 상대적으로 덜 복잡한 API를 제공한다.
2. API의 간결성
Zustand는 상태를 다루기 위한 간결하고 직관적인 API를 제공한다. 작은 훅 함수를 통해 쉽게 상태를 생성하고 사용할 수 있다.
Redux는 좀 더 많은 설정과 액션, 리듀서 등의 구조가 필요하며, 몇몇 복잡한 작업을 위해서는 추가적인 라이브러리를 사용해야 할 수도 있다.
3. 리랜더링 최적화
Zustand는 내부적으로 React의 useContext를 사용하여 컴포넌트 간에 상태를 전파하므로, 성능 측면에서 효율적이다. useContext의 가장 큰 단점, 상태가 변경될때마다 새로고침이 발생하는 문제를 해결할 수 있다.

#### Store 생성하기

- 먼저 Store를 생성해서 그 안에 원하는 값과 그 값을 업데이트 해주는 함수를 넣습니다.
- Store는 Hooks로 되어 있습니다.
- Store에는 객체, 함수 등 무엇이든 넣을 수 있습니다.
- Store를 생성할 때는 create 메서드를 사용하여 선언합니다.
- set 함수는 상태를 변경합니다.

useCounterStore

```javascript
import create from 'zustand'

export const useCounterStore = create(() => ({
    count: 1,
    inc: () => set((state) => ({ count: state.count + 1 })),
}))
```

App.js

```javascript
import create from 'zustand'

export const useCounterStore = create(() => ({
    count: 1,
    inc: () => set((state) => ({ count: state.count + 1 })),
}))
```

Counter.js

```javascript
import { useCounterStore } from '../store'

export default function Counter() {
    const { count, inc } = useCounterStore()
    return (
        <div className='counter'>
            <p>{count}</p>
            <button onClick={inc}>one up</button>
        </div>
    )
}
```

