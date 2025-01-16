# JavaScript DOM 조작 메서드 정리

JavaScript의 DOM(Document Object Model)은 웹 페이지의 구조를 동적으로 조작할 수 있는 다양한 메서드와 속성을 제공합니다. 이 문서에서는 DOM 조작과 관련된 주요 메서드와 속성인 **`document.createElement`**, **`E.prepend`**, **`E.append`**, **`E.remove`**, **`E.insertAdjacentElement`**, **`N.insertBefore`**, **`N.contains`**, **`N.textContent`**, **`E.innerHTML`**에 대해 정리합니다.

---

## 📂 DOM 조작 메서드

### **1. `document.createElement()`**

#### **개념**
- 새로운 HTML 요소를 생성합니다.
- 생성된 요소는 DOM에 추가되기 전까지는 독립적으로 존재합니다.

#### **예제**
```
const newDiv = document.createElement("div");
newDiv.textContent = "Hello, World!";
console.log(newDiv); // <div>Hello, World!</div>
```

---

### **2. `E.prepend()`**

#### **개념**
- 요소의 첫 번째 자식으로 새 노드를 추가합니다.
- 텍스트 노드도 추가할 수 있습니다.

#### **예제**
HTML:
```
<div id="container">
  <p>Last Child</p>
</div>
```

JavaScript:
```
const container = document.getElementById("container");
const newParagraph = document.createElement("p");
newParagraph.textContent = "First Child";
container.prepend(newParagraph);
// 결과: <div id="container"><p>First Child</p><p>Last Child</p></div>
```

---

### **3. `E.append()`**

#### **개념**
- 요소의 마지막 자식으로 새 노드를 추가합니다.
- 텍스트 노드도 추가할 수 있습니다.

#### **예제**
HTML:
```
<div id="container">
  <p>First Child</p>
</div>
```

JavaScript:
```
const container = document.getElementById("container");
const newParagraph = document.createElement("p");
newParagraph.textContent = "Last Child";
container.append(newParagraph);
// 결과: <div id="container"><p>First Child</p><p>Last Child</p></div>
```

---

### **4. `E.remove()`**

#### **개념**
- DOM에서 요소를 제거합니다.

#### **예제**
HTML:
```
<div id="container">
  <p id="removeMe">Remove Me</p>
</div>
```

JavaScript:
```
const elementToRemove = document.getElementById("removeMe");
elementToRemove.remove();
// 결과: <div id="container"></div>
```

---

### **5. `E.insertAdjacentElement()`**

#### **개념**
- 지정된 위치에 새 요소를 삽입합니다.
- 위치는 다음 중 하나로 지정됩니다:
  - `"beforebegin"`: 요소 이전.
  - `"afterbegin"`: 요소의 첫 번째 자식 이전.
  - `"beforeend"`: 요소의 마지막 자식 이후.
  - `"afterend"`: 요소 이후.

#### **예제**
HTML:
```
<div id="container">
  <p>Child</p>
</div>
```

JavaScript:
```
const container = document.getElementById("container");
const newDiv = document.createElement("div");
newDiv.textContent = "New Element";

container.insertAdjacentElement("beforebegin", newDiv);
// 결과: <div>New Element</div><div id="container"><p>Child</p></div>
```

---

### **6. `N.insertBefore()`**

#### **개념**
- 참조 노드 앞에 새 노드를 삽입합니다.

#### **예제**
HTML:
```
<ul id="list">
  <li>Item 2</li>
</ul>
```

JavaScript:
```
const list = document.getElementById("list");
const newItem = document.createElement("li");
newItem.textContent = "Item 1";

list.insertBefore(newItem, list.firstChild);
// 결과: <ul id="list"><li>Item 1</li><li>Item 2</li></ul>
```

---

## 📂 DOM 탐색 및 내용 조작 속성

### **7. `N.contains()`**

#### **개념**
- 특정 노드가 현재 노드의 자손인지 확인합니다.
- 포함되어 있으면 `true`, 그렇지 않으면 `false`.

#### **예제**
HTML:
```
<div id="parent">
  <span id="child">Child Node</span>
</div>
```

JavaScript:
```
const parent = document.getElementById("parent");
const child = document.getElementById("child");

console.log(parent.contains(child)); // true
console.log(parent.contains(document.body)); // false
```

---

### **8. `N.textContent`**

#### **개념**
- 요소의 모든 텍스트 콘텐츠를 반환하거나 설정합니다.
- HTML 태그는 무시하고 순수 텍스트만 반환합니다.

#### **예제**
HTML:
```
<div id="content">
  <b>Hello</b>, World!
</div>
```

JavaScript:
```
// 읽기
const content = document.getElementById("content");
console.log(content.textContent); // "Hello, World!"

// 쓰기
content.textContent = "New Text";
// 결과: <div id="content">New Text</div>
```

---

### **9. `E.innerHTML`**

#### **개념**
- 요소의 HTML 콘텐츠를 반환하거나 설정합니다.
- HTML 태그와 텍스트를 포함하여 반환하며, 설정 시 기존 내용을 덮어씁니다.

#### 주의:
- 사용자 입력을 포함한 데이터를 설정할 때는 XSS(크로스 사이트 스크립팅) 공격에 주의해야 합니다.

#### 예제**
HTML:
```
<div id="content">
  <b>Hello</b>, World!
</div>
```

JavaScript:
```
// 읽기
const content = document.getElementById("content");
console.log(content.innerHTML); // "<b>Hello</b>, World!"

// 쓰기
content.innerHTML = "<i>New Content</i>";
// 결과: <div id="content"><i>New Content</i></div>
```

---

## ✨ 요약

| 메서드/속성                  | 설명                                                                 | 예제                                      |
|-----------------------------|----------------------------------------------------------------------|------------------------------------------|
| `document.createElement()`   | 새로운 HTML 요소 생성                                                | `createElement('div') → <div>`           |
| `E.prepend()`                | 첫 번째 자식으로 새 노드 추가                                         | `.prepend(newNode)`                      |
| `E.append()`                 | 마지막 자식으로 새 노드 추가                                         | `.append(newNode)`                       |
| `E.remove()`                 | 현재 요소를 DOM에서 제거                                             | `.remove()`                              |
| `E.insertAdjacentElement()`  | 지정된 위치에 새 요소 삽입                                           | `.insertAdjacentElement('beforebegin', el)`|
| `N.insertBefore()`           | 참조 노드 앞에 새 노드 삽입                                          | `.insertBefore(newNode, referenceNode)`  |
| `N.contains()`               | 특정 노드가 현재 노드의 자손인지 확인                                | `.contains(childNode) → true/false`      |
| `N.textContent`              | 순수 텍스트 반환 또는 설정                                           | `.textContent → 'text'`                  |
| `E.innerHTML`                | HTML 콘텐츠 반환 또는 설정                                           | `.innerHTML → '<b>text</b>'`             |

---
