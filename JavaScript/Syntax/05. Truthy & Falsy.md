# JavaScript의 Truthy와 Falsy

JavaScript에서 값은 **Boolean 문맥**에서 평가될 때 **참(Truthy)** 또는 **거짓(Falsy)** 으로 간주됩니다. 이러한 개념은 조건문, 논리 연산자 등에서 자주 사용되며, 값이 실제로 `true`나 `false`가 아니더라도 해당 문맥에서 Boolean 값으로 변환됩니다.

---

## 📖 Truthy와 Falsy란?

### Truthy
- Boolean 문맥에서 `true`로 평가되는 값.
- 대부분의 값은 **Truthy**입니다.

### Falsy
- Boolean 문맥에서 `false`로 평가되는 값.
- JavaScript에서 Falsy 값은 다음 6가지입니다:
    1. `false`
    2. `0` (숫자 0)
    3. `-0` (음수 0)
    4. `""`, `''`, `` (빈 문자열)
    5. `null`
    6. `undefined`
    7. `NaN`

---

## 📂 Truthy와 Falsy의 예제

### **Falsy 값**
다음 값들은 모두 Boolean 문맥에서 `false`로 평가됩니다:
```
if (false) console.log("Falsy");
if (0) console.log("Falsy");
if (-0) console.log("Falsy");
if ("") console.log("Falsy");
if (null) console.log("Falsy");
if (undefined) console.log("Falsy");
if (NaN) console.log("Falsy");
```
출력 없음(모두 Falsy).

---

### **Truthy 값**
Falsy가 아닌 모든 값은 Truthy로 간주됩니다:
```
if (true) console.log("Truthy");
if (42) console.log("Truthy"); // 숫자
if ("hello") console.log("Truthy"); // 문자열
if (" ") console.log("Truthy"); // 공백 문자열도 Truthy
if ([1, 2, 3]) console.log("Truthy"); // 배열
if ({}) console.log("Truthy"); // 객체
if (function() {}) console.log("Truthy"); // 함수
```
출력:
```
Truthy
Truthy
Truthy
Truthy
Truthy
Truthy
Truthy
```

---

## 🛠️ Truthy와 Falsy의 활용

### **1. 조건문**
조건문에서 값을 평가할 때 자동으로 Boolean으로 변환됩니다.
```
let value = "hello";
if (value) {
    console.log("This is truthy!");
} else {
    console.log("This is falsy!");
}
// 출력: "This is truthy!"
```

---

### **2. 논리 연산자**
#### **AND (`&&`) 연산자**
- 첫 번째 Falsy 값을 반환하거나, 모든 피연산자가 Truthy면 마지막 값을 반환.
```
console.log(true && "JavaScript"); // "JavaScript"
console.log(false && "Hello");     // false
console.log(0 && "World");         // 0
```

#### **OR (`||`) 연산자**
- 첫 번째 Truthy 값을 반환하거나, 모든 피연산자가 Falsy면 마지막 값을 반환.
```
console.log(false || "JavaScript"); // "JavaScript"
console.log(0 || "Hello");          // "Hello"
console.log("" || NaN);             // NaN
```

---

### **3. 기본값 설정**
Falsy 값을 처리할 때 기본값을 설정하기 위해 OR 연산자를 사용할 수 있습니다.
```
let name = "";
let defaultName = name || "Guest";
console.log(defaultName); // "Guest"
```

---

### **4. 필터링**
`Boolean`을 활용해 배열에서 Falsy 값을 제거할 수 있습니다.
```
let mixedArray = [0, "hello", false, "", null, undefined, NaN, 42];
let truthyArray = mixedArray.filter(Boolean);
console.log(truthyArray); // ["hello", 42]
```

---

## 🔍 주의해야 할 점

1. **빈 배열(`[]`)과 빈 객체(`{}`)** 는 Truthy입니다.
   ```
   if ([]) console.log("Truthy!"); // 출력: "Truthy!"
   if ({}) console.log("Truthy!"); // 출력: "Truthy!"
   ```

2. **문자열 `"0"`과 `"false"`는 Truthy입니다.**
   ```
   if ("0") console.log("Truthy!");       // 출력: "Truthy!"
   if ("false") console.log("Truthy!");   // 출력: "Truthy!"
   ```

3. **`document.all`은 특수한 경우로 Falsy입니다.**
   - 이는 오래된 브라우저 호환성을 위해 존재하며, 일반적으로 사용하지 않는 것이 좋습니다.

---

## ✨ 요약

1. **Falsy 값**: JavaScript에서 Boolean 문맥에서 `false`로 평가되는 값은 다음과 같습니다:
    - `false`, `0`, `-0`, `""`, `null`, `undefined`, `NaN`.

2. **Truthy 값**: 위의 Falsy 값을 제외한 모든 값.

3. Truthy와 Falsy는 조건문, 논리 연산자, 기본값 설정 등 다양한 상황에서 활용됩니다.

---
