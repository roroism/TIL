# TODAY I LEARNED

## Learned

### scrollIntoView

- 지정된 요소가 현재 화면에 표시되도록 스크롤을 조정하는 데 사용됩니다.
-해당 요소가 현재 화면에 보일 수 있도록 스크롤을 조정합니다. 요소가 이미 화면에 보이는 경우 아무런 작업도 수행되지 않습니다.

```javascript
element.scrollIntoView();
```

- 선택적으로 scrollIntoViewOptions라는 객체를 전달하여 스크롤 동작을 사용자 정의할 수 있습니다. 이 객체에는 다음과 같은 속성들이 있습니다.
- behavior: 스크롤 동작을 제어합니다. 기본값은 'auto'로 스크롤이 부드럽게 이루어집니다. 'smooth'를 지정하면 부드럽게 스크롤됩니다.
- block: 요소가 스크롤되는 방향을 제어합니다. 기본값은 'start'로, 요소가 뷰포트의 맨 위에 위치하도록 스크롤됩니다. 'end'를 지정하면 요소가 뷰포트의 맨 아래에 위치하도록 스크롤됩니다.
- inline: 요소가 스크롤되는 방향을 제어합니다. 기본값은 'nearest'로, 요소가 뷰포트의 가장 가까운 쪽에 위치하도록 스크롤됩니다. 'start'를 지정하면 요소가 뷰포트의 가장 왼쪽에 위치하도록 스크롤됩니다. 'end'를 지정하면 요소가 뷰포트의 가장 오른쪽에 위치하도록 스크롤됩니다.

```javascript
// 특정 요소를 스크롤하여 화면에 보이도록 이동합니다.
document.getElementById("myElement").scrollIntoView();

// 스크롤을 부드럽게 이동합니다.
document.getElementById("myElement").scrollIntoView({ behavior: "smooth" });

// 요소가 뷰포트의 맨 아래에 위치하도록 스크롤합니다.
document.getElementById("myElement").scrollIntoView({ block: "end" });
```

- 이러한 옵션을 사용하여 scrollIntoView() 메소드를 사용할 때 스크롤 동작을 세밀하게 제어할 수 있습니다.

