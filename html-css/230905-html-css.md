# TODAY I LEARNED

## Learned

### 레이아웃, 여백의 비밀

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

##### keep aspect-ratio

- padding과 margin의 % value의 비밀을 알면, 비율 유지 기법(keep aspect-ratio) 에 활용할 수 있다.
- 부모 요소를 기준으로 일정한 너비와 높이비율을 만들 수 있기 때문에 이 특징을 사용하면 비율이 유지된 박스를 만들 수 있다.
- 보통 유튜브에 많이 활용한다. (퍼가기 공유하기)
- 유튜브 퍼가기를 하면 iframe 의 560px 너비와 315px 높이를 가진 유튜브 영상을 기본적으로 소스코드 조각을 준다. pc화면은 괜찮지만 작은 화면에 유튜브를 추가하면 영상이 넘쳐서 화면이 잘린다. 이 문제를 해결하는 것이 종횡비 유지 기법이다.
- 첫번째 해결 방법

```css
iframe {
    width: 100vw; /* Check margin or scroll */
    height: 56.25vw;
}
```

	- 하지만, body 영역에 margin이 들어간 상황에서는 body 영역의 너비와 youtube 영상의 너비가 동일해지기 때문에 왼쪽은 margin 만큼 떨어지지만 그만큼 오른쪽은 영상이 잘린다.

- 두번째 해결 방법

```css
iframe {
    width: 100%;
    height: auto;
    aspect-ratio: 100 / 56.25; /* Check caniuse. */
}
```

	- 하지만, 최근에 나온 속성이라서 사파리, 삼성 인터넷 지원을 확인해야 한다.
- 세번째 해결 방법

```css
.utube {
    position: relative;
    padding-top: 56.25%; /* 315 / 560 / 100 */
}
.utube_iframe {
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
}
```

	- 지금 현업에서 가장 많이 사용하는 방법이다.

