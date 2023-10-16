# TODAY I LEARNED

## Learned

### 웹 접근성 오류 유형 12개 리뷰

#### ARIA

- ARIA : Accessible Rich Internet Application의 약자.
- 접근 가능한 고기능 인터넷 애플리케이션.
- HTML의 접근성 문제를 보완하는 W3C 명세.
- HTML에 '역할(roles), 상태(states), 속성(properties)' 정보를 부여하여 보조기기의 웹 문서 접근을 지원.
- 역할은 html의 의미를 좀 더 다채롭게 만들어 준다. 상태와 속성 정보는 이 문서를 좀 더 살아 움직이는,(생동감있는) 문서로 만들어준다.
- 실시간으로 갱신되는 정보들을 화면 낭독기나 보조기기에 정확하게 전달해 줄 수 있게 된다.

##### Return to HTML

- 웹 접근성 문제의 80%는 HTML을 잘 못 사용해서이다.
- 대부분의 WAI-ARIA 명세는 HTML 요소와 속성을 흉내내는 것.
- ARIA를 사용하기에 앞서 HTML을 의미 있게 사용했는지 검토할 것.
- 예를 들면 a 태그에 role='button' 또는 role='link' 라는 명세를 적용하는 것은 적절하지 않다. 왜냐하면 role='button'에 해당하는 button 엘리먼트가 이미 존재하기 때문이다. 마찬가지로 role='link' 에 해당하는 a 엘리먼트가 이미 있다.

```html
<!-- X -->
<a href="#" role="button">...</a>
<a href="#" role="link">...</a>

<!-- O -->
<button type="button">...</button>
<a href="#">...</a>
```

#### ARIA - 역할(roles)

- 아래 예제 말고도 더 다양한 예시가 있다.

```html
<element role="tablist"> ⭐
<element role="tab"> ⭐
<element role="tabpanel"> ⭐
<element role="tooltip"> ⭐
<element role="status"> ⭐
<element role="alert"> ⭐
<element role="alertdialog"> == <dialog>
<element role="dialog"> == <dialog>
<element role="navigation"> == <nav>
<element role="complementary"> == <aside>
<element role="none"> == <div>
```

