# TODAY I LEARNED

## Learned

### Vite

- Vite(프랑스어로 "빠르다(Quick)"를 의미합니다.

#### Vite를 사용하는 이유

**vite 의 가장 큰 장점은 빌드 속도나 새로운 코드를 적용했을때의 반영 속도 같은 Feedback 속도의 엄청난 개선 때문입니다.**

브라우저에서 ESM(ES Modules)을 지원하기 전까지, JavaScript 모듈화를 네이티브 레벨에서 진행할 수 없었습니다. 그래서 소스 모듈을 브라우저에서 실행할 수 있는 파일로 크롤링, 처리 및 연결하는 "번들링(Bundling)"이라는 해결 방법을 사용해야 했습니다.

Webpack, Rollup 그리고 Parcel과 같은 도구는 이런 번들링 작업을 진행해줌으로써 프런트엔드 개발자의 생산성을 크게 향상시켰습니다.

하지만 애플리케이션이 점점 더 발전함에 따라 처리해야 하는 JavaScript 모듈의 개수도 극적으로 증가하고 있습니다. 심지어 수천 개의 모듈이 존재하는 것도 대규모 프로젝트에서는 그리 드문 일이 아닙니다. 이러한 상황에서 JavaScript 기반의 도구는 성능 병목 현상이 발생되었고, 종종 개발 서버를 가동하는 데 비합리적으로 오랜 시간을 기다려야 한다거나 HMR을 사용하더라도 변경된 파일이 적용될 때 까지 수 초 이상 소요되곤 했습니다. 이와 같은 느린 피드백 루프는 개발자의 생산성과 행복에 적지 않은 영향을 줄 수 있습니다.

Vite는 이러한 것에 초점을 맞춰, 브라우저에서 지원하는 ES Modules(ESM) 및 네이티브 언어로 작성된 JavaScript 도구 등을 활용해 문제를 해결하고자 합니다.

#### Vite을 이용해서 속도 개선을 하는 방법

- Vite에서는 느린 서버 시작 속도와 느린 서버 업데이트 속도를 개선합니다.
- Typescript Transpiling 속도가 빠릅니다.

##### 기존 방식(느린 서버 시작 속도)

개발 서버를 스타트할 때 번들러(webpack 등) 기반 빌드 설정은 서비스를 제공하기 전에 전체 애플리케이션을 열심히 크롤링하고 빌드해야 합니다.

##### 개선 방식(느린 서버 시작 속도)

Dependencies들의 대부분은 자주 변경되지 않는 일반 JavaScript이고, 일부 큰 종속성(예: 수백 개의 모듈이 있는 구성 요소 라이브러리)도 처리하는 데 비용이 많이 듭니다.

- 하지만, Vite는 esbuild를 사용하여 종속성을 사전 번들로 제공합니다. esbuild는 Go로 작성되었으며 JavaScript 기반 번들러보다 10~100배 더 빠르게 종속성을 사전 번들링합니다.

- 그리고 Vite는 기본 ESM을 통해 소스 코드를 제공합니다. 이것은 본질적으로 브라우저가 번들러 작업의 일부를 인계받게 할 수 있습니다. Vite는 브라우저가 요청할 때 요청에 따라 소스 코드를 변환하고 제공하기만 하면 됩니다. 조건부 동적 가져오기 뒤에 있는 코드는 현재 화면에서 실제로 사용되는 경우에만 처리됩니다.

##### 기존 방식(느린 서버 업데이트 속도)

번들러 기반 빌드 설정에서 파일을 편집할 때 명백한 이유로 전체 번들을 다시 빌드하는 것은 비효율적입니다. 업데이트 속도는 앱 크기에 따라 선형적으로(linearly) 저하됩니다.

##### 개선 방식(느린 서버 업데이트 속도)

일부 번들러에서 개발 서버는 파일이 변경될 때 모듈 그래프의 일부만 무효화하면 되지만 전체 번들을 다시 구성하고 웹 페이지를 다시 로드해야 하도록 메모리에서 번들링을 실행합니다. 번들을 재구성하는 데 비용이 많이 들 수 있으며 페이지를 다시 로드하면 애플리케이션의 현재 상태가 손상됩니다. 이것이 일부 번들러가 핫 모듈 교체(HMR)를 지원하는 이유입니다.

Vite는 페이지의 나머지 부분에 영향을 주지 않고 모듈 자체를 "Hot Module Replacement"할 수 있습니다.

이것은 DX (developer experience)를 크게 향상시킵니다.

##### Typescript Transpiling 속도

- Vite을 이용하면 기본적으로 Typescript 사용을 지원하며, esbuild (go로 쓰여있기 때문에 훨씬 빠릅니다)를 이용해서 transpiling 하기 때문에 훨씬 빠른 속도로 할 수 있으며, 하지만 타입 checking 기능은 없습니다.(어짜피 에디터에서 하기 때문) 그 이유는 이미 에디터 내에서 다른 것들이 타입 체킹을 하기 때문에 transpiling 만 제공합니다.
