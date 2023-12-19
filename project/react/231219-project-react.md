# TODAY I LEARNED

## Learned

### React Testing Library 소개

- RTL (React Testing Library)
- React 컴포넌트들을 테스팅 하기 위해 필요한 utility성 function들을 제공하는 라이브러리

#### 특징

- DOM 노드들을 찾거나, DOM 노드들과 소통하기 위한 솔루션 제공

#### React 컴포넌트 렌더링

- render 메서드 이용

```javascript
test('it renders the component', () => {
    render(<ComponentName />)
})
```

#### DOM 노드 검색

DOM 노드 검색 = 형태 + 쿼리 방식

##### 형태

- **getBy**XXX - 현재 DOM 트리 내에서 한 노드를 찾는 것. 못찾으면 에러 발생시킴
    - **getAllBy**XXX - 현재 DOM 트리 내에서 모든 노드를 찾는 것.
- **findBy**XXX - DOM 트리 내에서 노드 한 개가 나타날 때까지 기다렸다가 해당 DOM 을 선택하는 Promise 를 반환. 특정 시간 내에 나타나지 않으면(타임아웃 시) 에러 발생
    - **findAllBy**XXX - 노드 여러개가 나타날 때가지 기다림
- **queryBy**XXX - 현재 DOM 트리 내에서 노드를 찾는 것. 못찾으면 `null`을 리턴 함
    - **queryAllBy**XXX - 현재 DOM 트리 내에서 모든 노드를 찾는 것.

##### 쿼리 방식

- ByLabelText - `label`이 있는 `input` 엘리먼트의 라벨 내용으로 `input` 엘리먼트를 반환
- ByRole - 특정 `role` 속성을 가지고 있고 값이 매칭하는 엘리먼트를 반환
- ByText - 엘리먼트가 가지고 있는 텍스트 값으로 검색
- ByPlaceholderText - `placeholder` 속성 값을 가지고 값이 매칭하는 엘리먼트를 반환
- ByAltText - `alt` 속성을 가지고 있고(e.g. `img`) 값이 매칭하는 엘리먼트를 반환
- ByDisplayValue - 현재 DOM 트리에서 `input, textarea, select` 등의 엘리먼트가 화면 상에 보이는 현재 값과 주어진 값이 매칭하는 엘리먼트를 반환
- ByTitle - `title` 속성을 가지고 있고 값이 매칭하는 엘리먼트, 혹은 `title` 엘리먼트가 있는 `svg`엘리먼트를 반환
- ByTestId - `data-testid` 속성을 가지고 있고 값이 매칭하는 엘리먼트를 반환. 보통 위의 쿼리 방식들로 노드를 가져올 수 없을 경우, 이 방식을 사용하곤 한다.

##### 예시

```javascript
screen.getByPlaceholderText('그룹 정보 입력')

screen.findAllByRole('button')

screen.queryByLabelText('날짜')
```

#### 이벤트 발생시키기

##### 클릭 이벤트

- userEvent / fireEvent 메서드 이용

```javascript
userEvent.click(screen.getByText('저장'))
```

##### 값 입력

- userEvent / fireEvent 메서드 이용

```javascript
userEvent.type(screen.getByRole('textbox'), '제주도 여행')
```

##### 값 수정

- fireEvent 메서드 이용

```javascript
fireEvent.change(input, {target: {value: 'new value'}})
```

> userEvent와 fireEvent의 차이점은 뭔가요? fireEvent는 DOM 노드에 직접 일으키는 이벤트 입니다. userEvent는 실제로 사용자가 이벤트를 발생시켰을 때처럼 모든 인터랙션을 시뮬레이션 합니다. 예를 들면, 실제 특정 버튼 클릭 이후에 트리거 되는 다른 이벤트들도 포함되서 시뮬레이션 되는 것이죠.

#### DOM 노드 찾고, 이벤트 발생 시키는 것도 알겠는데.. 정작 중요한 값 확인(assert)은 어떻게 하나요?

- Jest 에서 제공하는 함수 중, `expect` 구문을 이용할 겁니다!

