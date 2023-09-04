# TODAY I LEARNED

## Learned

### 레이아웃, 여백의 비밀

- box-sizing : content-box 일 때는 width/height에 padding값과 border값은 포함되지 않는다. (default)
- box-sizing : border-box일 때는 width/height에 padding값과 border값이 포함된다.
- 그래서 사람들이 border-box를 더 선호하고 실제로도 추천을 한다.

#### Relative <length>

- vw, vh 모바일에서 유용하게 사용할 수 있는 값.
- vmax : 뷰포트의 너비 또는 높이 중에 큰 값을 선택해서 그것을 기준으로 비율을 결정하는 것이 vmax 이다.
- vmin : 뷰포트의 너비 또는 높이 중에 작은 값을 선택해서 그것을 기준으로 비율을 결정하는 것이 vmax 이다.

#### Reset box-sizing

- 많은 사람들이 공용선택자`(*)`를 이용해서 reset설정을 한다. 아래처럼..

```css
/* 추천x */
*,
::before,
::after { box-sizing: border-box; }
```

- 하지만, 아래 코드를 추천한다.

```css
/* 추천o */
[class],
[class]::before
[class]::after { box-sizing: border-box; }
/* class가 들어간 요소에만 box-sizing을 border-box로 선언한다. */
/* 이 코드의 장점은 사용자가 다른곳에서 코드와 스타일을 옮겨와서 위지윅 에디터에 붙여넣기를 했을 때, 그 사용자의 스타일을 존중하는 방식으로 스타일 충돌이 발생하지 않게 한다.  */
```

#### padding

##### padding의 비밀 : % value

- % 값을 설정했을 때, %의 기준이 무엇인지가 padding의 비밀이다.
- % value : Refer to logical width of containing block.
- % value : 컨테이너 블럭의 너비 값을 참조.

```css
.parent { width: 100px; }
.child {
  width: 0;
  height: 0;
  padding-left: 25%; /* == 25px */
  padding-top: 50%; /* == 50px */
  background: red;
}
```

- margin 도 부모요소의 너비 값을 기준으로 결정된다.

