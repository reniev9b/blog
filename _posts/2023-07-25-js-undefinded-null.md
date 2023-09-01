---
title: "[JS] undefined, null"
date: 2023-07-25 12:00:00 +09:00
categories: [Tech Notes, Frontend]
tags: [2023 NIPA AI Web Camp, Frontend, Javascript, JS]
---

## null과 undefined의 차이점

---

의미 :

- **null** : 개발자가 변수에 "값이 없음"을 명시적으로 할당하는 값.
- **undefined** : 변수가 선언되었지만, 값을 할당받지 않은 상태를 나타내는 값.

할당 여부 :

- **null** : 개발자가 명시적으로 변수에 null을 할당.
- **undefined** : 자바스크립트 엔진이 변수를 선언할 때 자동으로 할당.

타입 :

- **null** : 객체 타입의 값.
- **undefined** : 원시 타입의 값.

처리 방식 :

- **null** : null은 변수에 명시적으로 할당된 값이므로, 변수에 null이 할당된 경우 해당 변수는 "값이 없음"으로 간주된다.
- **undefined** : 변수에 아무 값도 할당되지 않은 경우 자바스크립트 엔진이 자동으로 undefined를 할당한다.

## 그래서 어떨 때 값이 null이 되고 undefined이 되는지

---

### Case 1. 변수에 아무 값도 할당하지 않음 : undefined

```javascript
let variable1;
console.log(variable1); // undefined
```

변수를 선언하고 값을 할당하지 않으면, 변수는 자동으로 `undefined`로 초기화된다.
이는 자바스크립트 엔진이 변수를 생성할 때 자동으로 수행되는 동작으로, 해당 변수는 메모리 공간을 차지하고 있지만 값이 없음을 나타내는 `undefined`가 할당된 상태다.

### Case 2. 접근하려는 객체의 속성이 존재하지 않음 : undefined

```javascript
let obj = { key: "value" };
console.log(obj.keyUnknown); // undefined
```

객체에 존재하지 않는 속성에 접근하면 `undefined`가 반환된다.
이때, 객체에 해당 속성이 실제로 존재하지 않기 때문에 `undefined`로 초기화된 것이 아니라, 해당 속성은 그냥 없는 것으로 간주된다.

### Case 3. 실행한 함수에 return문이 없음 : undefined

```javascript
function returnNothing() {}
console.log(returnNothing()); // undefined
```

`returnNothing()` 함수가 호출될 때, 함수에 `return` 문이 없거나 명시적으로 `return undefined;` 를 사용한 경우 자바스크립트 엔진은 암묵적으로 `undefined`를 반환한다.
이 경우 함수가 반환하는 값이 없으므로 반환값으로 `undefined`가 자동으로 할당되는 것이기 때문에 값이 초기화된 것은 아니다.

### Case 4. 변수에 undefined 값을 명시적으로 할당함 : undefined

```javascript
let variable2 = undefined;
console.log(variable2); // undefined
```

### Case 5. 변수에 null 값을 명시적으로 할당함 : null

```javascript
let variable3 = null;
console.log(variable3); // null
```

`null`은 개발자가 변수에 "값이 없다"는 의미로 명시적으로 할당하는 값이다.
`variable3`에 할당한 `null` 값이 출력된다.

## 비교연산자를 활용하여 각각의 케이스에 따라 null인지 undefined인지 확인

---

```js
let variable1;
let variable2 = undefined;
let variable3 = null;
let obj = { key: "value" };

console.log(variable1 === null); // false
console.log(variable1 === undefined); // true

console.log(variable2 === null); // false
console.log(variable2 === undefined); // true

console.log(variable3 === null); // true
console.log(variable3 === undefined); // false

console.log(obj.keyUnknown === null); // false
console.log(obj.keyUnknown === undefined); // true
```
