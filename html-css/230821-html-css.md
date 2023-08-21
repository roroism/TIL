# TODAY I LEARNED

## Learned

### Metadata - html, head

#### lang

- `<html lang="ko">` : 검색엔진이 특정 언어의 웹페이지를 검색할 때 도움을 주거나, 화면 낭독기 사용자들이 웹페이지를 읽을 때 어떤 음성 엔진을 선택해야 하는지 힌트를 주기도 한다.
- 구글은 lang 속성을 신뢰하지 않는다. 하지만 접근성 측면에서는 중요하다.

#### charset

- `<meta charset="utf-8">` : 한글 뿐만 아니라 전세계 모든 국가의 언어를 이 웹페이지에 문제없이 표시할 수 있다.
- utf-8이 표준이다.

#### name="description", content

- 사용 예 : `<meta name="description" content="A description of the page">`
- content : name에 대한 설명을 적는다.
- name="description" : content의 값을 검색엔진의 검색결과 화면에 노출된다. 검색 결과 화면에 사이트에 대한 설명을 표시해준다.

#### name="keywords", content

- 사용 예 : `<meta name="keywords" content="webtoon, adult, free, coupon, ...">`
- 구글 검색엔진은 이 값을 참고하지 않는다. 이유는 마켓터들이 이 keywords에 어뷰징을 하기 시작했기 때문.

#### name="viewport", content

- 사용 예 : `<meta name="viewport" content=width=device-width, initial-scale=1">`
- 모바일 디바이스에서 이 웹페이지가 모바일에서도 볼 수 있게 최적화 되어있는지를 검색엔진에 제공한다.

### Metadata - 구조화된 데이터

- 국내에서는 네이버 검색엔진을 많이 사용하기 때문에 네이버에도 잘 표시되어야 한다.

#### 연관채널 등록하기 - 네이버

- 네이버에서는 네이버 웹 마스터 설명 사이트에서 2가지 형식으로 구조화된 데이터를 제공해서 연관채널을 등록할 수 있도록 소개하고 있다. 1. JSON-LD 형식. 2. Microdata 형식

#### 연관채널 등록하기 - 페이스북

- https://developers.facebook.com/docs/sharing/webmasters#markup
- 페이스북은 공유 디버거가 있어서 미리 어떤식으로 노출될지 확인해 볼 수 있다. https://developers.facebook.com/tools/debug/

#### 연관채널 등록하기 - 트위터

- 트위터도 제공되는 포맷과 디버거가 있다.

