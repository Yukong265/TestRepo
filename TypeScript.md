# TypeScript란

## Definition

- MS에서 개발한 개발한 언어
- JS에 타입을 부여한 상위 호환 언어

### Why TS?

#### Error Prevention

- 타입 에러를 방지해준다

```js
function sum(a, b) {
  return a + b;
}
```
```ts
function sum(a: number, b: number) {
  return a + b;
}
```
- 위의 두 코드는 매개변수에 따라 다른 값이 나옵니다

```js
sum(1, 3)
```
 위의 코드는 둘 다 4가 나오지만

```js
sum('1', '3')
```
 만약 위의 코드로 실행을 시킨다면?
 JS는 13, TS는 Type Error를 발생시킵니다.



#### Code Auto-Completion

- 코드의 자동완성 기능을 사용 할 수 있다.
```js
function sum(a, b) {
  return a + b;
}
var total = sum(10, 20);
total.toLocaleString();
```

- 만약 위의 코드를 작성한다고 할 때
  - JS는 직접 코드를 쓰는 반면, TS는 자동 완성 기능을 사용 할 수 있다.
