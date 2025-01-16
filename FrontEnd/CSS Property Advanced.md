# CSS 배치 (Position) 정리

CSS의 `position` 속성은 요소의 위치를 지정하는 기준을 정의합니다. 이 속성을 활용하면 요소를 문서 흐름에서 벗어나거나 특정 기준에 따라 배치할 수 있습니다. 아래는 `position` 속성과 관련된 주요 개념과 예시를 정리한 내용입니다.

---

## 📍 Position 값

### **1. `static`**
- **기본값**으로, 문서의 일반적인 흐름에 따라 배치됩니다.
- 위치를 지정하는 `top`, `bottom`, `left`, `right` 속성이 적용되지 않습니다.

#### 예시:
```
<div style="position: static;">
  기본값(static)으로 배치된 요소
</div>
```

---

### **2. `relative`**
- **자신의 원래 위치**를 기준으로 이동합니다.
- 요소의 배치 기준이 자기 자신이기 때문에, 다른 요소들과의 상호작용에는 영향을 주지 않습니다.

#### 특징:
- 상대적으로 이동하더라도 요소가 차지하는 공간은 원래 위치에 남아 있습니다.

#### 예시:
```
<div style="position: relative; top: 20px; left: 10px;">
  상대적으로 이동한 요소
</div>
```

---

### **3. `absolute`**
- 가장 가까운 **`position`이 설정된 부모 요소**를 기준으로 위치를 지정합니다.
- 만약 부모 요소에 `position`이 설정되어 있지 않다면, 뷰포트(브라우저 창)가 기준이 됩니다.
- 문서 흐름에서 제거되므로, 다른 요소와의 상호작용이 무너질 수 있습니다.

#### 특징:
- 부모 요소에 `relative`, `absolute`, 또는 `fixed`가 설정되어 있어야 기준을 찾습니다.
- 그렇지 않으면 뷰포트를 기준으로 배치됩니다.

#### 예시:
```
<div style="position: relative;">
  <div style="position: absolute; top: 10px; left: 20px;">
    부모 요소를 기준으로 배치된 요소
  </div>
</div>
```

---

### **4. `fixed`**
- **뷰포트(브라우저 창)** 를 기준으로 위치를 고정합니다.
- 스크롤을 하더라도 화면에서 고정된 상태로 유지됩니다.

#### 예시:
```
<div style="position: fixed; bottom: 0; right: 0;">
  화면 하단에 고정된 요소
</div>
```

---

### **5. `sticky`**
- 스크롤 영역을 기준으로 특정 위치에 고정됩니다.
- 스크롤이 특정 지점에 도달하기 전까지는 일반적인 흐름을 따르며, 도달한 이후에는 고정됩니다.

#### 예시:
```
<div style="position: sticky; top: 0;">
  스크롤 시 상단에 고정되는 요소
</div>
```

---

## 🎯 Top, Bottom, Left, Right

`top`, `bottom`, `left`, `right` 속성은 요소의 각 방향별 거리를 지정합니다. 기본값은 `auto`이며, 음수 값도 사용할 수 있습니다.

#### 예시:
```
<div style="position: relative; top: -10px; left: 20px;">
  위로 10px, 오른쪽으로 20px 이동한 요소
</div>
```

---

## 📚 쌓임 순서 (Stack Order)

요소가 사용자와 얼마나 가까운지(위에 쌓이는지)를 결정하는 규칙입니다:

1. **Position 속성**이 설정된 요소(`static` 제외)가 더 위에 쌓입니다.
2. 동일한 조건에서는 **z-index 값**이 높은 요소가 더 위에 쌓입니다.
3. z-index 값도 같다면, HTML 문서에서 뒤에 작성된 요소가 더 위에 쌓입니다.

---

### **Z-Index**

`z-index` 속성은 쌓임 순서를 숫자로 지정하며, 숫자가 클수록 사용자와 가까운 위치에 쌓입니다.

#### 특징:
1. 기본값은 `auto`.
2. 부모 요소와 동일한 쌓임 순서를 가집니다.
3. 너무 큰 값을 사용하면 관리가 어려워질 수 있으므로 적절히 설정해야 합니다.

#### 예시:
```
<div style="position: relative; z-index: 1;">
  z-index가 낮은 요소
</div>
<div style="position: relative; z-index: 10;">
  z-index가 높은 요소 (위에 표시됨)
</div>
```

---

## 🖼️ Position과 Display

