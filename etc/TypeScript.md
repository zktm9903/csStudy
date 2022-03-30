## 타입스크립트란?

- 자바스크립트에 **타입**을 부여한 언어
- 자바스크립트의 확장된 언어
- 자바스크립트와 달리 브라우저에서 실행하려면 파일을 한번 변환해주는 **컴파일** 과정을 거쳐야함
  
## 타입스크립트를 쓰는 이유?

1. 에러의 사전방지
```js
// js
function sum(a, b) {
    return a + b;
}

sum(10, 20); // 30
sum('10', '20'); // 1020

// ts
function sum(a: number, b: number) {
    return a + b;
}

sum(10, 20); // 30
sum('10', '20'); // error
```
    사전에 데이터 타입을 정의하여 예외 상황을 방지

2. 코드 자동 완성과 가이드
```js
// js
function sum(a, b) {
    return a + b;
}
var total = sum(10, 20);
total.toLocaleString(); // 개발자가 직접 작성

// ts
function sum(a: number, b: number): number {
    return a + b;
}
var total = sum(10, 20);
total.toLocaleString(); // 자동완성 기능으로 작성
```
    
    데이터 타입이 정해져 있어 그에 맞는 함수들은 자동완성 가능함

## 타입스크립트 기본 타입
- Boolean
- Number
- String
- Object
- Array
- Tuple
- Enum
- Any
- Void
- Null
- Undefined
- Never

---

- 변수 선언 방식
```js
let 변수이름: 타입 = 타입에 맞는 값;

ex)
let str: string = 'hi';
let arr: number[] = [1,2,3];
```

---

- Array
```js
let arr: number[] = [1,2,3];
let arr: Array<number> = [1,2,3]; //제네릭 사용 가능
```
---
- Tuple  
  - 배열의 길이가 고정, 각 요소의 타입이 지정되어 있음
```js
let arr: [string, number] = ['hi', 10];

arr[1].concat('!'); // Error, 'number' does not have 'concat'
arr[5] = 'hello'; // Error, Property '5' does not exist on type '[string, number]'.
```
---
- Enum
  - 특정 값(상수)들의 집합
```js
enum Avengers { Capt, IronMan, Thor }

let hero: Avengers = Avengers.Capt;
let hero: Avengers = Avengers[0];
```
---
- Any
    - 모든 타입에 대해 허용
```js
let str: any = 'hi';
let num: any = 10;
let arr: any = ['a', 2, true];
```
---
- Void
  - undefined, null만 할당, 함수에서는 반환값을 설정 안함
```js
let unuseful: void = undefined;

function notuse(): void {
  console.log('sth');
}
```
---
- Never
  - 함수의 끝에 절대 도달하지 않는다는 의미
```js
function neverEnd(): never {
  while (true) {

  }
}
```