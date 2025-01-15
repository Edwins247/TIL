# JavaScript 전개 연산자 (Spread Operator) 정리

JavaScript의 **전개 연산자(Spread Operator)** 는 ES6(ECMAScript 2015)에서 도입된 강력한 기능으로, **배열, 객체, 문자열 등 이터러블(iterable)** 의 요소를 개별적으로 분리하거나 확장하는 데 사용됩니다. 이를 통해 데이터를 효율적으로 병합, 복사하거나 함수에 동적으로 전달할 수 있습니다.

---

## 📖 전개 연산자란?

- 전개 연산자는 **세 개의 점(`...`)** 으로 표현됩니다.
- 배열, 객체, 문자열 등 이터러블(iterable)의 요소를 개별적으로 **펼치거나 확장**하는 데 사용됩니다.
- 주로 다음과 같은 작업에 유용합니다:
  1. 배열 병합 및 복사
  2. 객체 병합 및 복사
  3. 함수 호출 시 인자 전달

---

## 📂 전개 연산자의 주요 활용

### **1. 배열에서의 활용**

#### **배열 병합**
- 여러 배열을 하나로 결합할 때 사용됩니다.
```
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const mergedArray = [...arr1, ...arr2];
console.log(mergedArray); // [1, 2, 3, 4, 5, 6]
```

#### **배열 복사**
- 기존 배열을 변경하지 않고 새로운 배열을 생성합니다.
```
const originalArray = [10, 20, 30];
const copiedArray = [...originalArray];
console.log(copiedArray); // [10, 20, 30]
console.log(originalArray === copiedArray); // false (서로 다른 참조)
```

#### **배열 요소 추가**
- 배열의 특정 위치에 요소를 추가할 수 있습니다.
```
const numbers = [3, 4];
const extendedNumbers = [1, 2, ...numbers, 5];
console.log(extendedNumbers); // [1, 2, 3, 4, 5]
```

---

### **2. 객체에서의 활용**

#### **객체 병합**
- 여러 객체를 하나로 결합할 때 사용됩니다.
```
const obj1 = { a: 1, b: 2 };
const obj2 = { c: 3 };
const mergedObject = { ...obj1, ...obj2 };
console.log(mergedObject); // { a: 1, b: 2, c: 3 }
```

#### **객체 복사**
- 기존 객체를 변경하지 않고 새로운 객체를 생성합니다.
```
const originalObject = { x: 10, y: 20 };
const copiedObject = { ...originalObject };
console.log(copiedObject); // { x: 10, y: 20 }
console.log(originalObject === copiedObject); // false (서로 다른 참조)
```

#### **속성 덮어쓰기**
- 병합 시 동일한 키가 존재하면 마지막에 추가된 값으로 덮어씁니다.
```
const obj1 = { a: 1, b: 2 };
const obj2 = { b: 3, c: 4 };
const updatedObject = { ...obj1, ...obj2 };
console.log(updatedObject); // { a: 1, b: 3, c: 4 }
```

---

### **3. 함수 호출에서의 활용**

#### **인자 전달**
- 배열의 요소를 개별적인 함수 인자로 전달할 수 있습니다.
```
function sum(a, b, c) {
    return a + b + c;
}

const numbers = [1, 2, 3];
console.log(sum(...numbers)); // Output: 6
```

#### **동적 인자 전달**
- 동적으로 생성된 배열이나 값들을 함수에 전달할 때 유용합니다.
```
function greet(greeting, ...names) {
    console.log(`${greeting}, ${names.join(", ")}!`);
}

greet("Hello", ..."John,Doe".split(",")); // "Hello, John, Doe!"
```

---

### **4. 문자열에서의 활용**

#### **문자열을 개별 문자로 분리**
- 문자열을 배열로 변환하거나 각 문자를 개별적으로 처리할 수 있습니다.
```
const str = "Hello";
const chars = [...str];
console.log(chars); // ['H', 'e', 'l', 'l', 'o']
```

---

## 🛠️ 전개 연산자의 특징과 주의점

### **1. 얕은 복사 (Shallow Copy)**
- 전개 연산자는 얕은 복사를 수행합니다. 중첩된 객체나 배열은 참조만 복사됩니다.
```
const nestedArray = [[1], [2]];
const copiedArray = [...nestedArray];

copiedArray = "changed";
console.log(nestedArray); // "changed" (원본도 변경됨)
```

### **2. 이터러블(iterable)만 사용 가능**
- 전개 연산자는 배열이나 문자열처럼 이터러블한 데이터 타입에만 사용할 수 있습니다.
```
const obj = { key: "value" };
// console.log([...obj]); // TypeError: obj is not iterable
```

---

## 🔄 전개 연산자 vs Rest 파라미터

| 구분                   | 전개 연산자 (`...`)                                  | Rest 파라미터 (`...`)                              |
|------------------------|----------------------------------------------------|--------------------------------------------------|
| 목적                   | 이터러블을 펼쳐서 개별 요소로 확장                   | 나머지 인자를 묶어서 배열로 만듦                   |
| 위치                   | 함수 호출/배열/객체 리터럴 등에서 사용               | 함수 정의 시 매개변수 자리에서 사용                |
| 예제                   | `[...array]`, `{...object}`, `func(...args)`        | `function(...args)`                              |

#### 비교 예제:
**전개 연산자**
```
let arr1 = [1, 2];
let arr2 = [...arr1]; // 배열 펼침
console.log(arr2);    // [1, 2]
```

**Rest 파라미터**
```
function sum(...args) {
    return args.reduce((accumulator, current) => accumulator + current);
}

console.log(sum(1, 2, 3)); // Output: 6
```

---

## ✨ 요약

1. **전개 연산자(`...`)** 는 이터러블(배열/문자열/객체)의 요소를 개별적으로 펼치거나 확장하는 데 사용됩니다.
   - 배열 병합 및 복사
   - 객체 병합 및 복사
   - 함수 호출 시 동적 인자 전달
   - 문자열 분리

2. 전개 연산자는 코드 가독성과 효율성을 높이는 데 유용하지만 얕은 복사를 수행하므로 중첩된 데이터 구조에서는 주의가 필요합니다.

---
