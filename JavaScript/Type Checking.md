# JavaScript 데이터 타입 확인 (Type Checking)

JavaScript에서 데이터 타입을 확인하는 것은 변수나 값의 유형을 파악해 올바른 작업을 수행하거나 오류를 방지하는 데 매우 중요합니다. 이를 위해 JavaScript는 여러 가지 방법을 제공합니다.

---

## 📖 데이터 타입 확인 방법

JavaScript에서 데이터 타입을 확인하는 주요 방법은 다음과 같습니다:

1. **`typeof` 연산자**: 원시형(Primitive) 및 일부 참조형 데이터 타입 확인.
2. **`instanceof` 연산자**: 객체가 특정 클래스의 인스턴스인지 확인.
3. **`Array.isArray()` 메서드**: 값이 배열인지 여부를 확인.
4. **`Object.prototype.toString.call()`**: 보다 구체적인 데이터 타입 확인.

---

## 1. `typeof` 연산자

### 설명
- `typeof`는 변수나 값의 데이터 타입을 문자열로 반환합니다.
- 원시형 데이터 타입(`string`, `number`, `boolean`, `undefined`, `symbol`, `bigint`)과 일부 참조형(`function`, `object`)에 대해 유용합니다.

### 구문
```
typeof operand
```

### 반환 값
| 데이터 타입       | 반환 값       |
|------------------|--------------|
| 문자열(String)    | `"string"`   |
| 숫자(Number)      | `"number"`   |
| 불리언(Boolean)   | `"boolean"`  |
| undefined         | `"undefined"`|
| 심볼(Symbol)      | `"symbol"`   |
| 빅인트(BigInt)    | `"bigint"`   |
| 객체(Object)      | `"object"`   |
| 함수(Function)    | `"function"` |

### 예제
```
console.log(typeof "Hello");       // "string"
console.log(typeof 42);            // "number"
console.log(typeof true);          // "boolean"
console.log(typeof undefined);     // "undefined"
console.log(typeof Symbol("id"));  // "symbol"
console.log(typeof 10n);           // "bigint"
console.log(typeof {});            // "object"
console.log(typeof function(){});  // "function"
```

#### 특수 사례
1. **`typeof null`**
   - `null`은 객체가 아님에도 불구하고 `"object"`를 반환합니다. 이는 JavaScript 초기 설계상의 버그입니다.
   ```
   console.log(typeof null); // "object"
   ```

2. **배열**
   - 배열은 객체로 반환됩니다.
   ```
   console.log(typeof [1, 2, 3]); // "object"
   ```

---

## 2. `instanceof` 연산자

### 설명
- 객체가 특정 클래스의 인스턴스인지 확인합니다.
- 프로토타입 체인을 따라 올라가며 해당 클래스와 연결되어 있는지 검사합니다.

### 구문
```
object instanceof constructor
```

### 반환 값
- `true`: 객체가 생성자의 인스턴스인 경우.
- `false`: 그렇지 않은 경우.

### 예제
```
let fruits = ["Apple", "Banana"];
console.log(fruits instanceof Array);  // true
console.log(fruits instanceof Object); // true

let date = new Date();
console.log(date instanceof Date);     // true
console.log(date instanceof Object);   // true

let str = new String("Hello");
console.log(str instanceof String);    // true
```

#### 주의점:
- 원시형 데이터는 `instanceof`로 검사할 수 없습니다.
```
let greeting = "Hello";
console.log(greeting instanceof String); // false (문자열 리터럴은 객체가 아님)
```

---

## 3. `Array.isArray()` 메서드

### 설명
- 값이 배열인지 여부를 확인합니다.
- 배열인지 정확히 판별할 때 사용하며, 다른 객체와 배열을 구분할 수 있습니다.

### 구문
```
Array.isArray(value)
```

### 반환 값
- `true`: 값이 배열인 경우.
- `false`: 그렇지 않은 경우.

### 예제
```
let numbers = [1, 2, 3];
let text = "Hello";

console.log(Array.isArray(numbers)); // true (배열)
console.log(Array.isArray(text));    // false (문자열)
```

#### 특수 사례:
```
console.log(Array.isArray([]));            // true (빈 배열)
console.log(Array.isArray(new Array(5))); // true (배열 생성자 사용)
console.log(Array.isArray({}));           // false (객체)
```

---

## 4. `Object.prototype.toString.call()`

### 설명
- 모든 데이터 타입에 대해 정확한 결과를 반환합니다.
- `[object Type]` 형식으로 결과를 반환하며, 배열, 날짜 등도 구분 가능합니다.

### 구문
```
Object.prototype.toString.call(value)
```

### 예제
```
console.log(Object.prototype.toString.call("Hello"));      // "[object String]"
console.log(Object.prototype.toString.call(42));           // "[object Number]"
console.log(Object.prototype.toString.call([1, 2, 3]));    // "[object Array]"
console.log(Object.prototype.toString.call(new Date()));   // "[object Date]"
console.log(Object.prototype.toString.call(null));         // "[object Null]"
console.log(Object.prototype.toString.call(undefined));    // "[object Undefined]"
```

---

## 🛠️ 비교: typeof vs instanceof vs Array.isArray()

| 방법                  | 주요 용도                                      | 제한 사항                                   |
|-----------------------|-----------------------------------------------|------------------------------------------|
| `typeof`             | 원시형 및 함수의 타입 확인                     | 배열과 null을 정확히 구분하지 못함         |
| `instanceof`         | 객체가 특정 클래스의 인스턴스인지 확인          | 원시형 데이터를 검사할 수 없음             |
| `Array.isArray()`    | 값이 배열인지 정확히 판별                       | 배열 외 다른 객체에는 적용 불가            |
| `Object.prototype.toString.call()` | 모든 데이터 타입에 대해 정확한 결과 반환 | 코드가 다소 길고 복잡함                    |

---

## ✨ 요약

1. **`typeof`**: 원시형 및 함수의 타입을 간단히 확인할 때 유용.
2. **`instanceof`**: 객체가 특정 클래스의 인스턴스인지 검사.
3. **`Array.isArray()`**: 값이 배열인지 판별하는 가장 정확한 방법.
4. **`Object.prototype.toString.call()`**: 모든 데이터 타입에 대해 정확한 결과를 제공.

---
