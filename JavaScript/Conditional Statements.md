# JavaScript 조건문: If와 Switch

JavaScript에서 **조건문**은 특정 조건에 따라 코드 블록을 실행하거나 분기 처리를 할 때 사용됩니다. 가장 일반적으로 사용되는 조건문은 **`if`**와 **`switch`**입니다. 두 조건문은 상황에 따라 적합하게 선택하여 사용할 수 있습니다.

---

## 📖 If 조건문

### **1. 개념**
- `if` 조건문은 주어진 **조건이 참(`true`)** 일 때, 특정 코드 블록을 실행합니다.
- 필요에 따라 **`else if`**와 **`else`**를 추가하여 여러 조건을 처리할 수 있습니다.

---

### **2. 구문**
```
if (condition) {
    // 조건이 true일 때 실행되는 코드
} else if (anotherCondition) {
    // 첫 번째 조건이 false이고, 두 번째 조건이 true일 때 실행되는 코드
} else {
    // 모든 조건이 false일 때 실행되는 코드
}
```

---

### **3. 예제**

#### 기본 사용:
```
let age = 18;

if (age >= 18) {
    console.log("You are an adult.");
} else {
    console.log("You are a minor.");
}
// 출력: "You are an adult."
```

#### 다중 조건 처리:
```
let score = 85;

if (score >= 90) {
    console.log("Grade: A");
} else if (score >= 80) {
    console.log("Grade: B");
} else if (score >= 70) {
    console.log("Grade: C");
} else {
    console.log("Grade: F");
}
// 출력: "Grade: B"
```

#### 중첩된 If:
```
let isLoggedIn = true;
let isAdmin = false;

if (isLoggedIn) {
    if (isAdmin) {
        console.log("Welcome, Admin!");
    } else {
        console.log("Welcome, User!");
    }
} else {
    console.log("Please log in.");
}
// 출력: "Welcome, User!"
```

---

### **4. 삼항 연산자와 비교**
- 간단한 조건문은 삼항 연산자(`? :`)로 대체할 수 있습니다.
```
let age = 20;
let message = (age >= 18) ? "Adult" : "Minor";
console.log(message); // "Adult"
```

---

## 📖 Switch 조건문

### **1. 개념**
- `switch` 조건문은 하나의 표현식을 평가하고, 그 결과 값에 따라 여러 **case** 중 하나를 실행합니다.
- `switch`는 다중 분기 처리를 간결하게 표현할 수 있으며, 주로 값 비교가 필요한 경우에 사용됩니다.

---

### **2. 구문**
```
switch (expression) {
    case value1:
        // expression이 value1과 같을 때 실행되는 코드
        break;
    case value2:
        // expression이 value2와 같을 때 실행되는 코드
        break;
    default:
        // 모든 case가 일치하지 않을 때 실행되는 코드
}
```

---

### **3. 예제**

#### 기본 사용:
```
let day = 3;

switch (day) {
    case 1:
        console.log("Monday");
        break;
    case 2:
        console.log("Tuesday");
        break;
    case 3:
        console.log("Wednesday");
        break;
    default:
        console.log("Invalid day");
}
// 출력: "Wednesday"
```

#### Default 처리:
- `default`는 모든 `case`가 일치하지 않을 경우 실행됩니다.
```
let color = "green";

switch (color) {
    case "red":
        console.log("Stop");
        break;
    case "yellow":
        console.log("Caution");
        break;
    case "green":
        console.log("Go");
        break;
    default:
        console.log("Invalid color");
}
// 출력: "Go"
```

#### 여러 값 처리:
- 동일한 처리를 여러 값에 대해 수행할 수 있습니다.
```
let fruit = "apple";

switch (fruit) {
    case "apple":
    case "pear":
        console.log("This is a pome fruit.");
        break;
    case "orange":
    case "lemon":
        console.log("This is a citrus fruit.");
        break;
    default:
        console.log("Unknown fruit.");
}
// 출력: "This is a pome fruit."
```

---

## 🛠️ If vs Switch

| 특징               | If 조건문                                  | Switch 조건문                              |
|--------------------|-------------------------------------------|-------------------------------------------|
| 주요 용도          | 복잡한 논리와 범위 기반의 조건 처리         | 특정 값과의 일치 여부를 처리               |
| 가독성             | 다중 조건이 많아지면 가독성이 떨어질 수 있음 | 값 기반 비교 시 가독성이 좋음              |
| 성능               | 논리적 비교가 많으면 성능 저하 가능          | 단순한 값 비교에서는 더 효율적일 수 있음   |
| 표현식 제한 여부   | 범위, 논리 연산 등 복잡한 표현식 가능         | 단순한 값 비교만 가능                      |

---

## ✨ 요약

1. **If 조건문**
   - 특정 조건에 따라 코드를 실행하며, 복잡한 논리와 범위 기반의 처리가 가능.
   - `else if`, `else`를 사용하여 다중 분기 처리 가능.

2. **Switch 조건문**
   - 하나의 표현식을 평가하고, 그 결과 값에 따라 여러 분기를 처리.
   - 단순한 값 비교에서 가독성과 효율성이 뛰어남.

3. 적합한 상황에서 If와 Switch를 선택적으로 사용하면 가독성과 유지보수성을 높일 수 있습니다.

---
