# JavaScript 선택적 체이닝 (Optional Chaining) 정리

**선택적 체이닝(Optional Chaining)** 은 JavaScript에서 **객체, 배열, 함수**의 중첩된 속성이나 메서드를 안전하게 접근할 수 있도록 도와주는 연산자입니다. ES2020(ECMAScript 2020)에서 도입된 이 기능은 코드의 가독성을 높이고, `null` 또는 `undefined`로 인해 발생할 수 있는 오류를 방지합니다.

---

## 📖 선택적 체이닝이란?

- 선택적 체이닝(`?.`)은 **중첩된 객체나 배열의 속성**을 접근할 때, 해당 경로에 값이 없으면 **`undefined`를 반환**합니다.
- 기존에는 중첩된 속성을 접근하기 전에 **명시적으로 null/undefined 체크**가 필요했지만, 선택적 체이닝을 사용하면 이를 간소화할 수 있습니다.

---

## 📂 선택적 체이닝의 문법

### **1. 기본 문법**
```
obj?.prop         // 객체의 정적 속성 접근
obj?.[expr]       // 객체의 동적 속성 접근
arr?.[index]      // 배열 요소 접근
func?.(...args)   // 함수 또는 메서드 호출
```

---

## 📂 선택적 체이닝의 주요 활용

### **1. 객체 속성 접근**

#### 기존 방식:
```
const user = { profile: { name: "Alice" } };

if (user && user.profile && user.profile.name) {
    console.log(user.profile.name); // "Alice"
}
```

#### 선택적 체이닝 사용:
```
const user = { profile: { name: "Alice" } };
console.log(user?.profile?.name); // "Alice"
```

- `user.profile`이나 `user.profile.name`이 `null` 또는 `undefined`인 경우, 에러 대신 `undefined`를 반환합니다.

---

### **2. 배열 요소 접근**

#### 예제:
```
const users = [{ name: "Alice" }, null, { name: "Bob" }];

console.log(users?.?.name); // "Alice"
console.log(users?.[1]?.name); // undefined (null인 요소)
console.log(users?.[2]?.name); // "Bob"
```

---

### **3. 함수 호출**

#### 기존 방식:
```
const obj = {
    greet: () => "Hello",
};

if (obj && typeof obj.greet === "function") {
    console.log(obj.greet()); // "Hello"
}
```

#### 선택적 체이닝 사용:
```
const obj = {
    greet: () => "Hello",
};

console.log(obj.greet?.()); // "Hello"
console.log(obj.nonExistentMethod?.()); // undefined (메서드가 없으므로)
```

---

### **4. 동적 속성 접근**

#### 예제:
```
const user = {
    settings: {
        theme: "dark",
    },
};

const key = "theme";
console.log(user.settings?.[key]); // "dark"

const invalidKey = "nonExistent";
console.log(user.settings?.[invalidKey]); // undefined
```

---

## 📂 선택적 체이닝과 단축 평가

### 단축 평가란?
- 선택적 체이닝은 **단축 평가(short-circuiting)** 를 수행합니다.
- 왼쪽 피연산자가 `null` 또는 `undefined`일 경우 평가를 멈추고 `undefined`를 반환합니다.

#### 예제:
```
const person = null;
console.log(person?.address?.city); // undefined (평가 중단)
```

---

## 📂 선택적 체이닝과 OR (`||`) 비교

| 연산자            | 동작                                                                 |
|-------------------|----------------------------------------------------------------------|
| 선택적 체이닝 (`?.`) | 왼쪽 값이 `null` 또는 `undefined`일 때만 평가 중단 후 `undefined` 반환. |
| OR (`||`)         | 모든 Falsy 값(`false`, `0`, `""`, `NaN`, `null`, `undefined`)에서 오른쪽 값 반환. |

#### 비교 예제:
```
const user = { name: "" };

console.log(user.name || "Guest");  // "Guest" (빈 문자열은 Falsy)
console.log(user.name ?? "Guest"); // "" (빈 문자열은 null/undefined가 아님)
```

---

## 🛠️ 실용적인 활용 사례

### **1. API 데이터 처리**
API 응답 데이터가 중첩된 구조를 가질 때 유용합니다.
```
const response = {
    data: {
        user: {
            name: "Alice",
        },
    },
};

console.log(response.data?.user?.name); // "Alice"
console.log(response.data?.user?.email); // undefined
```

---

### **2. 배열과 객체 병합**
배열이나 객체에서 특정 값이 존재하는지 확인하고 기본값을 설정할 때 사용됩니다.
```
const users = [{ name: "Alice" }, null, { name: "Bob" }];
const names = users.map(user => user?.name ?? "Unknown");

console.log(names); // ["Alice", "Unknown", "Bob"]
```

---

### **3. 함수 호출**
함수가 존재하지 않을 가능성이 있을 때 안전하게 호출할 수 있습니다.
```
const api = {
    fetchData: () => console.log("Data fetched"),
};

api.fetchData?.();      // 실행됨
api.nonExistentFunc?.(); // 아무 일도 일어나지 않음
```

---

## 📂 주의사항

1. **선택적 체이닝은 읽기 전용입니다.**
   - 값을 읽는 데만 사용할 수 있으며, 쓰기에는 사용할 수 없습니다.
   ```
   const obj = {};
   obj?.property = 42; // SyntaxError
   ```

2. **너무 남용하지 말 것**
   - 모든 상황에서 선택적 체이닝을 사용하는 것은 가독성을 떨어뜨릴 수 있습니다.

3. **구식 브라우저 지원**
   - ES2020 이전 브라우저에서는 지원되지 않으므로 폴리필(polyfill)이 필요할 수 있습니다.

---

## ✨ 요약

1. **선택적 체이닝(`?.`)** 은 중첩된 객체, 배열, 함수 등을 안전하게 접근하는 데 사용됩니다.
2. 왼쪽 피연산자가 `null` 또는 `undefined`일 경우 평가를 멈추고 `undefined`를 반환합니다.
3. API 데이터 처리, 동적 속성 접근, 함수 호출 등 다양한 상황에서 유용하게 활용됩니다.
4. 단축 평가와 기본값 설정(`??`)을 조합하면 더욱 강력한 코드 작성이 가능합니다.

---
