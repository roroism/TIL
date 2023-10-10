# TODAY I LEARNED

## Learned

### 덜컥덜컥 누적 배치 변경 문제 (CLS 란)

#### 자리표시자

- 최소값을 미리 넣어둔다.
- 배경색을 회색 등을 넣어서 자리 표시자를 제공한 것과 같은 느낌을 준다.

```css
.heroBanner {
    min-height: 100px;
    background: silver;
}
```

#### 웹 폰트 대체 글꼴

- 그냥 system 글꼴을 제공하는 것이 아니라 사용하려는 웹 폰트와 특성이 비슷한 대체 글꼴을 사용하는 것이 좋다.

```css
// bad
font-family: 'Noto Sans KR', sans-serif;

// good
font-family: 'Noto Sans KR', Verdana, sans-serif;
```

#### 정리

1. 이미지/영상 요소에 비율 힌트(width, height) 제공.
2. 추가 DOM에 자리표시자 제공.
3. 웹 폰트와 유사한 시스템 대체 글꼴 제공.

