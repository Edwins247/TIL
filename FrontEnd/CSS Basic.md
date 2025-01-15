# CSS 기본 개념 및 선택자 정리

CSS(Cascading Style Sheets)는 HTML 요소에 스타일을 적용하기 위한 언어입니다. CSS는 선택자와 속성을 사용하여 웹 페이지의 디자인과 레이아웃을 정의합니다. 아래는 CSS의 기본 개념과 선택자, 그리고 주요 특징을 체계적으로 정리한 내용입니다.

---

## 📖 CSS의 기본 구조

CSS는 다음과 같은 형식으로 작성됩니다:

```
선택자 {
  속성: 값;
}
```

- **선택자(Selector)**: 스타일을 적용할 HTML 요소를 지정.
- **속성(Property)**: 스타일의 종류를 정의.
- **값(Value)**: 스타일의 구체적인 값을 설정.

#### 예시:

```
p {
  color: blue; /* 글자 색상을 파란색으로 설정 */
  font-size: 16px; /* 글자 크기를 16px로 설정 */
}
```

---

## 🛠️ CSS 작성 방식

1. **내장 방식**
   - `<style>` 태그 내에 CSS를 작성.
   - 프로젝트 번들링 시 사용되기도 하지만, 직접 사용하는 것은 지양.
   ```
   <style>
     p {
       color: blue;
     }
   </style>
   ```

2. **인라인 방식**
   - HTML 요소의 `style` 속성에 직접 작성.
   - 선택자가 없으며, 특정 요소에만 적용.
   ```
   <p style="color: blue;">파란색 텍스트</p>
   ```

3. **링크 방식**
   - `<link>` 태그를 사용해 외부 CSS 파일 연결(병렬 방식).
   ```
   <link rel="stylesheet" href="styles.css">
   ```

4. **@import 방식**
   - CSS 파일에서 다른 CSS 파일을 가져오는 방식(직렬 방식).
   ```
   @import url("reset.css");
   ```

---

## 🔑 CSS 선택자

### **1. 기본 선택자**

| 선택자         | 설명                                       | 예시                          |
|----------------|--------------------------------------------|-------------------------------|
| `*`           | 모든 요소 선택                              | `* { margin: 0; }`           |
| 태그 선택자    | 해당 태그 이름으로 요소 선택                | `p { color: red; }`          |
| 클래스 선택자  | 클래스 속성 값으로 요소 선택 (`.class`)      | `.box { background: gray; }` |
| 아이디 선택자  | 아이디 속성 값으로 요소 선택 (`#id`)         | `#header { font-size: 20px; }` |

---

### **2. 복합 선택자**

| 선택자                     | 설명                                           | 예시                           |
|----------------------------|------------------------------------------------|--------------------------------|
| `span.orange`              | 태그와 클래스 모두 만족하는 요소               | `span.orange { color: orange; }` |
| `ul > li`                  | 부모-자식 관계에서 자식 요소만 선택            | `ul > li { list-style: none; }` |
| `div .item`                | 특정 요소의 하위(후손) 요소 선택               | `div .item { padding: 10px; }` |
| `.box + p`                 | 특정 요소의 바로 다음 형제 요소 선택           | `.box + p { margin-top: 20px; }` |
| `.box ~ p`                 | 특정 요소 이후 모든 형제 요소 선택             | `.box ~ p { color: gray; }`    |

---

### **3. 가상 클래스**

가상 클래스는 특정 상태에서 동작하는 스타일을 정의합니다:

| 가상 클래스      | 설명                                              | 예시                          |
|------------------|---------------------------------------------------|-------------------------------|
| `:hover`         | 마우스 커서가 올라간 동안                         | `a:hover { color: red; }`     |
| `:active`        | 클릭 중인 동안                                    | `button:active { opacity: 0.8; }` |
| `:focus`         | 포커스된 동안                                     | `input:focus { border-color: blue; }` |
| `:first-child`   | 형제 중 첫 번째 자식                              | `li:first-child { font-weight: bold; }` |
| `nth-child(n)`   | 형제 중 n번째 자식                                | `li:nth-child(2n) { color: green; }` |

---

### **4. 가상 요소**

가상 요소는 HTML 문서에 실제로 존재하지 않는 콘텐츠를 삽입합니다:

| 가상 요소        | 설명                                              | 예시                          |
|------------------|---------------------------------------------------|-------------------------------|
| `::before`       | 요소 내부 앞에 콘텐츠 삽입                        | 
```
h1::before {
  content: "🔥 ";
}
```
결과:
🔥 제목 텍스트

---

### **5. 속성 선택자**

속성을 기준으로 특정 요소를 선택할 수 있습니다:

| 속성 선택자      | 설명                                              | 예시                          |
|------------------|---------------------------------------------------|-------------------------------|
| `[attr]`         | 특정 속성을 가진 모든 요소                        | `[disabled] { opacity: 0.5; }` |
| `[attr="value"]` | 특정 속성과 값을 가진 모든 요소                   | `[type="text"] { width: 100%; }` |

---

## 🎨 스타일 상속과 우선순위

### **1. 스타일 상속**
- 상위(부모) 요소의 스타일이 하위(자식) 요소에 전달되는 것.
- 글꼴 관련 속성은 기본적으로 상속됩니다:
```
body {
  font-family: Arial, sans-serif;
}
p {
  color: gray;
}
```
결과:
모든 `<p>` 태그는 회색 텍스트와 Arial 폰트를 상속받음.

- 강제 상속:
```
h1 {
  font-size: inherit;
}
```

### **2. 우선순위**
CSS 선언은 우선순위 점수에 따라 적용됩니다:
1. 인라인 스타일 (`1000점`)
2. 아이디 선택자 (`100점`)
3. 클래스/속성/가상 클래스 (`10점`)
4. 태그/가상 요소 (`1점`)
5. 전체 선택자 (`0점`)
6. 동일 점수일 경우, 가장 마지막 선언이 우선. / !important의 경우 우선순위 무조건 먼저

![우선순위 점수표 이미지 예시](https://private-user-images.githubusercontent.com/144297891/403205127-3741c0c1-1111-4c0e-b0b7-7ec1bae06dce.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MzY5MDg2NTQsIm5iZiI6MTczNjkwODM1NCwicGF0aCI6Ii8xNDQyOTc4OTEvNDAzMjA1MTI3LTM3NDFjMGMxLTExMTEtNGMwZS1iMGI3LTdlYzFiYWUwNmRjZS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMTE1JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDExNVQwMjMyMzRaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0zZWNlNDA2YmFjOTA1YWE2NGY1Yjg1NDRmYTViNDY3MzJjYWI1YmEzODRiYjcyZTg2NDdhMjA3YmE5MzJmOTAwJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.gTxz4J2_LeaVgET-7qsGTj3proB7AathikwyVjizbd4)

---
