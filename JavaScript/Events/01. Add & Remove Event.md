# JavaScript Event: `.addEventListener`와 `.removeEventListener` 정리

JavaScript에서 **이벤트(Event)** 는 사용자와 웹 페이지 간의 상호작용(예: 클릭, 입력, 스크롤 등)을 처리하는 중요한 메커니즘입니다. 이벤트를 처리하기 위해 **`.addEventListener`**와 **`.removeEventListener`** 메서드를 사용하여 이벤트 리스너를 추가하거나 제거할 수 있습니다. 이 문서에서는 두 메서드의 개념과 사용법을 정리합니다.

---

## 📖 이벤트란?

- **이벤트(Event)**는 사용자가 웹 페이지에서 수행하는 작업(클릭, 키보드 입력, 마우스 이동 등) 또는 브라우저에서 발생하는 작업(페이지 로드, 네트워크 요청 등)을 나타냅니다.
- 이벤트를 처리하기 위해 **이벤트 리스너(Event Listener)**를 사용하여 특정 동작을 실행할 수 있습니다.

---

## 📂 `.addEventListener()`

### **개념**
- **`.addEventListener()`**는 특정 요소에 이벤트 리스너를 추가하여 지정된 이벤트가 발생했을 때 실행할 함수를 등록합니다.
- 하나의 요소에 여러 개의 이벤트 리스너를 추가할 수 있습니다.

### **구문**
```
element.addEventListener(eventType, listener, options);
```

- **`eventType`**: 처리할 이벤트 유형 (예: `"click"`, `"keyup"`, `"submit"` 등).
- **`listener`**: 이벤트 발생 시 실행할 콜백 함수.
- **`options`**: 선택적 옵션 객체(예: `capture`, `once`, `passive`).

---

### **예제**

#### 1. 클릭 이벤트 추가
HTML:
```
<button id="myButton">Click Me</button>
```

JavaScript:
```
const button = document.getElementById("myButton");

button.addEventListener("click", () => {
    console.log("Button clicked!");
});
// 버튼 클릭 시 "Button clicked!" 출력
```

#### 2. 키보드 입력 이벤트 추가
HTML:
```
<input type="text" id="myInput" placeholder="Type something...">
```

JavaScript:
```
const input = document.getElementById("myInput");

input.addEventListener("keyup", (event) => {
    console.log(`Key pressed: ${event.key}`);
});
// 키보드 입력 시 눌린 키 출력
```

#### 3. 옵션 사용 (`once`, `capture`, `passive`)
- **`once`:** 이벤트가 한 번만 실행되도록 설정.
- **`capture`:** 캡처링 단계에서 이벤트를 처리.
- **`passive`:** 스크롤 성능 최적화를 위해 기본 동작을 방지하지 않도록 설정.

JavaScript:
```
const button = document.getElementById("myButton");

// 한 번만 실행
button.addEventListener("click", () => {
    console.log("This will run only once!");
}, { once: true });

// 캡처링 단계에서 실행
button.addEventListener("click", () => {
    console.log("Capture phase listener");
}, { capture: true });

// 스크롤 성능 최적화
window.addEventListener("scroll", () => {
    console.log("Scrolling...");
}, { passive: true });
```

---

## 📂 `.removeEventListener()`

### **개념**
- **`.removeEventListener()`**는 요소에 등록된 이벤트 리스너를 제거합니다.
- 제거하려면 동일한 `eventType`, `listener`, `options`로 등록된 리스너를 지정해야 합니다.

### **구문**
```
element.removeEventListener(eventType, listener, options);
```

- **`eventType`**: 제거할 이벤트 유형.
- **`listener`**: 제거할 콜백 함수.
- **`options`**: 선택적 옵션 객체(등록 시 사용한 옵션과 동일해야 함).

---

### **예제**

#### 1. 클릭 이벤트 제거
HTML:
```
<button id="myButton">Click Me</button>
```

JavaScript:
```
const button = document.getElementById("myButton");

function handleClick() {
    console.log("Button clicked!");
}

// 이벤트 리스너 추가
button.addEventListener("click", handleClick);

// 이벤트 리스너 제거
button.removeEventListener("click", handleClick);
```

#### 2. 익명 함수는 제거 불가
익명 함수로 등록된 리스너는 제거할 수 없습니다.
```
button.addEventListener("click", () => {
    console.log("This cannot be removed!");
});

// removeEventListener로 익명 함수 제거 불가능
button.removeEventListener("click", () => {
    console.log("This cannot be removed!");
});
```

---

## 📂 실용적인 활용 사례

### 1. 동적 버튼 생성 및 클릭 처리
HTML:
```
<div id="container"></div>
<button id="addButton">Add Button</button>
```

JavaScript:
```
const container = document.getElementById("container");
const addButton = document.getElementById("addButton");

addButton.addEventListener("click", () => {
    const newButton = document.createElement("button");
    newButton.textContent = "New Button";
    container.appendChild(newButton);

    newButton.addEventListener("click", () => {
        console.log("New button clicked!");
    });
});
```

---

### 2. 스크롤 이벤트 최적화 (Passive 옵션)
HTML:
```
<div style="height: 2000px;">Scroll down</div>
```

JavaScript:
```
window.addEventListener(
    "scroll",
    () => {
        console.log(`Scroll position: ${window.scrollY}`);
    },
    { passive: true }
);
```

---

### 3. 특정 조건에서 이벤트 리스너 제거
HTML:
```
<button id="myButton">Click Me</button>
<p id="message"></p>
```

JavaScript:
```
const button = document.getElementById("myButton");
const message = document.getElementById("message");

function handleClick() {
    message.textContent = "You clicked the button!";
    button.removeEventListener("click", handleClick); // 클릭 후 리스너 제거
}

button.addEventListener("click", handleClick);
```

---

## 📂 주요 차이점 및 주의사항

1. **익명 함수와 리스너 제거**
   - 익명 함수로 등록된 리스너는 동일한 참조를 제공할 수 없으므로 `removeEventListener()`로 제거할 수 없습니다.

2. **옵션 일치**
   - `addEventListener()`와 `removeEventListener()`에서 동일한 옵션을 사용해야 리스너가 제대로 제거됩니다.

3. **캡처링과 버블링**
   - 기본적으로 DOM 이벤트는 버블링 단계에서 처리됩니다.
   - 캡처링 단계에서 처리하려면 `{ capture: true }` 옵션을 설정해야 합니다.

---

## ✨ 요약

| 메서드                  | 설명                                                                 | 예제                                      |
|-------------------------|----------------------------------------------------------------------|------------------------------------------|
| `.addEventListener()`   | 요소에 이벤트 리스너 추가                                             | `.addEventListener('click', handler)`     |
| `.removeEventListener()`| 요소에 등록된 이벤트 리스너 제거                                      | `.removeEventListener('click', handler)` |
| 옵션                    | `{ once, capture, passive }`                                         | `{ once: true } → 한 번만 실행`          |

---