- `absolute` 또는 `fixed`로 설정된 경우, 해당 요소는 자동으로 **`display: block;`**으로 변경됩니다.
- 별도로 인라인 요소의 display 값을 명시하지 않아도 블록처럼 동작합니다.

#### 예시:
```
<div style="position: absolute;">
  이 요소는 자동으로 display가 block으로 변경됨
</div>
```

---

## ✨ 요약

1. **Position 값**은 문서 흐름과 배치 기준을 결정합니다.
2. **Top, Bottom, Left, Right**는 방향별 거리 조정을 제공합니다.
3. **Z-Index**는 쌓임 순서를 제어하며, 숫자가 클수록 위로 쌓입니다.
4. Absolute와 Fixed는 자동으로 Block Display로 변경됩니다.

위 내용을 통해 CSS 배치 속성을 활용하여 다양한 레이아웃을 구성할 수 있습니다.

---

# CSS Flexbox 정리

Flexbox는 **1차원 레이아웃**을 제공하며, 요소를 수평 또는 수직으로 정렬하기 위해 사용됩니다. 부모 요소(Flex Container)와 자식 요소(Flex Items) 간의 정렬과 배치를 쉽게 처리할 수 있습니다.

---

## 🧩 Flex Container (부모 요소)

Flex Container는 Flex Items(자식 요소)를 정렬하고 배치하는 기준을 제공합니다. Flex Container에 적용되는 주요 속성을 아래에 정리했습니다.

### **1. Display**
- Flex 컨테이너를 활성화하려면 부모 요소에 `display: flex;` 또는 `display: inline-flex;`를 설정합니다.
- `flex`: 블록 요소처럼 동작.
- `inline-flex`: 인라인 요소처럼 동작.

#### 예시:
```
.container {
  display: flex;
}
```

---

### **2. Flex Direction**
- 주 축(Main Axis)을 설정합니다.
- 기본값: `row`.

| 값               | 설명                                       |
|------------------|------------------------------------------|
| `row`            | 행 축(좌 → 우).                          |
| `row-reverse`    | 행 축(우 → 좌).                          |
| `column`         | 열 축(위 → 아래).                        |
| `column-reverse` | 열 축(아래 → 위).                        |

#### 예시:
```
.container {
  display: flex;
  flex-direction: row; /* 가로 방향 정렬 */
}
```

---

### **3. Flex Wrap**
- Flex Items의 줄바꿈 여부를 설정합니다.
- 기본값: `nowrap`.

| 값              | 설명                                       |
|-----------------|------------------------------------------|
| `nowrap`        | 줄바꿈 없음 (아이템이 찌그러질 수 있음).   |
| `wrap`          | 여러 줄로 묶음 (줄바꿈 허용).              |
| `wrap-reverse`  | 줄바꿈 방향 반대로 묶음.                  |

#### 예시:
```
.container {
  display: flex;
  flex-wrap: wrap;
}
```

---

### **4. Justify-Content**
- 주 축(Main Axis)의 정렬 방식을 설정합니다.
- 기본값: `flex-start`.

| 값               | 설명                                       |
|------------------|------------------------------------------|
| `flex-start`     | 시작점으로 정렬.                          |
| `flex-end`       | 끝점으로 정렬.                            |
| `center`         | 가운데 정렬.                              |
| `space-between`  | 아이템 사이 간격 균등 분배.               |
| `space-around`   | 아이템 외부 여백 균등 분배.               |

#### 예시:
```
.container {
  display: flex;
  justify-content: center;
}
```

---

### **5. Align-Content**
- 교차 축(Cross Axis)의 여러 줄 정렬 방식을 설정합니다.
- 기본값: `stretch`.

> *주의*: 이 속성은 여러 줄로 나뉘어진 경우에만 적용됩니다.

| 값               | 설명                                       |
|------------------|------------------------------------------|
| `stretch`        | 아이템을 교차 축 방향으로 늘림 (기본값).     |
| `flex-start`     | 시작점으로 정렬.                          |
| `flex-end`       | 끝점으로 정렬.                            |
| `center`         | 가운데 정렬.                              |
| `space-between`  | 아이템 사이 간격 균등 분배.               |
| `space-around`   | 아이템 외부 여백 균등 분배.               |

#### 예시:
```
.container {
  display: flex;
  align-content: space-between;
}
```

---

### **6. Align-Items**
- 교차 축(Cross Axis)의 한 줄 정렬 방식을 설정합니다.
- 기본값: `stretch`.

