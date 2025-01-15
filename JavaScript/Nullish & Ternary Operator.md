# JavaScript Nullish 병합 연산자와 삼항 연산자 정리

JavaScript에서 **Nullish 병합 연산자(`??`)** 와 **삼항 연산자(`? :`)** 는 조건에 따라 값을 처리하거나 기본값을 설정하는 데 유용한 도구입니다. 두 연산자는 코드의 가독성과 효율성을 높이는 데 도움을 줍니다. 아래는 각각의 개념, 사용법, 예제를 포함한 정리입니다.

---

## 🌐 Nullish 병합 연산자 (`??`)

### **1. 개념**
- **Nullish 병합 연산자**는 **`null` 또는 `undefined`**인 경우에만 오른쪽 값을 반환합니다.
- 다른 **Falsy 값**(`false`, `0`, `""`, `NaN`)은 그대로 반환됩니다.
- ECMAScript 2020(ES11)에서 도입되었습니다.

### **2. 구문**
```
value1 ?? value2
```
- `value1`: 평가할 첫 번째 값.
- `value2`: `value1`이 `null` 또는 `undefined`일 때 반환할 기본값.

### **3. 예제**

#### 기본 사용:
```
let userName = null;
let defaultName = "Guest";

let displayName = userName ?? defaultName;
console.log(displayName); // "Guest" (userName이 null이므로 defaultName 반환)
```

#### Falsy 값 처리:
```
let count = 0;
let result = count ?? 42;
console.log(result); // 0 (count가 null이나 undefined가 아니므로 그대로 반환)
```

#### 객체 속성 기본값 설정:
```
let user = {
  name: null,
  age: 25
};

let userName = user.name ?? "Anonymous";
console.log(userName); // "Anonymous" (name이 null이므로 기본값 반환)

let userAge = user.age ?? 18;
console.log(userAge); // 25 (age가 정의되어 있으므로 그대로 반환)
```

---

## 🔄 Nullish 병합 연산자 vs OR (`||`)

| 연산자 | 동작                                                                                 |
|--------|--------------------------------------------------------------------------------------|
| `??`   | `null` 또는 `undefined`일 때만 오른쪽 값을 반환.                                      |
| `||`   | 모든 Falsy 값(`false`, `0`, `""`, `NaN`, `null`, `undefined`)일 때 오른쪽 값을 반환. |

#### 비교 예제:
```
let value1 = "";
let result1 = value1 || "Default";
console.log(result1); // "Default" (빈 문자열은 Falsy)

let result2 = value1 ?? "Default";
console.log(result2); // "" (빈 문자열은 null이나 undefined가 아니므로 그대로 반환)
```

---

## ❓ 삼항 연산자 (`? :`)

### **1. 개념**
- **삼항 연산자**는 조건에 따라 값을 선택하는 간단한 방법을 제공합니다.
- 조건문(`if...else`)의 축약형으로 사용됩니다.

### **2. 구문**
```
condition ? expressionIfTrue : expressionIfFalse
```
- `condition`: 평가할 조건.
- `expressionIfTrue`: 조건이 참일 때 실행되는 표현식.
- `expressionIfFalse`: 조건이 거짓일 때 실행되는 표현식.

### **3. 예제**

#### 기본 사용:
```
let age = 20;
let canVote = (age >= 18) ? "Yes" : "No";
console.log(canVote); // "Yes"
```

#### 숫자의 홀짝 판별:
```
let number = 7;
let isEven = (number % 2 === 0) ? "Even" : "Odd";
console.log(isEven); // "Odd"
```

---

## 🛠️ 삼항 연산자의 활용

### **1. 변수 초기화**
조건에 따라 변수에 값을 할당합니다.
```
let isLoggedIn = true;
let message = isLoggedIn ? "Welcome back!" : "Please log in.";
console.log(message); // "Welcome back!"
```

---

### **2. 함수에서 값 반환**
삼항 연산자를 사용해 간단한 조건을 처리합니다.
```
function getDiscount(price) {
    return price > 100 ? "10% Discount" : "No Discount";
}

console.log(getDiscount(150)); // "10% Discount"
console.log(getDiscount(80));  // "No Discount"
```

---

### **3. 중첩된 삼항 연산자**
중첩된 삼항 연산자를 사용해 복잡한 조건을 처리할 수 있습니다.
> *주의*: 중첩된 삼항 연산자는 가독성을 떨어뜨릴 수 있으므로 신중히 사용하세요.
```
let score = 85;

let grade = (score >= 90) ? "A" :
            (score >= 80) ? "B" :
            (score >= 70) ? "C" :
            (score >= 60) ? "D" : "F";

console.log(grade); // "B"
```

---

## Nullish 병합과 삼항 연산자의 차이점

| 특징                     | Nullish 병합 연산자 (`??`)                       | 삼항 연산자 (`? :`)                          |
|--------------------------|-------------------------------------------------|----------------------------------------------|
| 주요 목적                | 기본값 제공                                    | 조건에 따라 다른 값을 선택                   |
| 작동 방식                | 왼쪽 값이 `null` 또는 `undefined`인지 확인      | 주어진 조건을 평가하여 참/거짓에 따라 값 선택 |
| 단순 조건 처리 가능 여부 | 불가능                                         | 가능                                         |

---

## ✨ 요약

1. **Nullish 병합 연산자 (`??`)**
   - 왼쪽 값이 `null` 또는 `undefined`일 경우 오른쪽 값을 반환.
   - 다른 Falsy 값(`false`, `0`, `""`)은 그대로 유지.

2. **삼항 연산자 (`? :`)**
   - 조건문을 간단히 표현하며, 참/거짓에 따라 다른 값을 반환.
   - 중첩 사용 시 가독성에 주의해야 함.

---
