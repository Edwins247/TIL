# TypeScript 모듈과 타입 선언, 가져오기 및 내보내기 정리

TypeScript에서 **모듈(Module)** 은 코드의 재사용성과 유지보수성을 높이기 위해 코드 조각을 분리하고 관리하는 방법입니다. 모듈은 JavaScript의 ES6 모듈 시스템을 기반으로 하며, TypeScript는 타입과 인터페이스를 포함한 다양한 선언을 내보내고 가져오는 기능을 제공합니다. 이 문서에서는 **모듈의 개념**, **타입 선언**, **타입 가져오기와 내보내기**에 대해 정리합니다.

---

## 📖 TypeScript 모듈이란?

- **모듈(Module)** 은 코드의 논리적 단위를 정의하며, 외부에서 사용할 수 있는 기능(클래스, 함수, 변수, 타입 등)을 내보내고(import/export) 다른 파일에서 가져올 수 있습니다.
- TypeScript는 ES6 모듈 시스템(`import`/`export`)을 기반으로 동작하며, 추가적으로 타입과 인터페이스를 내보내고 가져오는 기능을 제공합니다.
- 모듈은 파일 단위로 정의되며, 각 파일은 자체적인 스코프를 가집니다.

---

## 📂 기본 모듈 사용법

### **1. 내보내기 (Export)**

#### **개념**
- 모듈에서 특정 변수, 함수, 클래스 또는 타입을 외부에서 사용할 수 있도록 내보냅니다.
- 두 가지 방식으로 내보낼 수 있습니다:
  1. **Named Export**: 여러 항목을 이름으로 내보냄.
  2. **Default Export**: 하나의 기본 항목을 내보냄.

---

#### 예제: Named Export
```typescript
// math.ts
export const add = (a: number, b: number): number => a + b;
export const subtract = (a: number, b: number): number => a - b;
```

#### 예제: Default Export
```typescript
// math.ts
const multiply = (a: number, b: number): number => a * b;
export default multiply;
```

---

### **2. 가져오기 (Import)**

#### **개념**
- 다른 모듈에서 내보낸 항목을 현재 파일로 가져옵니다.
- `import` 키워드를 사용하며, Named Export와 Default Export에 따라 구문이 다릅니다.

---

#### 예제: Named Import
```typescript
// main.ts
import { add, subtract } from "./math";

console.log(add(10, 5)); // 출력: 15
console.log(subtract(10, 5)); // 출력: 5
```

#### 예제: Default Import
```typescript
// main.ts
import multiply from "./math";

console.log(multiply(10, 5)); // 출력: 50
```

#### 예제: 모든 항목 가져오기
```typescript
// main.ts
import * as MathUtils from "./math";

console.log(MathUtils.add(10, 5)); // 출력: 15
console.log(MathUtils.subtract(10, 5)); // 출력: 5
```

---

## 📂 타입 선언 및 내보내기

TypeScript에서는 타입과 인터페이스도 모듈로 내보내고 가져올 수 있습니다.

### **1. 타입 선언 내보내기**

#### 예제:
```typescript
// types.ts
export interface User {
    id: number;
    name: string;
}

export type ApiResponse<T> = {
    data: T;
    statusCode: number;
};
```

---

### **2. 타입 선언 가져오기**

#### 예제:
```typescript
// main.ts
import { User, ApiResponse } from "./types";

const user: User = { id: 1, name: "Alice" };

const response: ApiResponse<User> = {
    data: user,
    statusCode: 200,
};

console.log(response);
```

---

## 📂 Re-export (다시 내보내기)

### **개념**
- 한 모듈에서 가져온 항목을 다른 모듈로 다시 내보낼 수 있습니다.
- 이를 통해 여러 모듈의 내용을 하나의 진입점(entry point)에서 관리할 수 있습니다.

---

### **예제**
```typescript
// mathOperations.ts
export { add, subtract } from "./math";
export { divide } from "./advancedMath";
```

```typescript
// main.ts
import { add, subtract, divide } from "./mathOperations";

console.log(add(10, 5)); // 출력: 15
console.log(divide(10, 2)); // 출력: 5
```

---

## 📂 Import와 Export의 주요 형태

| 형태                  | 설명                                                                 | 예제                                      |
|-----------------------|----------------------------------------------------------------------|------------------------------------------|
| Named Export          | 여러 항목을 이름으로 내보냄                                          | `export const add = ...;`                |
| Default Export        | 하나의 기본 항목만 내보냄                                            | `export default function() {...}`        |
| Named Import          | 특정 이름으로 항목 가져옴                                            | `import { add } from "./file";`          |
| Default Import        | 기본 항목 가져옴                                                    | `import multiply from "./file";`         |
| 모든 항목 가져오기     | 모든 내용을 객체 형태로 가져옴                                       | `import * as Utils from "./file";`       |
| Re-export             | 다른 모듈에서 가져온 내용을 다시 내보냄                              | `export { add } from "./file";`          |

---

## 📂 타입 전용 가져오기 및 내보내기

TypeScript에서는 타입만 가져오거나 내보낼 때 `type` 키워드를 사용할 수 있습니다. 이는 런타임에 영향을 미치지 않으며 컴파일 시 제거됩니다.

### **1. 타입 전용 내보내기**

#### 예제:
```typescript
// types.ts
export type User = {
    id: number;
    name: string;
};
```

---

### **2. 타입 전용 가져오기**

#### 예제:
```typescript
// main.ts
import type { User } from "./types";

const user: User = { id: 1, name: "Alice" };
```

#### 설명:
- `type` 키워드를 사용하면 해당 선언이 런타임 코드에 포함되지 않으며 컴파일 시 제거됩니다.

---

## 📂 활용 사례

### 1. 유틸리티 함수와 타입 분리

#### 예제:
```typescript
// utils.ts
export const toUpperCase = (str: string): string => str.toUpperCase();

export type StringTransformer = (input: string) => string;
```

```typescript
// main.ts
import { toUpperCase } from "./utils";
import type { StringTransformer } from "./utils";

const transformer: StringTransformer = toUpperCase;
console.log(transformer("hello")); // 출력: HELLO
```

---

### 2. API 요청 및 응답 모델링

#### 예제:
```typescript
// apiModels.ts
export interface User {
    id: number;
    name: string;
}

export type ApiResponse<T> = {
    data?: T;
    error?: string;
};
```

```typescript
// apiClient.ts
import { ApiResponse, User } from "./apiModels";

function fetchUser(): ApiResponse<User> {
    return {
        data: { id: 1, name: "Alice" },
    };
}

console.log(fetchUser());
```

---

## ✨ 요약

1. **모듈이란?**
   - 코드를 논리적으로 분리하여 재사용성과 유지보수성을 높이는 방법.
   - ES6 모듈 시스템(`import`/`export`) 기반.

2. **내보내기와 가져오기**
   - Named Export/Import와 Default Export/Import를 지원.
   - 모든 항목을 객체 형태로 가져오거나 다시 내보낼 수도 있음.

3. **타입 선언**
   - 인터페이스와 타입도 모듈로 정의하고 재사용 가능.
   - `type` 키워드를 사용해 런타임 코드에 영향을 미치지 않도록 설정 가능.

4. 활용 사례:
   - 유틸리티 함수와 데이터 모델링 분리.
   - API 요청 및 응답 처리 모델링.

---