| 값               | 설명                                       |
|------------------|------------------------------------------|
| `stretch`        | 아이템을 교차 축 방향으로 늘림 (기본값).     |
| `flex-start`     | 시작점으로 정렬.                          |
| `flex-end`       | 끝점으로 정렬.                            |
| `center`         | 가운데 정렬.                              |
| `baseline`       | 각 줄의 문자 기준선에 맞춰 정렬.           |

#### 예시:
```
.container {
  display: flex;
  align-items: center;
}
```

---

## 🧩 Flex Items (자식 요소)

Flex Items는 Flex Container 내부에서 배치되는 개별 요소입니다. 각 아이템에 적용할 수 있는 주요 속성을 아래에 정리했습니다.

### **1. Order**
- Flex Item의 순서를 변경합니다.
- 기본값: `0`.
- 숫자가 작을수록 먼저 배치됩니다.

#### 예시:
```
.item {
  order: 2; /* 순서를 뒤로 밀기 */
}
```

---

### **2. Flex-Grow**
- Flex Item의 증가 너비 비율을 설정합니다.
- 기본값: `0`.

#### 특징:
1. 비어 있는 공간을 채우기 위해 사용됩니다.
2. 숫자가 클수록 더 많은 공간을 차지합니다.

#### 예시:
```
.item {
  flex-grow: 1; /* 비어 있는 공간을 채움 */
}
```

---

### **3. Flex-Shrink**
- Flex Item의 감소 너비 비율을 설정합니다.
- 기본값: `1`.

#### 특징:
1. 컨테이너가 줄어들 때, 아이템이 얼마나 줄어들지 결정합니다.
2. 숫자가 클수록 더 많이 줄어듭니다.

#### 예시:
```
.item {
  flex-shrink: 0; /* 크기 감소하지 않음 */
}
```

---

### **4. Flex-Basis**
- Flex Item의 공간 배분 전 기본 너비를 설정합니다.
- 기본값: `auto`.

#### 특징:
1. px, em, rem 등 단위를 사용하여 지정할 수 있습니다.
2. 이 값을 설정하면 콘텐츠 크기와 상관없이 고정된 크기를 가질 수 있습니다.

#### 예시:
```
.item {
  flex-basis: 200px; /* 기본 너비를 200px로 지정 */
}
```

---

## ✨ 요약

1. **Flex Container**는 부모 요소로서 자식 요소(Flex Items)를 배치하고 정렬하는 기준을 제공합니다.
2. **Flex Items**는 개별적으로 크기와 순서를 조정할 수 있습니다.
3. 주요 속성인 `justify-content`, `align-items`, 그리고 각종 Flex Item 속성을 조합하여 다양한 레이아웃을 구현할 수 있습니다.

위 내용을 통해 CSS Flexbox를 활용한 효율적인 레이아웃 구성이 가능합니다.

---

# CSS 전환(Transition) 및 변환(Transform) 정리

CSS의 `transition`과 `transform` 속성은 요소의 상태 변화와 시각적 효과를 부드럽게 처리하는 데 사용됩니다. 이를 활용하면 웹 페이지의 상호작용성을 높이고, 동적인 사용자 경험을 제공할 수 있습니다.

---

## 🎬 전환 (Transition)

`transition` 속성은 요소의 **전 상태와 후 상태** 간의 변화를 부드럽게 처리합니다. 이를 통해 애니메이션 없이도 자연스러운 전환 효과를 구현할 수 있습니다.

### **1. Transition 단축 속성**

단축 속성 형식:
```
transition: [property] [duration] [timing-function] [delay];
```

#### 주요 속성:
1. **`transition-property`**: 전환 효과를 적용할 속성 이름을 지정합니다.
    - 기본값: `all` (모든 속성에 적용).
    - 특정 속성만 명시적으로 지정 가능 (예: `width`, `background-color` 등).
    - 여러 속성을 콤마로 구분하여 다르게 설정 가능.

2. **`transition-duration`**: 전환 효과의 지속 시간을 설정합니다.
    - 기본값: `0s` (전환 효과 없음).
    - 초 단위(`s`)로 지정.

3. **`transition-timing-function`**: 전환 효과의 타이밍 함수를 설정합니다.
    - 기본값: `ease`.
    - 주요 값:
        - `linear`: 일정한 속도로 변화.
        - `ease`: 느리게 → 빠르게 → 느리게 (기본값).
        - `ease-in`: 느리게 → 빠르게.
        - `ease-out`: 빠르게 → 느리게.
        - `ease-in-out`: 느리게 → 빠르게 → 느리게.
        - `cubic-bezier(n,n,n,n)`: 사용자 정의 타이밍 함수.
        - `steps(n)`: n번 분할된 애니메이션.

