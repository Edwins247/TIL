# HTML 기본 개념 및 태그 정리

HTML은 웹 페이지의 구조를 정의하는 마크업 언어입니다. 본 문서는 HTML의 기본 개념과 주요 태그, 그리고 활용법을 체계적으로 정리한 자료입니다.

---

## 📖 HTML 기본 개념

### **1. DOCTYPE (Document Type Declaration)**
- HTML 문서의 **버전**을 지정하며, 웹 브라우저에게 해당 문서를 어떤 방식으로 해석해야 하는지 알려줍니다.
- HTML5에서는 다음과 같이 선언합니다:

  ```
  <!DOCTYPE html>
  ```
- 이전 버전(DTD 기반)과 달리, HTML5의 DOCTYPE은 간단하게 작성됩니다.
---

### **2. HTML 태그**
- HTML 문서의 시작과 끝을 나타내며, 문서 전체의 범위를 정의합니다.
- `lang` 속성을 통해 문서의 언어를 지정할 수 있습니다.

  ```
  <html lang="ko">
  ...
  </html>
  ```

---

### **3. Head 태그**
- 문서의 메타데이터를 정의하는 영역으로, 웹 브라우저가 처리해야 할 정보를 포함합니다.
- 주요 태그:
  - **`<title>`**: 웹 페이지의 제목을 정의하며, 브라우저 탭에 표시됩니다.
    
    ```
    <title>My Webpage</title>
    ```
  - **`<meta>`**: 문서 정보를 제공하는 태그로, 검색엔진 최적화(SEO)와 브라우저 설정에 사용됩니다.
    - `charset`: 문자 인코딩 방식을 지정 (일반적으로 UTF-8 사용).
      
      ```
      <meta charset="UTF-8">
      ```
    - `viewport`: 반응형 웹을 위한 초기 뷰포트 설정.
      
      ```
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      ```
  - **`<link>`**: 외부 리소스(CSS 파일 등)를 연결합니다.
    
    ```
    <link rel="stylesheet" href="styles.css">
    ```
  - **`<style>`**: CSS를 직접 작성하여 적용합니다.
    
    ```
    <style>
      body {
        font-family: Arial, sans-serif;
      }
    </style>
    ```
  - **`<script>`**: JavaScript 파일을 연결하거나 직접 작성합니다.
    
    ```
    <script src="script.js"></script>
    ```

---

### **4. Body 태그**
- 사용자에게 보이는 콘텐츠를 정의하는 영역으로, 웹 페이지의 구조와 요소들을 작성합니다.
- 예시:
  
  ```
  <body>
    <header>Header Section</header>
    <nav>Navigation Menu</nav>
    <main>Main Content</main>
    <footer>Footer Section</footer>
  </body>
  ```

---

## 📂 경로 설정

### **1. 상대 경로**
- 현재 파일을 기준으로 경로를 설정합니다.
  - `./`: 현재 디렉토리.
    
  - `../`: 상위 디렉토리.
    
  ```
  <a href="./about.html">About</a>
  ```

### **2. 절대 경로**
- 루트 디렉토리 또는 원격 URL을 기준으로 경로를 설정합니다.
  - `/`: 루트 디렉토리 기준.
    
  - `http(s)://`: 원격 URL 경로.
    
  ```
  <a href="/home">Home</a>
  ```
---

## 🌐 주요 태그 및 활용

### **1. `<a>` 태그**
- 다른 페이지나 리소스로 이동할 수 있는 하이퍼링크를 생성합니다.
- 절대 경로와 상대 경로 모두 사용 가능하며, 하위 페이지 연결 시 `index.html`이 기본적으로 참조됩니다.
  
  ```
  <a href="contact.html">Contact Us</a>
  ```

---

## 🔧 개발 도구 활용

### **1. 개발자 도구**
- 브라우저에서 제공하는 개발자 도구(DevTools)를 활용해 HTML과 CSS를 분석하고 수정할 수 있습니다.
- 주요 탭:
  - **Elements**: DOM 요소와 스타일 확인 및 임시 수정 가능.
  - **Computed**: 실제 적용된 스타일 확인 가능.
  - **Hov (Hover)**: 특정 상태(예: hover 효과)를 테스트.

### **2. CodePen.io**
- 간단한 코드 테스트 및 프로토타이핑 도구로, 프로젝트 생성 없이 코드 실행이 가능합니다.

---

## 🎨 브라우저 스타일 초기화

브라우저는 기본 스타일(여백 등)을 제공하므로 이를 초기화하는 것이 중요합니다:
1. Reset CSS 사용:
   
   ```
   <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/meyer-reset/2.0/reset.min.css">
   ```

2. CodePen 설정에서 기본 스타일 초기화 가능.

---

## ⚡ Emmet (VS Code)
- VS Code에서 제공하는 기능으로, 짧은 입력만으로 HTML 태그를 자동 완성할 수 있습니다.
  
- 예시:
  
  입력: `div.container>ul>li*3`
  
  결과:
  
  ```
  <div class="container">
    <ul>
      <li></li>
      <li></li>
      <li></li>
    </ul>
  </div>
  ```
