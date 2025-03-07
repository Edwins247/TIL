# CSS 속성 기본 정리

CSS 속성은 HTML 요소의 스타일과 레이아웃을 정의하는 데 사용됩니다. 각 속성을 이해하고 활용하면, 요소가 화면에 어떻게 렌더링될지 예측하며 작업할 수 있습니다. 특히 요소의 크기, 여백, 배경 등은 웹 페이지의 레이아웃과 디자인에 큰 영향을 미칩니다.

---

## 📦 박스 모델

HTML 요소는 **박스 모델(Box Model)** 을 기반으로 크기와 여백을 계산합니다. 박스 모델은 다음과 같은 구성 요소로 이루어져 있습니다:
1. **Content**: 콘텐츠 영역.
2. **Padding**: 콘텐츠와 테두리 사이의 내부 여백.
3. **Border**: 테두리.
4. **Margin**: 테두리와 외부 요소 사이의 외부 여백.

### **1. 너비와 높이**

| 속성              | 설명                                                                 |
|-------------------|----------------------------------------------------------------------|
| `width`, `height` | 요소의 가로/세로 크기를 지정합니다. 기본값은 `auto`.                  |
| `max-width`, `max-height` | 요소가 커질 수 있는 최대 크기를 지정합니다. 기본값은 `none`.         |
| `min-width`, `min-height` | 요소가 작아질 수 있는 최소 크기를 지정합니다. 기본값은 `0`.           |

#### **인라인 vs 블록 요소**
- **인라인 요소**: `width`와 `height`를 명시적으로 설정할 수 없으며, 콘텐츠 크기에 따라 자동 조정됩니다.
- **블록 요소**: 기본적으로 부모 요소의 너비를 가득 채우며, 높이는 콘텐츠 크기에 따라 조정됩니다.
- 각각을 섞어서 parent-child 관계에서 조정할 수 있음(child가 경우에 따라 커질수도)

#### 예시:
```
div {
  width: 50%; /* 부모 요소의 50% */
  max-width: 800px; /* 최대 너비 800px */
  min-height: 200px; /* 최소 높이 200px */
}
```

---

### **2. 단위**

CSS에서는 다양한 단위를 사용하여 크기를 정의할 수 있습니다:

| 단위      | 설명                                                                 |
|-----------|----------------------------------------------------------------------|
| `px`      | 픽셀(절대 단위).                                                    |
| `%`       | 부모 요소를 기준으로 한 백분율(상대 단위).                           |
| `em`      | 현재 요소의 글꼴 크기를 기준으로 한 배수(상대 단위).                 |
| `rem`     | 루트 요소(`<html>`)의 글꼴 크기를 기준으로 한 배수(상대 단위).       |
| `vw`, `vh`| 뷰포트의 너비/높이를 기준으로 한 백분율(상대 단위).                  |

#### **em vs rem**
- `em`: 현재 요소의 글꼴 크기를 기준으로 계산.
- `rem`: 루트 요소(`<html>`)의 글꼴 크기를 기준으로 계산.

#### 예시:
```
p {
  font-size: 2rem; /* 루트 폰트 크기의 2배 */
  width: 50vw; /* 뷰포트 너비의 50% */
}
```

---

### **3. 여백**

#### **(1) Margin**
- 외부 여백을 지정하며, 기본값은 `0`.
- 음수 값도 가능하며, `margin: auto;`를 사용하면 가로 방향 가운데 정렬이 가능합니다.
- 단축 속성으로 사용 시 입력 값 개수에 따라 적용 방식이 다릅니다:
    - 하나 값: 모든 방향 동일.
    - 두 값: 위/아래, 좌/우.
    - 세 값: 위, 좌/우, 아래.
    - 네 값: 위, 오른쪽, 아래, 왼쪽 (시계방향).

#### 예시:
```
div {
  margin: 10px auto; /* 위아래 여백은 10px, 좌우는 가운데 정렬 */
}
```

#### **(2) Padding**
- 내부 여백을 지정하며, 부모 요소의 가로 너비를 기준으로 비율 설정 가능합니다.
- Padding은 콘텐츠 영역을 확장시키기 때문에 요소의 전체 크기가 커집니다.

#### 예시:
```
div {
  padding: 20px; /* 모든 방향에 대해 내부 여백 20px */
}
```

---

### **4. 테두리**

테두리는 다음 세 가지 속성을 조합하여 지정합니다:
1. `border-width`: 테두리 두께.
2. `border-style`: 테두리 스타일 (예: solid, dashed, dotted).
3. `border-color`: 테두리 색상.
4. 요소의 크기가 커짐.

