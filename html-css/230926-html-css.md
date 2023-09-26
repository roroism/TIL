# TODAY I LEARNED

## Learned

### 덩어리 콘텐츠 빨리 그리기

#### LCP 개선 사례 (LCP 3.6초 단축한 이야기)

##### 히어로 이미지 preload

- 히어로 이미지를 미리 로딩하는 기법
- 원래 이미지는 html body 요소 안쪽에 마크업이 되어있지만, 첫번째 히어로 이미지를 빨리 로딩하기 위해서 html head에서 미리 로딩을 한다.

```html
<head>
    <link 
        rel="preload" as="image" 
        media="(max-width:640px)" href="small.avif">
    <link 
        rel="preload" as="image" 
        media="(min-width:641px)" href="large.avif">
</head>
```

- 해상도가 640px 보다 같거나 작은 환경에서 "small.avif" 이미지를 미리 로딩한다.
- 해상도가 641px 과 같거나 크면 태블릿이나 데스크탑 해상도에서는 "large.avif" 이미지를 미리 다운로드 받는다.

##### Feature detection

- Image type 이나 Viewport width 를 감지해서 성능을 개선하는 방법이다.
- 우리가 일반적으로 사용하는 방법은 아래와 같다.

```html
<!-- UNOPTIMIZED HERO IMAGE (이미지최적화가 되어있지 않음)-->
<img src="large.jpg" alt>
```

- 이미지 회적화를 한다면 아래처럼 할 수 있다.

```html
<!-- OPTIMIZED HERO IMAGE -->
<picture>
	<!-- AVIF && SMALL SCREEN -->
    <source srcset="small.avif" type="image/avif" media="(max-width:640px)">
	<!-- AVIF && LARGE SCREEN -->
    <source srcset="large.avif" type="image/avif">
	<!-- WEBP && SMALL SCREEN -->
    <source srcset="small.webp" type="image/webp" media="(max-width:640px)">
	<!-- WEBP && LARGE SCREEN -->
    <source srcset="large.webp" type="image/webp">
	<!-- FALLBACK -->
    <img src="small.jpg" alt>
</picture>
```

- type 과 media라는 조건 구문을 붙인다.

