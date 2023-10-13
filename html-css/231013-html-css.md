# TODAY I LEARNED

## Learned

### 웹 접근성 오류 유형 12개 리뷰

#### 정지 기능 제공 (Timing Adjustable)

- 콘텐츠에 시간 제한이 설정되어 있다면 최소한 다음 중 하나를 만족해야 한다. 끄기, 조절, 연장.
- (정지 기능 제공) 자동으로 변경되는 콘텐츠는 움직임을 제어할 수 있어야 한다.
- 움직이는 콘텐츠에는 이전, 다음, 정지기능을 제공하면 된다.

#### 키보드 사용 보장 (Keyboard)

마우스에서의 동작이 키보드로도 똑같이 동작해야 한다.

- 콘텐츠의 모든 기능은 개인적인 타이핑 속도에 구애 받지 않고 키보드 인터페이스를 이용하여 조작이 가능해야 한다.
- (키보드 사용 보장) 모든 기능은 키보드만으로도 사용할 수 있어야 한다.
- 위처럼 구현해야 하는 이유는 상지 장애인분들도 있기 때문이다.
- 예를 들어 키보드 초점이 들어가면 sub 메뉴가 펼쳐질 때, 키보드 초점이 들어가도 같은 동작이 나와야 한다.

##### 해결방법

- '장치 독립적 이벤트 핸들러'를 알아야 한다.
- '장치 독립적 이벤트 핸들러' 키보드와 마우스의 동등한 사용을 보장하는 이벤트 핸들러이다.
- 예를 들어 onclick 이벤트 핸들러는 사용자의 마우스 클릭에도 반응하지만, 사용자가 키보드 초점이 들어간 컨트롤에 엔터를 쳐도 onclick 이벤트가 발생한다. 이처럼 마우스와 키보드 모두 사용할 수 있다.

```
onblur
onchange
onclick
onfocus
oninput
onselect
```

```
// 아래 이벤트 핸들러는 키보드 접근이 보장되는지 주의를 기울여야 한다.
ondblclick ⚠️
onkeydown ⚠️
onkeypress ⚠️
onkeyup ⚠️
onmousedown ⚠️
onmouseenter ⚠️
onmouseleave ⚠️
onmousemove ⚠️
onmouseout ⚠️
onmouseover ⚠️
onmouseup ⚠️
touchstart ⚠️
touchend ⚠️
touchmove ⚠️
touchcancel ⚠️
```

