# JavaScript 원시형 데이터 타입 (Primitive Types)

JavaScript의 원시형 데이터 타입은 **객체가 아니며**, 메서드나 속성을 가지지 않는 데이터 타입입니다. 원시 값은 **불변(immutable)**하며, 직접적으로 언어의 가장 낮은 수준에서 구현됩니다. 이러한 원시형 데이터 타입은 JavaScript에서 가장 기본적인 데이터 구조를 형성합니다.

---

## 📖 원시형 데이터 타입 종류

JavaScript에는 다음과 같은 5가지 주요 원시형 데이터 타입이 있습니다:

1. **String** (문자열)
2. **Number** (숫자)
3. **Boolean** (참/거짓)
4. **Null** (값이 없음)
5. **Undefined** (정의되지 않음)

---

## 1. String (문자열)

### 설명
- 문자열 데이터를 나타냅니다.
- 작은따옴표(`'`)나 큰따옴표(`"`)로 감싸서 표현합니다.
- 템플릿 리터럴(``````)을 사용하면 문자열 내에서 변수를 쉽게 포함할 수 있습니다.

### 예제
```
let greeting = "Hello, World!";
let name = 'John Doe';
let message = `Welcome, ${name}!`; // 템플릿 리터럴 사용

console.log(greeting); // "Hello, World!"
console.log(message);  // "Welcome, John Doe!"
```

### 주요 메서드
- `length`: 문자열의 길이를 반환.
- `toUpperCase()`: 문자열을 대문자로 변환.
- `toLowerCase()`: 문자열을 소문자로 변환.
- `includes()`: 특정 문자열이 포함되어 있는지 확인.

#### 예제:
```
let str = "JavaScript";
console.log(str.length);          // 10
console.log(str.toUpperCase());   // "JAVASCRIPT"
console.log(str.includes("Java")); // true
```

---

## 2. Number (숫자)

### 설명
- 정수와 실수를 포함한 모든 숫자를 나타냅니다.
- 특별한 숫자 값: `Infinity`, `-Infinity`, `NaN` (Not-a-Number).

### 예제
```
let age = 25;            // 정수
let pi = 3.14159;        // 실수
let infinity = Infinity; // 무한대

console.log(age + pi);   // 28.14159
console.log(10 / 0);     // Infinity
console.log("abc" * 3);  // NaN (숫자가 아님)
```

### 주요 메서드 및 속성
- `toFixed()`: 고정 소수점 형식으로 숫자를 반환.
- `isNaN()`: 값이 NaN인지 확인.

#### 예제:
```
let num = 123.456;
console.log(num.toFixed(2));      // "123.46"
console.log(Number.isNaN("abc")); // false
```

---

## 3. Boolean (참/거짓)

### 설명
- 논리적 참(`true`) 또는 거짓(`false`) 값을 나타냅니다.
- 주로 조건문에서 사용됩니다.

### 예제
```
let isAdult = true;
let hasPermission = false;

if (isAdult && hasPermission) {
    console.log("Access granted.");
} else {
    console.log("Access denied.");
}
```

### Boolean 변환
- JavaScript에서는 다음 값을 **Falsy**로 간주합니다:
    - `false`, `0`, `""`(빈 문자열), `null`, `undefined`, `NaN`.
- 나머지 값은 모두 **Truthy**로 간주됩니다.

#### 예제:
```
console.log(Boolean(0));         // false
console.log(Boolean("hello"));   // true
console.log(Boolean(null));      // false
```

---

## 4. Null (값이 없음)

### 설명
- 의도적으로 "값이 없음"을 나타내기 위해 사용됩니다.
- JavaScript에서 `null`은 객체가 아님에도 불구하고, 역사적인 이유로 `typeof null`이 `"object"`를 반환합니다.

### 예제
```
let emptyValue = null;

console.log(emptyValue);         // null
console.log(typeof emptyValue);  // "object"
```

### 주의점:
- `null`은 명시적으로 비어 있는 값을 나타낼 때 사용됩니다.
- 반면, `undefined`는 값이 아직 할당되지 않았음을 나타냅니다.

---

## 5. Undefined (정의되지 않음)

### 설명
- 변수가 선언되었지만 값이 할당되지 않은 상태를 나타냅니다.
- 함수에서 반환값이 없을 경우에도 자동으로 `undefined`를 반환합니다.

### 예제
```
let notAssigned;
console.log(notAssigned);        // undefined

function noReturn() {}
console.log(noReturn());         // undefined
```

---

## 🔍 Null vs Undefined

| 구분           | Null                          | Undefined                     |
|----------------|-------------------------------|--------------------------------|
| 의미           | 명시적으로 비어 있는 값        | 값이 할당되지 않은 상태        |
| typeof 결과    | `"object"`                    | `"undefined"`                 |
| 동등 비교 (`==`)| true                          |                                |
| 일치 비교 (`===`)| false                         |                                |

#### 예제:
```
console.log(null == undefined);   // true (동등 비교)
console.log(null === undefined);  // false (일치 비교)
```

---

## ✨ 요약

1. **String**: 문자열 데이터를 표현하며, 다양한 메서드를 통해 조작 가능.
2. **Number**: 정수와 실수를 포함하며, 특별한 숫자 값(`Infinity`, `NaN`)도 포함.
3. **Boolean**: 논리적 참(`true`) 또는 거짓(`false`) 값을 표현.
4. **Null**: 명시적으로 비어 있는 값을 나타냄.
5. **Undefined**: 값이 할당되지 않은 상태를 나타냄.

---
