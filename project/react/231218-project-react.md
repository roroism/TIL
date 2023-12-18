# TODAY I LEARNED

## Learned

### Styled 소개

> ES6과 CSS의 장점을 누리면서 당신의 앱을 스트레스 없이 스타일링 하세요!
> Styled 홈페이지 번역

- 파일 단위의 CSS(`public/index.css`)가 아닌, **컴포넌트**화 된 스타일링 기법 소개
- Lyft, Coinbase, Atlassian, Doordash, Jane 등 다양한 테크 회사에서 사용 중인 라이브러리

#### 왜 Styled-components를 사용해야 할까?

- 리액트 컴포넌트를 CSS로 쉽게 styling 하기 위한 방법 제공

```javascript
const StyledButton = styled(Button)`
    background-color: blue;
    color: white;
    padding: 20px 10px;
    
    &:hover {
        background-color: darkblue;
    }
`;

const App = () => {
    <h1>Hello world!</h1>
    <StyledButton>여기를 클릭!</StyledButton>
}
```

#### '쉽게' 라는게 구체적으로 어떤거죠?

- 코드 스플릿(code split): 하나의 CSS 파일을 전역으로 적용하는 것이 아닌 컴포넌트 단위의 스타일링 가능. 필요한 코드만 로드
- className 이 중복될 염려 ❎: styled-components는 각 컴포넌트에 대해 고유한 class 이름을 생성하므로 이미 존재하는 클래스 이름과 겹칠 염려를 하지 않아도 됨.
- React 컴포넌트 처럼 사용할 수 있음 → 재사용 가능. 컴포넌트 트리에서 볼 수 있음
- 모든 스타일이 컴포넌트화 되어 있으므로, 컴포넌트의 사용처가 없는지 IDE (e.g. VS code, IntelliJ)를 통해 확인하고 쉽게 삭제 가능
- 컴포넌트에 적용되는 CSS가 무엇인지 찾기 위해 여러 파일을 찾지 않아도 됨

#### 핵심 기능

##### props에 따른 스타일링 적용

- 여느 React 컴포넌트처럼 styled 컴포넌트도 props를 지원
- props에 따라 스타일링을 유동적으로 적용 가능

##### Style 상속 가능

- React 컴포넌트 혹은 Styled 컴포넌트를 상속 받아 스타일 오버라이딩 가능
- 특정 상황에서 이미 존재하는 컴포넌트의 스타일링이 달라져야 할 때 사용 가능

##### CSS nesting 가능

##### 컴포넌트의 속성(attributes)은 그대로

- 상속하는 컴포넌트에서 제공하는 props/attributes는 Styled 컴포넌트 에서도 사용 가능
- e.g. Button 컴포넌트에서 제공하는 `onClick` 그대로 사용 가능

##### 컴포넌트의 속성(attributes) 설정도 가능

- .attrs 생성자를 이용해서 컴포넌트에 추가 속성(props)를 넘길 수 있음

##### Animation도 설정 가능!

- @keyframes를 이용하면 CSS의 animations도 설정할 수 있다.

