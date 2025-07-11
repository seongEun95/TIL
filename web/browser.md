
# 브라우저를 학습해야 하는 이유

웹 프론트엔드 개발자라면 브라우저와 함께 살아야 한다.  
하지만 브라우저의 동작 원리를 모른다면, 개발 여정이 점점 어려워질 수 있다.  
사용자는 빠르고 상호작용이 원활한 콘텐츠를 원하며, 페이지 속도가 1초에서 3초가 되면 이탈률이 32% 증가한다.  
결국 브라우저 최적화는 비즈니스 성과에도 영향을 미친다.

---

# 브라우저의 렌더링 과정

## 렌더링이란?

- HTML, CSS, JS로 작성된 문서를 **브라우저에 시각적으로 출력**하는 과정

## 파싱이란?

- 문법에 맞는 문자열을 **토큰 단위로 나눈 후**, 구조화된 트리(파스트리)로 변환

## 토큰이란?

- 문법적으로 더 이상 나눌 수 없는 코드의 최소 단위  
예: `const foo = 1 + 3;` → `const`, `foo`, `=`, `1`, `+`, `3`, `;`

---

## 1. 요청과 응답

- 브라우저 주소창에 URL 입력 → DNS → IP 주소로 변환
- 해당 서버로 요청 전송
- 서버는 HTML, JS, CSS 등 리소스 응답
- 개발자도구 > 네트워크 탭에서 리소스 확인 가능

---

## 2. HTML 파싱과 DOM 생성

- HTML은 문자열 → 바이트 → 토큰 → 노드 → DOM(Document Object Model)
- 트리 구조로 HTML 요소들의 관계를 나타냄
- JavaScript로 DOM에 접근하여 조작 가능

---

## 3. CSS 파싱과 CSSOM 생성

- HTML 파싱 중 CSS 링크나 스타일 발견 시 CSS 파싱
- CSS 역시 토큰 → 노드 → CSSOM(CSS Object Model) 생성
- 상속 정보까지 반영되어 트리 구조 형성

---

## 4. 렌더트리(Render Tree) 생성

- DOM + CSSOM → 렌더트리 생성
- 화면에 표시되는 요소만 포함 (예: `display: none`은 제외)
- 이 렌더트리를 기준으로 **레이아웃 계산**과 **페인팅** 수행

---

## 5. 자바스크립트 파싱과 실행

- JS는 JS 엔진이 처리 (예: V8)
- 추상 구문 트리(AST)를 만들고 바이트코드로 변환하여 실행

---

## 6. 리플로우(Reflow)와 리페인트(Repaint)

- **리플로우**: 레이아웃 변경 시 재계산 (노드 추가/삭제, 크기 변경 등)
- **리페인트**: 요소에 색을 다시 입히는 과정
- 둘 다 브라우저 성능에 비용 큼 → 이를 줄이기 위해 **가상 DOM** 사용
- React, Vue 등은 가상 DOM 기반 프레임워크

---

# 웹사이트 성능 진단 방법

## 1. Lighthouse (크롬 개발자 도구)

- 성능, 접근성, SEO 등 종합 측정 도구
- 자동 진단 및 개선 방향 제공

## 2. PageSpeed Insights

- Google의 웹 성능 측정 도구
- URL 입력만으로 모바일/데스크탑 성능 분석 가능

## 3. 개발자 도구 > 네트워크 탭

- 리소스 로드 시간, 용량, 파일 확인 가능
- 성능 병목 원인을 분석하고 최적화에 활용

---

# 결론

브라우저의 동작 원리를 이해하는 것은 단순히 기능 구현을 넘어서  
성능, 접근성, 사용자 경험 개선에 핵심적입니다.  
웹 프론트엔드 개발자라면 반드시 브라우저 렌더링과 진단 도구를 이해하고 활용할 수 있어야 합니다.
