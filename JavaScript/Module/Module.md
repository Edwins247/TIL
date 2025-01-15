# JavaScript Modules: 내보내기와 가져오기 정리

JavaScript의 **모듈(Module)** 은 코드를 재사용 가능하고 유지보수하기 쉽게 만드는 구조입니다. 모듈을 사용하면 코드를 여러 파일로 나누고, 필요한 부분만 가져와 사용할 수 있습니다. 이 문서에서는 **모듈 내보내기 및 가져오기**, **기본 내보내기 및 가져오기**, **이름 내보내기 및 가져오기**, **동적 모듈 가져오기**, **가져온 모듈 바로 내보내기**에 대해 개념과 예제를 정리합니다.

---

## 📖 모듈이란?

- JavaScript 모듈은 코드를 **재사용 가능**하고 **독립적**으로 관리할 수 있도록 분리한 파일입니다.
- 각 모듈은 자체적인 스코프를 가지며, 전역 스코프를 오염시키지 않습니다.
- 모듈은 `import`와 `export` 키워드를 사용해 데이터를 주고받습니다.

---

## 📂 1. 모듈 내보내기 (Export)

### **1.1 기본 내보내기 (Default Export)**

#### 개념:
- 한 파일에서 **단 하나의 기본 값**만 내보낼 수 있습니다.
- 기본 내보내기는 이름 없이 내보낼 수 있으며, 가져올 때 원하는 이름으로 사용할 수 있습니다.

#### 예제:
**`math.js`**
```
export default function add(a, b) {
    return a + b;
}
```

**`main.js`**
```
import addFunction from './math.js';
console.log(addFunction(2, 3)); // 5
```

---

### **1.2 이름 내보내기 (Named Export)**

#### 개념:
- 여러 값을 이름으로 지정하여 내보낼 수 있습니다.
- 가져올 때 반드시 동일한 이름(또는 `as` 키워드로 별칭)을 사용해야 합니다.

#### 예제:
**`math.js`**
```
export const PI = 3.14;
export function multiply(a, b) {
    return a * b;
}
```

**`main.js`**
```
import { PI, multiply } from './math.js';
console.log(PI); // 3.14
console.log(multiply(2, 3)); // 6
```

#### 별칭 사용:
```
import { multiply as mul } from './math.js';
console.log(mul(2, 3)); // 6
```

---

### **1.3 모두 내보내기**

#### 개념:
- 여러 값을 한 번에 내보낼 수 있습니다.

#### 예제:
**`math.js`**
```
const add = (a, b) => a + b;
const subtract = (a, b) => a - b;

export { add, subtract };
```

**`main.js`**
```
import { add, subtract } from './math.js';
console.log(add(5, 3)); // 8
console.log(subtract(5, 3)); // 2
```

---

## 📂 2. 모듈 가져오기 (Import)

### **2.1 기본 가져오기 (Default Import)**

#### 개념:
- 기본 내보내기는 중괄호 없이 임의의 이름으로 가져올 수 있습니다.

#### 예제:
```
import myFunction from './module.js';
myFunction();
```

---

### **2.2 이름 가져오기 (Named Import)**

#### 개념:
- 이름 내보내기는 중괄호를 사용해 동일한 이름으로 가져옵니다.

#### 예제:
```
import { namedExport } from './module.js';
namedExport();
```

---

### **2.3 모든 내용 가져오기**

#### 개념:
- `* as`를 사용해 모듈의 모든 내용을 객체로 가져옵니다.

#### 예제:
**`math.js`**
```
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;
```

**`main.js`**
```
import * as math from './math.js';
console.log(math.add(2, 3)); // 5
console.log(math.subtract(5, 3)); // 2
```

---

## 📂 3. 동적으로 모듈 가져오기 (Dynamic Import)

### **개념**
- `import()` 표현식을 사용해 모듈을 동적으로 로드합니다.
- 비동기로 동작하며 `Promise`를 반환합니다.

### **예제**

#### 기본 동적 가져오기:
```
const modulePath = './math.js';

import(modulePath)
    .then(module => {
        console.log(module.add(2, 3)); // 5
    })
    .catch(err => console.error(err));
```

#### `async/await` 사용:
```
async function loadModule() {
    const math = await import('./math.js');
    console.log(math.add(4, 5)); // 9
}
loadModule();
```

---

## 📂 4. 가져온 모듈 바로 내보내기 (Re-exporting)

### **개념**
- 다른 모듈에서 가져온 내용을 다시 내보낼 수 있습니다.
- 이를 통해 여러 모듈을 하나의 진입점(entry point)에서 관리할 수 있습니다.

### **예제**

#### 다시 내보내기:
**`moduleA.js`**
```
export const greet = () => console.log('Hello');
```

**`moduleB.js`**
```
export { greet } from './moduleA.js';
```

**`main.js`**
```
import { greet } from './moduleB.js';
greet(); // Hello
```

---

## 📂 JSON 데이터 가져오기

### **개념**
- JSON 파일을 모듈처럼 가져올 수 있습니다.

### **예제: JSON 데이터 로드**
**`data.json`**
```
{
    "name": "Alice",
    "age": 25
}
```

**`main.js`**
```
import data from './data.json' assert { type: 'json' };
console.log(data.name); // Alice
console.log(data.age); // 25
```

---

## ✨ 요약

| 유형                       | 설명                                                                                             | 예제                                                                                     |
|----------------------------|--------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------|
| 기본 내보내기               | 한 파일에서 하나의 값만 내보냄                                                                   | `export default function() {}`                                                          |
| 이름 내보내기               | 여러 값을 이름으로 지정하여 내보냄                                                               | `export const name = 'John'; export function greet() {}`                                 |
| 기본 가져오기               | 기본 값을 중괄호 없이 임의의 이름으로 가져옴                                                     | `import myFunc from './module.js'; myFunc();`                                            |
| 이름 가져오기               | 지정된 이름으로 값을 중괄호 안에 넣어 가져옴                                                     | `import { name } from './module.js'; console.log(name);`                                 |
| 동적 모듈 가져오기          | 비동기로 모듈을 로드하며 필요할 때만 실행                                                        | `const module = await import('./module.js'); module.func();`                             |
| 다시 내보내기               | 다른 모듈에서 가져온 내용을 다시 내보냄                                                          | `export { func } from './moduleA.js'; export * as utils from './utils/index.js';`         |

---
