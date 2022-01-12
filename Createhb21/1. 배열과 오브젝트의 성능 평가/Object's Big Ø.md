# Goal

- 객체와 배열이 Big Ø라는 관점에서 어떻게 작동하는지 알 수 있다.
- 배열의 시작부분에 요소를 추가하는 것이 왜 소모가 큰 것인지 알 수 있다.
- 배열과 객체의 실행시간 그리고 그들의 내장 메서드를 비교 대조해본다.

---

# 1️⃣ Object's Big Ø

- 빅오표기법과 성능이라는 관점에서 객체를 이해해보자.

<aside>
💡 객체란 순서가 배정되지 않은 데이터 구조이고 모든 정보는 키-값 구조로 저장된다.

</aside>

```tsx
let instructor = {
	firstName: "Lee",
	isInstructor: true,
	favoriteNumbers: [0,1,2,3]
}
```

## When to use objects

- When you don't need order
- When you need fast access / insertion and removal

## Big Ø of Objects

- Insertion - **O(1)**
- Removal - **O(1)**
- Searching - **O(N)**
- Access - **O(1)**

**→ When you don't need any ordering, objects are an excellent choice!**

## Big Ø of Object Methods

- Object.keys - **O(N)**
- Object.values - **O(N)**
- Object.entries - **O(N)**
- hasOwnProperty - **O(1)**

### 결론적으로, 객체는 정말 모든 것을 빠르게 처리할 수 있다. 그렇지만 순서가 없다.

객체는 기본적인 것들로 많은 경우 잘 작동하고, 키와 값의 순서쌍이다. 대부분의 기존 동작들, 삽입, 접근, 업데이트, 제거 등이 다 상수값의 시간을 가지고 탐색은 좀 예외적인데, 그렇지만 탐색도 빅오(n)이라서 n이 커지는 만큼안 커지는 1차함수 관계이다.

그리고 keys, values, entries처럼 객체에 있는 데이터를 기반으로 배열을 만드는 메소드들이 있는데 그러면 객체가 커질수록 동작의 개수도 많아지고 이것들을 엮는데 걸리는 시간도 길어진다. 따라서 이 녀석들도 빅오(n)의 값을 가진다.

다음으로 배열에 대한 것들을 보겠지만 배열은 많은 부분에서 빠르게 작동하지만 순서가 있기 때문에 무엇을 하는지에 따라 속도가 느려질 수도 있다. 

---
