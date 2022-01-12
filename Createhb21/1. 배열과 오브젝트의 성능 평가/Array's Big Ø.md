# 2️⃣ Array's Big Ø

- 빅오표기법과 성능이라는 관점에서 배열을 이해해보고 그걸 객체와 비교해보자.

<aside>
💡 배열이 중요한 이유는, 순서가 있다는 것. 데이터가 모두 뭉쳐서 하나로 떠다니는 객체와 달리 배열에 있는 데이터는 그 자체로 순서가 존재한다.

순서가 필요할 때는 아주 유용한데, 일부 동작을 실행할 때는 비용이 있을 수 있다.

</aside>

```tsx
let names = ["Michael", "Melissa", "Andrea"];

let values = [true, [], 2, "awesome"];
```

## When to use Arrays

- When you need order
    - 배열이 지구상에서 유일하게 순서를 가지는 데이터 구조는 ❌
- When you need fast access / insertion and removal (sort of....)

## Big Ø of Arrays

- Insertion - **it depends....**
    - insert at end - **O(1)**
    - insert at beginning - **O(N)**
- Removal - **it depends....**
    - removal at end - **O(1)**
    - removal at beginning - **O(N)**
- Searching - **O(N)**
- Access - **O(1)**

**→ Let's see what we mean by that!**

## Big Ø of Arrays Operations

- push- **O(1)**
- pop - **O(1)**
- shift - **O(N)**
- unshift - **O(N)**

you don't need to know all this...

                       😵

- concat - **O(N)**
- slice - **O(N)**
- splice - **O(N)**
- sort - **O(N * log N)**
- forEach/map/filter/reduce/etc. - **O(N)**

## 객체와 배열의 차이점

먼저, 객체는 거의 모든 것에 있어서 더 빠르지만 순서가 없다

배열은 순서가 필요할 때는 좋지만 끝 부분에서 삽입과 제거를 하는 것이 좋으며 시작 부분에서 삽입과 제거를 하는 것은 피라는 게 좋다. 왜냐하면 누적효과를 일으켜서 모든 요소들이 뒤로 밀려서 다시 인덱스를 부여받아야 하기 때문이다. 가운데 부분에서 삽입하거나 제거하는 것도 마찬가지이다. 이러면 또 다시 누적효과가 발생하는데, 추가하거나 제거한 요소 뒤로 얀쇄적인 인덱스 재부여가 발생해야 하기 때문이다.
