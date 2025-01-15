# JavaScript 참조형 데이터 타입 (Reference Types)

JavaScript의 참조형 데이터 타입은 **객체**를 기반으로 하며, 변수는 객체 자체가 아닌 **메모리 주소(참조)** 를 저장합니다. 참조형 데이터는 **동적 크기**를 가지며, 변경 가능한(mutable) 특성을 가지고 있습니다.

---

## 📖 참조형 데이터 타입 종류

JavaScript에서 주요 참조형 데이터 타입은 다음과 같습니다:
1. **Array** (배열)
2. **Object** (객체)
3. **Function** (함수)

---

## 1. Array (배열)

### 설명
- 배열은 여러 값을 하나의 변수에 저장할 수 있는 데이터 구조입니다.
- 배열은 **인덱스(index)** 를 사용해 요소에 접근하며, 0부터 시작합니다.
- JavaScript 배열은 다양한 데이터 타입을 혼합하여 저장할 수 있습니다.

### 예제
```
let fruits = ["apple", "banana", "cherry"];
console.log(fruits); // "apple"
console.log(fruits.length); // 3
```

### 주요 메서드
- `push()`: 배열의 끝에 요소 추가.
- `pop()`: 배열의 마지막 요소 제거.
- `shift()`: 배열의 첫 번째 요소 제거.
- `unshift()`: 배열의 앞에 요소 추가.
- `map()`: 배열의 각 요소를 변환한 새로운 배열 반환.
- `filter()`: 조건을 만족하는 요소로 새로운 배열 생성.

#### 예제:
```
let numbers = [1, 2, 3, 4];
numbers.push(5); // [1, 2, 3, 4, 5]
numbers.pop(); // [1, 2, 3, 4]
let evenNumbers = numbers.filter(num => num % 2 === 0); // [2, 4]
```

---

## 2. Object (객체)

### 설명
- 객체는 **키(key)** 와 **값(value)** 의 쌍으로 이루어진 데이터 구조입니다.
- 키는 문자열 또는 심볼이어야 하며, 값은 어떤 데이터 타입도 가능합니다.

### 예제
```
let person = {
    name: "John",
    age: 30,
    city: "New York"
};
console.log(person.name); // "John"
console.log(person["age"]); // 30
```

### 주요 메서드 및 속성
- `Object.keys()`: 객체의 모든 키를 배열로 반환.
- `Object.values()`: 객체의 모든 값을 배열로 반환.
- `Object.assign()`: 객체 복사(얕은 복사).
- `Object.freeze()`: 객체 수정 불가로 설정.

#### 예제:
```
let car = { brand: "Toyota", model: "Corolla" };
let keys = Object.keys(car); // ["brand", "model"]
let values = Object.values(car); // ["Toyota", "Corolla"]
let newCar = Object.assign({}, car); // { brand: "Toyota", model: "Corolla" }
```

---

## 3. Function (함수)

### 설명
- 함수는 작업을 수행하거나 값을 반환하기 위한 코드 블록입니다.
- 함수는 JavaScript에서 특별한 객체로 간주되며, 다른 변수에 할당하거나 인자로 전달할 수 있습니다.

### 예제
```
function greet(name) {
    return `Hello, ${name}!`;
}
let sayHello = greet;
console.log(sayHello("Alice")); // "Hello, Alice!"
```

### 주요 특징
- **콜백 함수**: 다른 함수의 인자로 전달되는 함수.
- **익명 함수**: 이름이 없는 함수.
- **화살표 함수**: 간결한 문법으로 작성된 함수.

#### 콜백 함수 예제:
```
function processUserInput(callback) {
    let name = prompt("Enter your name:");
    callback(name);
}
processUserInput(name => console.log(`Hello, ${name}!`));
```

---

## 📂 참조형 데이터의 특징

1. **참조 저장**
   - 변수는 실제 데이터를 저장하지 않고 메모리 주소(참조)를 저장합니다.
   - 동일한 객체를 참조하는 변수는 모두 동일한 데이터를 공유합니다.

#### 예제:
```
let obj1 = { name: "Alice" };
let obj2 = obj1;
obj2.name = "Bob";
console.log(obj1.name); // "Bob" (obj1과 obj2가 동일한 객체를 참조)
```

2. **변경 가능(Mutable)**
   - 참조형 데이터는 변경이 가능하며, 변경 사항은 모든 참조 변수에 반영됩니다.

3. **얕은 복사 vs 깊은 복사**
   - 얕은 복사(Shallow Copy): 최상위 속성만 복사.
   - 깊은 복사(Deep Copy): 중첩된 객체까지 모두 복사.

#### 깊은 복사 예제:
```
let original = { name: "Alice", address: { city: "Wonderland" } };
let deepCopy = JSON.parse(JSON.stringify(original));
deepCopy.address.city = "Dreamland";
console.log(original.address.city); // "Wonderland" (원본 영향 없음)
```

---

## ✨ 요약

1. **Array**
   - 여러 값을 하나의 변수에 저장하며 다양한 메서드를 제공.
   - 예: `push()`, `pop()`, `map()` 등.

2. **Object**
   - 키와 값으로 구성된 데이터 구조로 유연성과 확장성이 높음.
   - 예: `{ key: value }` 형태로 사용.

3. **Function**
   - 작업을 수행하거나 값을 반환하는 코드 블록으로 고유한 유연성을 가짐.
   - 예: 콜백 함수, 화살표 함수 등.

---