#### 단축 속성:
```
div {
  border: 2px solid #000; /* 두께, 스타일, 색상을 한 번에 지정 */
}
```

#### 개별 속성:
```
div {
  border-top-width: 5px;
  border-right-style: dashed;
}
```

#### **(1) Border-Radius**
- 모서리를 둥글게 깎습니다. 각 모서리를 개별적으로 설정하거나 단축 속성을 사용할 수 있습니다.

```
div {
  border-radius: 10px; /* 모든 모서리를 둥글게 */
}
```

---

### **5. Box-Sizing**

요소의 크기 계산 방식을 정의합니다:
- 기본값인 `content-box`는 콘텐츠 영역만 크기로 계산합니다.
- `border-box`는 콘텐츠 + 패딩 + 테두리를 포함하여 크기를 계산합니다.

> *Tip*: 패딩이나 테두리가 추가될 때 전체 크기가 변하지 않도록 하려면 `box-sizing: border-box;`를 사용하는 것이 좋습니다.

#### 예시:
```
div {
  box-sizing: border-box;
}
```

---

### **6. Overflow**

요소의 크기를 초과한 콘텐츠를 처리하는 방법을 정의합니다:
- 기본값은 `visible`.
- 주요 값:
    - `hidden`: 초과된 내용 숨김.
    - `scroll`: 스크롤바 생성.
    - `auto`: 초과된 경우에만 스크롤바 생성.

#### 예시:
```
div {
  overflow: auto;
}
```

---

### **7. Display**

요소의 화면 출력 특성을 정의합니다:
- 기본값은 각 HTML 태그에 따라 다릅니다 (`block`, `inline` 등).
- 주요 값:
    - `block`: 블록 요소처럼 동작.
    - `inline`: 인라인 요소처럼 동작.
    - `inline-block`: 인라인 + 블록 특성 혼합.
    - `flex`: 플렉스 박스 레이아웃.
    - `grid`: 그리드 레이아웃.

#### 예시:
```
span {
  display: inline-block;
}
```

---

## ✨ 글꼴 관련 속성

### **1. Font Properties**

| 속성           | 설명                                                                 |
|----------------|----------------------------------------------------------------------|
| `font-style`   | 글자의 기울기 (`normal`, `italic`).                                  |
| `font-weight`  | 글자의 두께 (`normal`, `bold`, 또는 숫자 값).                         |
| `font-size`    | 글자의 크기 (기본값은 `16px`).                                       |
| `line-height`  | 한 줄의 높이 (행간).                                                |
| `font-family`  | 글꼴(서체) 지정 (여러 개 작성 가능하며 마지막에 계열 필수).          |

#### 예시:
```
p {
  font-family: "Arial", sans-serif;
  font-size: 18px;
}
```

---

## 🖋️ 문자 관련 속성

### **1. Text Properties**

| 속성                | 설명                                                             |
|---------------------|------------------------------------------------------------------|
| `color`             | 글자의 색상 (`rgb`, Hex 코드 등 사용 가능).                      |
| `text-align`        | 텍스트 정렬 방식 (`left`, center 등).                            |
| `text-decoration`   | 텍스트 장식 (`none`, underline 등).                              |
| `text-indent`       | 문자 들여쓰기, 음수 사용시 내어쓰기 (`0`, 숫자 사용).              |

#### 예시:
```
h1 {
  color: #333;
  text-align: center;
}
```

---

## 🎨 배경 관련 속성

### **1. Background Properties**

| 속성                  | 설명                                                                 |
|-----------------------|----------------------------------------------------------------------|
| `background-color`    | 배경 색상 지정 (`transparent`이 기본값).                            |
| `background-image`    | 배경 이미지 삽입 (`url()` 사용).                                    |
| `background-repeat`   | 배경 이미지 반복 방식 (`repeat-x`, 또는 no-repeat 등).               |
| `background-position` | 배경 이미지 위치 (`0% 0%`가 기본값, x-y축 위치 직접 지정 가능).       |
| `background-size`     | 배경 이미지 크기 (`auto`가 기본값, `cover`, `contain` 등).           |
| `background-attachment`| 배경 이미지 스크롤 특성 (`scroll`이 기본값, 또는 `fixed` ).          |

#### 예시:
```
div {
  background-color: #f0f0f0;
  background-image: url("background.jpg");
  background-repeat: no-repeat;
  background-position: center center /*(or 50% 50%)*/;
  background-size: cover;
  background-attachment: fixed;
}
```

---
