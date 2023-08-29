# TODAY I LEARNED

## Learned

### CSS의 절대 권력, 초기화

- CSS 리셋이 정말 꼭 필요할까?
- 대부분의 reset 파일들은 덮어쓰기 되고 사용되지 않는다. 많이 사용되고 있는 reset.css는 현재 시점에서 굳이 선언하지 않아도 되는 스타일이 대부분.

#### Find unused CSS

- 사용하지 않는 CSS를 찾는 방법.
- 개발자 도구 : Ctrl + Shift + P + (coverage) 로 coverage 탭을 노출시킨다.
- css을 선택하여 사용되지 않는 코드의 비율을 확인할 수 있다.

#### CSS reset reinvent

- 아래 코드들은 reset style 에 있었으면 하는 코드들.

```css
/* Reset body */
body {
    margin: 0;
    overflow-wrap: break-word;
}

/* Do not break Korean words */
:lang(ko) { word-break: keep-all; }
```

```css
/* Reset img */
img {
  max-width: 100%;
  height: auto;
}
```

```css
/* CSS Reset by [class] */
/* class 속성이 들어간 요소만 style 속성 */
[class] {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  list-style: none; // ol, ul
  border: 0; // button, table, fieldset, input, textarea, select, iframe
  background-color: transparent; // button, dialog, input, mark, meter, progress
  border-collapse: collapse; // table
  border-spacing: 0; // table  
  -webkit-appearance: none;
  appearance: none; // button, input, textarea, select, meter, progress
}
[class]::before,
[class]::after { box-sizing: border-box; }

/* 위 코드는 모든 요소에 불필요한 속성까지도 과도하게 reset 속성을 부여한다.*/
/* 아래처럼 where를 사용하면 필요한 범위에만 스타일을 적용한다. */

/* CSS Reset by [class] - Will be used when Samsung Internet supports it. */
[class] {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
[class]::before,
[class]::after { box-sizing: border-box; }
[class]:where(ol, ul) { list-style: none; }
[class]:where(button, fieldset, iframe, input, select, textarea) { border: 0; }
[class]:where(button, dialog, input, mark, meter, progress) { background-color: transparent; }
[class]:where(table) {
  border: 0;
  border-collapse: collapse;
  border-spacing: 0;
}
[class]:where(button, input, meter, progress, select, textarea) {
  -webkit-appearance: none;
  appearance: none;
}
```

