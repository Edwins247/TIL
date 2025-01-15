# JavaScript 함수 매개변수 패턴 정리

JavaScript에서 **함수의 매개변수**는 함수 호출 시 값을 전달받아 작업을 수행하는 중요한 역할을 합니다. 다양한 매개변수 패턴을 활용하면 함수의 유연성과 가독성을 높일 수 있습니다. 이 문서에서는 기본 매개변수, 나머지 매개변수(Rest Parameters), 구조 분해 할당(Destructuring Assignment) 등을 다룹니다.

---

## 📖 1. 기본 매개변수 (Default Parameters)

### **1. 개념**
- 기본 매개변수는 함수 호출 시 인자가 전달되지 않거나 `undefined`일 경우, **기본값**을 설정할 수 있는 방식입니다.
- ES6에서 도입되었습니다.

### **2. 구문**
```
function functionName(param = defaultValue) {
    // 실행할 코드
}
```

### **3. 예제**

#### 기본값 설정:
```
function greet(name = "Guest") {
    console.log(`Hello, ${name}!`);
}

greet("Alice"); // "Hello, Alice!"
greet();        // "Hello, Guest!" (기본값 사용)
```

#### 여러 매개변수에 기본값 설정:
```
function calculatePrice(price, tax = 0.1, discount = 0) {
    return price + price * tax - discount;
}

console.log(calculatePrice(100));          // 110 (기본값 사용)
console.log(calculatePrice(100, 0.2, 10)); // 110
```

---

## 📂 2. 나머지 매개변수 (Rest Parameters)

### **1. 개념**
- 나머지 매개변수는 함수가 **가변 인자(variable-length arguments)**를 처리할 수 있도록 도와줍니다.
- `...` 문법을 사용하며, 나머지 매개변수를 배열로 수집합니다.

### **2. 구문**
```
function functionName(param1, ...restParams) {
    // restParams는 배열로 수집됨
}
```

### **3. 예제**

#### 가변 인자 처리:
```
function sum(...numbers) {
    return numbers.reduce((total, num) => total + num, 0);
}

console.log(sum(1, 2, 3));       // 6
console.log(sum(10, 20, 30, 40)); // 100
```

#### 첫 번째 인자와 나머지 인자 분리:
```
function introduce(firstName, ...hobbies) {
    console.log(`Hi, I'm ${firstName}. My hobbies are: ${hobbies.join(", ")}`);
}

introduce("Alice", "reading", "traveling", "coding");
// 출력: Hi, I'm Alice. My hobbies are: reading, traveling, coding
```

---

## 📂 3. 구조 분해 할당 (Destructuring Assignment)

### **1. 개념**
- 구조 분해 할당은 객체나 배열의 값을 함수 매개변수로 전달받을 때 특정 속성이나 요소를 쉽게 추출할 수 있는 문법입니다.
- ES6에서 도입되었습니다.

---

### **2. 객체 구조 분해**

#### 기본 사용:
```
function displayUser({ name, age }) {
    console.log(`Name: ${name}, Age: ${age}`);
}

const user = { name: "Alice", age: 25 };
displayUser(user);
// 출력: Name: Alice, Age: 25
```

#### 기본값 설정:
```
function displayUser({ name = "Guest", age = 18 }) {
    console.log(`Name: ${name}, Age: ${age}`);
}

displayUser({});                // Name: Guest, Age: 18
displayUser({ name: "Bob" });   // Name: Bob, Age: 18
```

---

### **3. 배열 구조 분해**

#### 기본 사용:
```
function sum([a, b]) {
    return a + b;
}

console.log(sum([10, 20])); // 30
```

#### 나머지 요소 추출:
```
function printElements([first, second, ...rest]) {
    console.log(`First: ${first}, Second: ${second}, Rest: ${rest}`);
}

printElements([1, 2, 3, 4]);
// 출력:
// First: 1
// Second: 2
// Rest: [3,4]
```

---

## 📂 혼합 패턴 활용

### 객체와 배열 혼합:
- 구조 분해와 나머지 매개변수를 함께 사용할 수 있습니다.
```
function processOrder({ id, items }, ...actions) {
    console.log(`Order ID: ${id}`);
    console.log(`Items: ${items.join(", ")}`);
    console.log(`Actions to perform: ${actions.join(", ")}`);
}

const order = { id: "12345", items: ["item1", "item2"] };
processOrder(order, "validate", "ship", "deliver");
// 출력:
// Order ID: 12345
// Items: item1, item2
// Actions to perform: validate, ship, deliver
```

---

## 📂 주의사항

1. **나머지 매개변수는 마지막에 위치해야 함**:
   ```
   function example(a, ...restParams) {} // 올바른 구문
   function example(...restParams, a) {} // 오류 발생
   ```

2. **구조 분해와 기본값 충돌 방지**:
   - 기본값과 구조 분해를 함께 사용할 때는 신중히 작성해야 합니다.
   ```
   function greet({ name = "Guest" } = {}) {
       console.log(`Hello, ${name}!`);
   }

   greet();             // Hello, Guest!
   greet({ name: "Bob" }); // Hello, Bob!
   ```

---

## ✨ 요약

1. **기본 매개변수**:
   - 함수 호출 시 누락된 인자에 대해 기본값을 설정.

2. **나머지 매개변수**:
   - 가변 길이의 인자를 배열로 처리.

3. **구조 분해 할당**:
   - 객체나 배열에서 필요한 값만 추출하여 함수 매개변수로 전달.

4. 혼합 패턴을 활용하면 복잡한 데이터 구조를 간단하고 효율적으로 처리할 수 있습니다.

---
