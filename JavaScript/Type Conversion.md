# JavaScript 형 변환 (Type Conversion)

JavaScript는 **동적 타입 언어**로, 변수의 데이터 타입이 자동으로 변환되거나 명시적으로 변환될 수 있습니다. 이러한 **형 변환(Type Conversion)** 은 크게 두 가지로 나뉩니다:

1. **암시적 형 변환 (Implicit Conversion)**: JavaScript가 자동으로 데이터 타입을 변환.
2. **명시적 형 변환 (Explicit Conversion)**: 개발자가 의도적으로 데이터 타입을 변환.

---

## 📖 암시적 형 변환 (Implicit Conversion)

JavaScript는 연산자나 표현식에 따라 자동으로 데이터 타입을 변환합니다. 이를 **타입 강제 변환(Type Coercion)** 이라고도 합니다.

### **1. 문자열로 변환**
- 숫자나 불리언 값이 문자열과 함께 사용되면, JavaScript는 이를 문자열로 변환합니다.

#### 예제:
```
console.log("5" + 2);   // "52" (숫자 2가 문자열로 변환)
console.log("Hello" + true); // "Hellotrue" (불리언이 문자열로 변환)
```

### **2. 숫자로 변환**
- 산술 연산(+, -, *, / 등)에서 문자열이 숫자로 변환됩니다.
- 빈 문자열(`""`), `null`, `false`는 숫자 `0`으로 변환됩니다.
- `true`는 숫자 `1`로 변환됩니다.

#### 예제:
```
console.log("5" - 2);   // 3 ("5"가 숫자로 변환)
console.log("10" * 2);  // 20 ("10"이 숫자로 변환)
console.log(true + 1);  // 2 (true가 1로 변환)
console.log(null + 1);  // 1 (null이 0으로 변환)
```

### **3. 불리언으로 변환**
- 조건문에서 사용되는 값은 자동으로 불리언 값으로 평가됩니다.
- 아래 값들은 **Falsy**로 간주됩니다:
    - `false`, `0`, `""`(빈 문자열), `null`, `undefined`, `NaN`.
- 나머지 값은 모두 **Truthy**로 간주됩니다.

#### 예제:
```
if ("") {
    console.log("Truthy");
} else {
    console.log("Falsy"); // 실행됨
}

console.log(Boolean(0));         // false
console.log(Boolean("Hello"));   // true
```

---

## 📖 명시적 형 변환 (Explicit Conversion)

개발자가 의도적으로 데이터 타입을 변경하는 방법입니다.

### **1. 문자열로 변환**

#### 방법:
- `String()` 함수를 사용.
- `.toString()` 메서드를 호출.

#### 예제:
```
let num = 123;
let bool = true;

console.log(String(num));      // "123"
console.log(bool.toString());  // "true"
```

---

### **2. 숫자로 변환**

#### 방법:
- `Number()` 함수를 사용.
- 단항 연산자(`+`)를 사용.

#### 예제:
```
let str = "456";
let bool = false;

console.log(Number(str));      // 456
console.log(+bool);            // 0
```

#### 주의:
- 숫자로 변환할 수 없는 값은 `NaN`을 반환합니다.
```
console.log(Number("abc"));    // NaN
```

---

### **3. 불리언으로 변환**

#### 방법:
- `Boolean()` 함수를 사용.

#### 예제:
```
let num = 0;
let str = "Hello";

console.log(Boolean(num));     // false
console.log(Boolean(str));     // true
```

---

## 🔍 특수 사례

### **1. Null과 Undefined**
- `null`과 `undefined`는 각각 고유한 동작을 가집니다.
    - `Number(null)` → `0`
    - `Number(undefined)` → `NaN`

#### 예제:
```
console.log(Number(null));       // 0
console.log(Number(undefined));  // NaN
```

---

### **2. 객체(Object)의 형 변환**
객체를 원시형 데이터로 변환하려고 하면 다음 단계를 거칩니다:
1. **ToPrimitive**: 객체를 원시 값으로 바꾸려 시도.
2. **valueOf()** → **toString()** 순서로 호출.

#### 예제:
```
let obj = {
    valueOf() {
        return 42;
    },
    toString() {
        return "Hello";
    }
};

console.log(String(obj));       // "Hello"
console.log(Number(obj));       // 42
```

---

## 🛠️ 형 변환 요약 표

| 원시 값        | 문자열(`String()`) | 숫자(`Number()`) | 불리언(`Boolean()`) |
|----------------|---------------------|------------------|---------------------|
| `"123"`        | `"123"`             | `123`            | `true`              |
| `"abc"`        | `"abc"`             | `NaN`            | `true`              |
| `true`         | `"true"`            | `1`              | `true`              |
| `false`        | `"false"`           | `0`              | `false`             |
| `null`         | `"null"`            | `0`              | `false`             |
| `undefined`    | `"undefined"`       | `NaN`            | `false`             |

---

## ✨ 요약

1. JavaScript는 암시적 형 변환을 통해 자동으로 데이터 타입을 변경합니다.
   - 문자열, 숫자, 불리언 간의 자동 전환이 자주 발생합니다.
2. 명시적 형 변환은 개발자가 의도적으로 데이터를 다른 타입으로 변경합니다.
   - 주요 함수: `String()`, `Number()`, `Boolean()`.
3. 특수 사례(`null`, `undefined`, 객체`)는 주의 깊게 다뤄야 합니다.

---
