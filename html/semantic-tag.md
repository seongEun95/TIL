
# 시맨틱 태그(Semantic Tag)란?

## div만 사용하는 나의 HTML 구조?

HTML과 CSS를 배우며 코드를 작성하다 보면 어느 순간 모든 구조를 `<div>`만으로 채우고 있는 자신을 발견하게 됩니다. 처음에는 문제가 없어 보여 그대로 작성하지만, 결국 `<html>`과 `<body>`를 제외하면 전부 `<div>`...?  
이게 맞는 건지 의문이 들고, 그때 **시맨틱 태그**라는 개념을 접하게 됩니다.

---

## 시맨틱 태그란?

- "Semantic"은 **의미의, 의미론적인**이라는 뜻을 가집니다.
- **시맨틱 태그**란, 의미가 담긴 HTML 태그로 웹 문서의 구조와 역할을 명확하게 나타내는 태그를 말합니다.

### HTML5 이전

HTML5 이전에는 대부분의 레이아웃이 `<div>`로 구성되었습니다.  
예를 들어, 네이버와 같은 오래된 사이트에서는 `id="header"`와 같은 식으로 div에 id를 부여하는 방식을 사용했습니다.

### HTML5 이후

HTML5부터는 `<nav>`, `<main>`, `<section>`, `<footer>`와 같은 **시맨틱 태그**들이 등장했습니다.  
예: 토스 홈페이지 등 최신 웹사이트는 시맨틱 태그를 활용해 구조화되어 있습니다.

---

## 언제 사용하는가?

- 레이아웃을 구성할 때 **단순히 div를 사용하는 것이 아닌**, 해당 영역의 **의미**를 고려하여 시맨틱 태그를 사용합니다.
- 시맨틱 태그는 기능적으로는 `<div>`와 동일하게 **block 요소**이지만, **의미가 부여된 태그**입니다.

---

## 주요 시맨틱 태그와 용도

| 역할 및 위치             | 태그         |
|------------------------|--------------|
| 사이트 최상단, 머릿말        | `<header>`   |
| 메뉴 내비게이션            | `<nav>`      |
| 주요 본문 콘텐츠           | `<main>`     |
| 뉴스 기사, 블로그 글        | `<article>`  |
| 주제별 구역 (소개, 기능 등) | `<section>`  |
| 사이드 정보 (광고, 추천 등) | `<aside>`    |
| 페이지 하단               | `<footer>`   |

> 이 외에도 다양한 시맨틱 태그가 있으며, [MDN 문서](https://developer.mozilla.org/ko/docs/Web/HTML/Element)에서 더 많은 정보를 확인할 수 있습니다.

---

## 시맨틱 태그의 장점

### 1. 접근성 향상

- 시맨틱 태그는 웹 페이지의 구조와 역할을 명확히 전달해 **스크린 리더**와 같은 보조 기술이 페이지를 올바르게 이해할 수 있도록 돕습니다.
- 웹접근성이란, **장애인이나 고령자도 웹의 정보를 비장애인과 동등하게 접근할 수 있도록 보장하는 것**입니다.

#### 예시:

```html
<p>html을 작성할 때 <span style="font-weight: bold;">시맨틱 태그</span>를 사용하자</p>
<p>html을 작성할 때 <strong>시맨틱 태그</strong>를 사용하자</p>
```

- 두 문장의 **스타일은 동일**하지만, 스크린 리더는 `<strong>` 태그를 **강조된 음성**으로 읽어줍니다.
- 즉, 시각 장애인도 해당 부분이 중요한 내용임을 인식할 수 있습니다.

---

### 2. SEO(검색엔진 최적화)

- 검색엔진은 시맨틱 태그를 통해 콘텐츠의 구조를 파악하고, 주요 콘텐츠가 어떤 부분인지 인식합니다.
- 결과적으로 **검색 결과 노출에 긍정적인 영향**을 미칩니다.

---

### 3. 코드 가독성 및 유지보수 향상

- `<div>`로만 구성된 코드보다 의미 있는 시맨틱 태그를 사용한 코드가 **가독성**이 높고 **협업** 시 이해하기 쉽습니다.

#### 예시:

```html
<header>...</header>
<!-- vs -->
<div class="header">...</div>
```

---

## 결론

**시맨틱 태그는 단순한 마크업 작성 그 이상입니다.**  
접근성, SEO, 가독성 측면 모두에서 웹 개발의 질을 높여주는 요소입니다.  
앞으로는 의미 없는 `<div>` 대신, **적절한 시맨틱 태그를 사용하여 더 나은 HTML 문서를 작성해 보세요.**