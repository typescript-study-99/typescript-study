---
title: enum
---

```ts
enum Direction {
  Up,
  Down,
  Left,
  Right
}
```

위 타입스크립트 enum은 아래와 같이 자바스크립트 코드로 컴파일 됩니다

```js
var Direction;
(function (Direction) {
    Direction[Direction["Up"] = 0] = "Up";
    Direction[Direction["Down"] = 1] = "Down";
    Direction[Direction["Left"] = 2] = "Left";
    Direction[Direction["Right"] = 3] = "Right";
})(Direction || (Direction = {}));
```

<details>
<summary>Q: 타입스크립트에서 "console.log(Direction)"의 값은?</summary>

```console
{
  "0": "Up",
  "1": "Down",
  "2": "Left",
  "3": "Right",
  "Up": 0,
  "Down": 1,
  "Left": 2,
  "Right": 3
} 
```

> 리버스 맵핑: [TypeScript: Handbook - Enums#reverse-mappings](https://www.typescriptlang.org/docs/handbook/enums.html#reverse-mappings)

<details>
<summary>
추가 문제
</summary>
Q: 그렇다면, "type DirectionType = keyof typeof Direction;" 해당 DirectionType의 타입 추론 결과는?

<details>
<summary>
정답 보기
</summary>
'Up' | 'Down' | 'Left' | 'Right'
</details>

</details>

</details>

---

```ts
let dir = Direction.Up;
dir = Direction.Down;
let currentDir = Direction[0];
currentDir = Direction[dir];

console.log(currentDir);
```
<details>
<summary>
Q: 위와 같은 타입스크립트에서 코드가 있을 때, currentDir의 로그 값은?
</summary>

정답: 'Down'

[playground에서 보기](https://www.typescriptlang.org/play?#code/PTAECIGEBcCcBsAUkC2ATAlKA1KAogHbQCms4ognGuAC46IIMDgF02Aa46AEoCuBogIT2A9S6IC4LgWs7AGquAb0dAAZAPYBzAM6BbhcAi46ECqa4A9xwC6rgF57AHIOAUsYBQxAmxSgAIgEtYxAMbQrUzgG9DoUAFUADgBp3llIA7gT+HhLEAGbQYaxWMgAW0IYAvoaG0ACe3sSWNvaOzgDKcFYEMqAAvKAA1sSZUpGgWTmNebYOTgQA3OnwxNCgaDZV7QVdAHQ+vcOwo9YdhQQTFsE9hv2DdmywtkQL8-mdzgDaAAwAur3buybQB9UL46ezV+l2znJS-RN2-QCGsEQGHen2+xAm8FkiCexwIIMMHwIXx+UJkiFmvlANz29xsGCAA)
</details>

---

enum은 다음과 같이 `const enum` 키워드를 활용하여 표현할 수 있다.

```ts
const enum EDirection {
  Up,
  Down,
  Left,
  Right,
}
```

<details>
<summary>
그렇다면, 오브젝트 리터럴을 활용하여 위와 같은 const enum을 표현하는 방식은?
</summary>
<pre>
const ODirection = {
  Up: 0,
  Down: 1,
  Left: 2,
  Right: 3,
} as const;
//^? 타입 단언
</pre>
</details>

---

참고자료: (1) 승귤 on X: "우아한 타입스크립트 보고 있는데, enum을 사용하는 이유도 사용하지 않는 이유도 납득이 간드 https://t.co/LmWH8w6Rhr" / X](https://twitter.com/wapj2000/status/1722924411114889322/photo/1)

> 해당 포스트의 출처: 우아한 타입스크립트 with 리액트 https://g.co/kgs/kNw7riv