4. **`transition-delay`**: 전환 효과가 시작되기 전 대기 시간을 설정합니다.
    - 기본값: `0s`.

#### 예시:
```
div {
  transition: background-color 0.5s ease-in-out 0.2s;
}
```

---

### **2. Transition 예제**

#### 단일 속성 전환:
```
div {
  transition: width 1s ease;
}

div:hover {
  width: 200px;
}
```

#### 다중 속성 전환:
```
div {
  transition: width 1s ease, background-color 0.5s linear;
}

div:hover {
  width: 200px;
  background-color: blue;
}
```

#### 참고 사이트:
- [Easings.net](https://easings.net/ko): 다양한 타이밍 함수 시각화.
- [MDN Easing Functions](https://developer.mozilla.org/en-US/docs/Web/CSS/easing-function).

---

## 🔄 변환 (Transform)

`transform` 속성은 요소를 이동, 크기 조정, 회전, 기울임 등의 효과를 통해 시각적으로 변형시킵니다.

### **1. Transform 함수**

#### **2D 변환**
- **이동**
    - `translate(x, y)`: x축과 y축으로 이동.
    - `translateX(x)`: x축으로 이동.
    - `translateY(y)`: y축으로 이동.

- **크기 조정**
    - `scale(x, y)`: x축과 y축 크기 조정.
    - `scaleX(x)`: x축 크기 조정.
    - `scaleY(y)`: y축 크기 조정.

- **회전**
    - `rotate(deg)`: 시계 방향으로 각도만큼 회전.

- **기울임**
    - `skew(x, y)`: x축과 y축으로 기울임.
    - `skewX(x)`: x축으로 기울임.
    - `skewY(y)`: y축으로 기울임.

- **행렬 변환**
    - `matrix(n,n,n,n,n,n)`: 2D 변환을 행렬로 정의 (복잡하여 일반적으로 사용하지 않음).

#### 예시:
```
div {
  transform: translate(50px, 100px) rotate(45deg);
}
```

---

#### **3D 변환**
- **이동**
    - `translateZ(z)`: z축으로 이동.
    - `translate3d(x, y, z)`: x, y, z축으로 이동.

- **크기 조정**
    - `scaleZ(z)`: z축 크기 조정.
    - `scale3d(x, y, z)`: x, y, z축 크기 조정.

- **회전**
    - `rotateX(deg)`: x축을 기준으로 회전.
    - `rotateY(deg)`: y축을 기준으로 회전.
    - `rotateZ(deg)`: z축을 기준으로 회전.
    - `rotate3d(x, y, z, deg)`: x, y, z축을 기준으로 회전.

- **원근법**
    - `perspective(n)`: 원근법을 적용하여 거리감을 표현합니다. 항상 transform에서 가장 앞에 작성해야 동작합니다.

- **행렬 변환**
    - `matrix3d(n,n,n,…n)`: 3D 변환을 행렬로 정의 (복잡하여 일반적으로 사용하지 않음).

#### 예시:
```
div {
  transform: perspective(1000px) rotateY(45deg);
}
```

---

### **2. Perspective**

- 하위 요소를 관찰하는 원근 거리를 설정합니다.
- px 단위로 입력하며 부모 요소에 적용됩니다.

#### 예시:
```
.container {
  perspective: 1000px;
}

.item {
  transform: rotateY(45deg);
}
```

---

### **3. Backface Visibility**

3D 변환 시 뒤집힌 면의 표시 여부를 설정합니다.

| 값         | 설명                         |
|------------|------------------------------|
| `visible`  | 뒷면 보임 (기본값).           |
| `hidden`   | 뒷면 숨김.                   |

#### 예시:
```
div {
  backface-visibility: hidden;
}
```

---

## ✨ 요약

1. **Transition**은 요소의 상태 변화 간 전환 효과를 부드럽게 처리합니다.
2. **Transform**은 요소를 이동, 크기 조정, 회전 등 다양한 방식으로 변형할 수 있습니다.
3. 원근법(`perspective`)과 뒷면 가시성(`backface-visibility`)을 활용하여 입체적인 효과를 구현할 수 있습니다.

위 내용을 통해 CSS 전환 및 변환 속성을 활용한 동적인 레이아웃과 애니메이션 효과를 구현할 수 있습니다.

---

