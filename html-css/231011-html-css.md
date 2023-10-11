# TODAY I LEARNED

## Learned

### 웹 접근성 오류 유형 12개 리뷰

#### 대체 텍스트 제공 (Non-text Content)

텍스트 아닌 콘텐츠는 그 목적에 상응하는 대체 텍스트를 포함한 상태로 표시해야 한다.

1. 

```html
<img src="valid.jpg" alt="장식"> ❌
<img src="valid.jpg" alt> 👏
```

- 장식 목적의 이미지는 alt 속성만 제공하고 값을 비워둔다.

2.

- 주변 문맥을 통해 이미 충분히 설명하고 있는 내용은 대체 텍스트 불필요. 내용 중복 금지.
- 내용이 중복되면 화면 낭독기를 사용하는 시각 장애인들이 오히려 더 불편해 한다.

3.

```html
<a href="...">
	<img src="..." alt> 👏
	우리사이느은
</a>
```

- 하나의 anchor 태그가 이미지와 텍스트를 감싸고 있다. 이 이미지에 대한 설명은 이미 텍스트로 설명되고 있으므로 alt 속석의 값을 생략한다.
- 화면 낭독기는 anchor 태그를 만나면, 그 안에 있는 내용들을 전부 하나의 텍스트처럼 읽어주기 때문이다.

4.

- CSS 배경 이미지에 의미가 포함된 경우 IR (Image Replacement) 기법 사용.
- img 태그로 이미지를 제공하는 것이 아니기 때문에 대체 텍스트를 제공하지 않게 된다. 이 때 IR기법을 활용한다.
- 화면에는 css 배경 이미지를 표시하고, html 코드에 대체 텍스트를 화면에 보이지 않게 추가한다.
- 대체 텍스트에 적용하는 css 코드는 아래와 같다.

```css
.a11y {
  position: absolute; 👌
  opacity: 0; 👌
  display: none; ❌
  visibility: hidden; ❌
  width|height: 0; ❌
  font-size: 0; ❌
}
```

#### 반복 영역 건너뛰기 (Bypass Blocks)

여러 웹 페이지에서 반복되는 콘텐츠 블록을 우회할 수 있어야 한다.

- Tab 키를 눌렀을 때, 화면에 나오는 숨은링크이다.

```css
@media (max-width: 960px) { .skipToMain { display: none; } } 
@media (min-width: 961px) {
  .skipToMain {
    display: block;
    height: 1px;
    margin-bottom: -1px;
    overflow: hidden;
    text-align: center;
    line-height: 48px;
  }
  .skipToMain:focus {
    height: auto;
    margin-bottom: 0;
  }
}
```

- 위 코드에서 960이하의 해상도에서는 사용하지 않게 처리한 이유는 모바일이나 테블릿과 같은 장치에서는 키보드라는 장치가 없기 때문에(보통 터치로 제어한다.) 모바일에서는 display: none으로 숨겼다.
- 해상도 961 이상에서는 height: 1px, overflow: hidden 을 주어서 넘치는 영역을 보이지 않도록 만들고, focus를 설정하여 키보드 초점이 들어가면 height: auto 로 설정하여 화면에 등장하게 만든다.


