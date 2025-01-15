# JavaScript 반복문: While과 Do...While

JavaScript에서 **`while`**과 **`do...while`** 반복문은 특정 조건이 참(`true`)인 동안 코드를 반복 실행하는 데 사용됩니다. 두 반복문은 조건을 평가하고 반복을 수행한다는 점에서 비슷하지만, 조건 평가 시점에 따라 동작 방식이 다릅니다.

---

## 📖 While 반복문

### **1. 개념**
- `while` 반복문은 **조건이 참일 때만** 코드를 실행합니다.
- 조건이 거짓이면 반복을 종료합니다.
- 조건을 먼저 평가한 후 실행되므로, 조건이 처음부터 거짓이라면 코드 블록은 **한 번도 실행되지 않을 수 있습니다**.

---

### **2. 구문**
```
while (condition) {
    // 조건이 true일 때 실행되는 코드
}
```

- **condition**: 반복 여부를 결정하는 논리 표현식.

---

### **3. 예제**

#### 기본 사용:
```
let count = 0;

while (count < 5) {
    console.log(`Count: ${count}`);
    count++;
}
// 출력:
// Count: 0
// Count: 1
// Count: 2
// Count: 3
// Count: 4
```

#### 사용자 입력 처리:
```
let input;

while (input !== "exit") {
    input = prompt("Enter a command (type 'exit' to quit):");
    console.log(`You entered: ${input}`);
}
// 사용자가 "exit"를 입력할 때까지 반복
```

#### 무한 루프:
- 조건이 항상 참이라면 무한히 실행됩니다. 반드시 종료 조건을 포함해야 합니다.
```
let i = 0;

while (true) {
    console.log(i);
    if (i === 10) break; // 종료 조건
    i++;
}
// 출력: 0부터 10까지 출력 후 종료
```

---

## 📖 Do...While 반복문

### **1. 개념**
- `do...while` 반복문은 **코드를 먼저 실행한 후** 조건을 평가합니다.
- 따라서, 조건이 거짓이라도 코드 블록은 **적어도 한 번은 실행됩니다**.

---

### **2. 구문**
```
do {
    // 실행할 코드
} while (condition);
```

- **condition**: 반복 여부를 결정하는 논리 표현식.

---

### **3. 예제**

#### 기본 사용:
```
let count = 0;

do {
    console.log(`Count: ${count}`);
    count++;
} while (count < 5);
// 출력:
// Count: 0
// Count: 1
// Count: 2
// Count: 3
// Count: 4
```

#### 사용자 입력 처리:
- 사용자 입력을 최소 한 번은 처리해야 할 때 유용합니다.
```
let password;

do {
    password = prompt("Enter your password:");
} while (password !== "1234");

console.log("Access granted.");
// 사용자가 "1234"를 입력할 때까지 반복
```

#### 무한 루프:
- 종료 조건 없이 작성하면 무한히 실행됩니다.
```
let i = 0;

do {
    console.log(i);
    if (i === 10) break; // 종료 조건
    i++;
} while (true);
// 출력: 0부터 10까지 출력 후 종료
```

---

## 🛠️ While vs Do...While

| 특징               | While                                  | Do...While                              |
|--------------------|---------------------------------------|----------------------------------------|
| 조건 평가 시점      | 반복 전에 조건을 평가                  | 반복 후에 조건을 평가                   |
| 최소 실행 횟수      | 조건이 처음부터 거짓이면 한 번도 실행되지 않음 | 적어도 한 번은 실행됨                   |
| 주요 용도           | 조건에 따라 반복 여부를 결정           | 최소 한 번은 실행이 보장되어야 하는 경우 |

---

## 📂 활용 사례

### While 활용:
#### 데이터 처리:
데이터가 남아 있는 동안 작업을 수행합니다.
```
let data = [1, 2, 3, 4, 5];

while (data.length > 0) {
    console.log(data.pop());
}
// 출력:
// 5
// 4
// 3
// 2
// 1
```

---

### Do...While 활용:
#### 사용자 입력 유효성 검사:
사용자 입력을 최소 한 번은 처리해야 할 때 유용합니다.
```
let number;

do {
    number = parseInt(prompt("Enter a number greater than 10:"), 10);
} while (number <= 10);

console.log(`You entered: ${number}`);
// 사용자가 입력한 숫자가 10보다 클 때까지 반복
```

---

## ✨ 요약

1. **While**
   - 조건을 먼저 평가하고, 참일 경우에만 코드 블록을 실행.
   - 조건이 처음부터 거짓이라면 코드가 한 번도 실행되지 않음.

2. **Do...While**
   - 코드를 먼저 실행한 후 조건을 평가.
   - 적어도 한 번은 코드 블록이 실행되는 것이 보장됨.

3. 두 반복문 모두 특정 작업을 여러 번 수행하거나 데이터 처리를 자동화하는 데 유용하며, 상황에 맞게 선택적으로 사용할 수 있습니다.

---
