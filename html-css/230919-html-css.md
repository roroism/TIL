# TODAY I LEARNED

## Learned

### 포토샵 닫고 CSS 열기

- css를 이용해서 이미지를 대체할 수 있는 기법들을 소개하겠습니다.
- 이미지를 사용하지 않는다면 웹페이지 성능을 더 좋게 만들 수 있다.

#### 삼각형 만들기

- 삼각형은 웹 페이지에서 많이 사용하는 디자인 요소중에 하나이다.
- 삼각형 만들기의 기본적인 코드 (::after 활용)

```css
border: 40px solid transparent;
border-left-color: red;
```

#### 꺽쇠 만들기

- 꺽쇠 / 화살표 만들기의 기본적인 코드 (::before 활용)

```css
transform: rotate(-45deg);
transform-origin: 25% 25%;
```

#### 화살표 만들기

- 꺽쇠 / 화살표 만들기의 기본적인 코드 (::before, ::after 활용)

```css
transform: rotate(-45deg);
transform-origin: 25% 25%;
```

#### 스피너 만들기

- 스피너 만들기의 기본적인 코드

```css
border: 8px solid silver;
border-top-color: transparent;
animation: spin 1s linear infinite;

@keyframes spin {
  to { transform: rotate(360deg); }
}
```

#### 격자 배경 만들기

- 격자 배경 만들기의 기본적인 코드

```css
background: 
  linear-gradient(to bottom, transparent 47px, silver 47px) 0 0 / 100vw 48px repeat-y,
  linear-gradient(to right, transparent 47px, silver 47px) 0 0 / 48px 100vh repeat-x
  black;
```

#### 체커 배경 만들기

- 사각형 4개가 하나의 배경이미지 영역이다.
- 체커 배경 만들기의 기본적인 코드

```css
background-image: 
  linear-gradient(135deg, silver 25.1%, transparent 25%),
  linear-gradient(225deg, silver 25.1%, transparent 25%),
  linear-gradient(315deg, silver 25%, transparent 25%),
  linear-gradient(45deg, silver 25%, transparent 25%);
background-size: 20px 20px;
background-position: 10px 0, -10px 10px, 0 -10px, 0 0;
```

#### 햄버거 아이콘 만들기

- 두번째, 세번째 선은 그림자로 만든 것.
- 햄버거 아이콘 만들기의 기본적인 코드

```css
box-shadow: 0 8px 0 black, 0 16px 0 black;
box-shadow: 0 0 0 3px white;
```

