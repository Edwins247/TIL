# JavaScript 부정, 비교 연산자 정리

JavaScript에서 **부정 연산자**와 **비교 연산자**는 조건문과 논리적 판단을 수행할 때 필수적으로 사용됩니다. 이들은 값의 참/거짓 여부를 확인하거나, 두 값 간의 관계를 비교하는 데 사용됩니다. 아래는 각각의 개념과 예제를 포함한 정리입니다.

---

## 📖 부정 연산자 (Logical NOT Operator)

### 설명
- 부정 연산자는 **`!`** 기호를 사용하며, Boolean 값을 반대로 변환합니다.
- `true`는 `false`로, `false`는 `true`로 변환됩니다.
- 값이 Truthy인지 Falsy인지 확인할 때 유용합니다.

### 구문
```
!value
```

### 예제:
```
console.log(!true);        // false
console.log(!false);       // true
console.log(!0);           // true (Falsy 값)
console.log(!"hello");     // false (Truthy 값)
console.log(!null);        // true (Falsy 값)
```

#### **이중 부정 (`!!`)**
- 이중 부정을 사용하면 값을 명시적으로 Boolean 타입으로 변환할 수 있습니다.
```
console.log(!!"hello");    // true
console.log(!!0);          // false
```

---

## 📂 비교 연산자 (Comparison Operators)

### 설명
- 비교 연산자는 두 값을 비교하여 Boolean 값을 반환합니다.
- **동등성 비교**와 **크기 비교**로 나뉩니다.

---

### **1. 동등성 비교**

| 연산자   | 이름                         | 설명                                                                 |
|----------|------------------------------|----------------------------------------------------------------------|
| `==`     | 동등(Loose Equality)         | 값이 같으면 `true`, 타입은 무시.                                      |
| `===`    | 일치(Strict Equality)        | 값과 타입이 모두 같으면 `true`.                                       |
| `!=`     | 부등(Loose Inequality)       | 값이 다르면 `true`, 타입은 무시.                                      |
| `!==`    | 불일치(Strict Inequality)    | 값 또는 타입이 다르면 `true`.                                         |

#### 예제:
```
console.log(5 == "5");     // true (타입 강제 변환)
console.log(5 === "5");    // false (타입이 다름)
console.log(5 != "5");     // false (타입 강제 변환 후 같음)
console.log(5 !== "5");    // true (값은 같지만 타입이 다름)
```

---

### **2. 크기 비교**

| 연산자   | 이름         | 설명                                   |
|----------|--------------|----------------------------------------|
| `<`      | 미만         | 왼쪽 값이 오른쪽 값보다 작으면 `true`. |
| `<=`     | 이하         | 왼쪽 값이 오른쪽 값보다 작거나 같으면 `true`. |
| `>`      | 초과         | 왼쪽 값이 오른쪽 값보다 크면 `true`.   |
| `>=`     | 이상         | 왼쪽 값이 오른쪽 값보다 크거나 같으면 `true`. |

#### 예제:
```
console.log(10 < 20);      // true
console.log(10 <= 10);     // true
console.log(15 > 10);      // true
console.log(15 >= 20);     // false
```

---

## 🔄 암시적 형 변환과 비교

JavaScript에서는 비교 시 **암시적 형 변환(Type Coercion)**이 발생할 수 있습니다. 이를 방지하려면 항상 **엄격한 비교(`===`, `!==`)** 를 사용하는 것이 좋습니다.

#### 예제:
```
console.log("10" == 10);   // true (문자열 "10"이 숫자 10으로 변환됨)
console.log("10" === 10);  // false (타입이 다름)
```

---

## 🛠️ 활용 사례

### **1. 조건문에서의 활용**
부정 연산자와 비교 연산자는 조건문에서 자주 사용됩니다.
```
let age = 18;

if (age >= 18) {
    console.log("You are an adult.");
} else {
    console.log("You are a minor.");
}
```

---

### **2. Truthy/Falsy 확인**
부정 연산자를 사용해 값을 Boolean으로 변환하고 조건을 평가할 수 있습니다.
```
let username = "";

if (!username) {
    console.log("Username is required."); // 출력: Username is required.
}
```

---

### **3. 배열이나 객체의 빈 상태 확인**
배열이나 객체가 비어 있는지 확인할 때도 유용합니다.
```
let arr = [];

if (!arr.length) {
    console.log("Array is empty."); // 출력: Array is empty.
}

let obj = {};
if (!Object.keys(obj).length) {
    console.log("Object is empty."); // 출력: Object is empty.
}
```

---

## ✨ 요약

1. **부정 연산자 (`!`)**
   - Boolean 값을 반대로 변환하며, Truthy/Falsy를 평가하는 데 유용.
   - 이중 부정(`!!`)을 통해 값을 명시적으로 Boolean으로 변환 가능.

2. **비교 연산자**
   - 동등성 비교: 느슨한(`==`, `!=`) vs 엄격한(`===`, `!==`) 비교.
   - 크기 비교: `<`, `<=`, `>`, `>=`.

3. 항상 엄격한 비교(`===`, `!==`)를 사용하는 것이 예상치 못한 오류를 방지하는 데 도움이 됩니다.

---
