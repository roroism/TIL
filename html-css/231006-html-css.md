# TODAY I LEARNED

## Learned

### 덜컥덜컥 누적 배치 변경 문제 (CLS 란)

#### 이미지/영상 비율 힌트 제공하기

##### 1. img 태그에 width와 height를 적용하기

```html
// As is
<img src="..." alt>

// To be
<img src="..." width="800" height="534" alt>
➕
max-width: 100%;
height: auto;
```

- img 태그에 width와 height를 작성하는 것이 좋다.
- 적용한 width와 height 값대로 렌더링되지 않아도 상관없다. 중요한 것은 width와 height의 비율이 중요하다.
- 웹 브라우저는 img에 적혀있는 width와 height의 값을 이용하여 이미지의 비율을 계산할 수 있다.

##### 2. aspect-ratio 로 문제를 해결하기

- 콘텐츠의 너비와 높이의 비율을 고정해주는 속성이다.
- 사용하기 전에 caniuse에서 지원하는 브라우저를 확인하자.

```css
aspect-ratio: 800 / 534; /* ⚠️ Check caniuse. */
```

##### 3. 영상 종횡비 유지하기 (padding)

- 비율을 유지하면서 영상을 삽입하는 방법이다.
- 영상의 종횡비를 유지하는데 가장 많이 사용되는 코드이다.
- 부모요소의 너비값을 기준으로 padding 의 비율이 결정되기 때문에 이 특징을 이용하여 종횡비 유지에 사용할 수 있다.

```css
.utube {
  position: relative;
  padding-top: 56.25%; /* 315 / 560 * 100 */
}
.utube__iframe {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
}
```

