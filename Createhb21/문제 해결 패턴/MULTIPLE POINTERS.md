# MULTIPLE POINTERS


💡 Creating **pointers** or values that correspond to an index or position and move towards the beginning, end or middle based on a certain condition
**Very** efficient for solving problems with minimal space complexity as well


핵심은 인덱스나 위치에 상응하는 포인터나 값을 만든 다음 특정한 조건을 충족시키면, 처음 지점이나 마지막 지점 또는 중간에서 양쪽으로 움직이게 하는 것... 이해가 잘 안가니 예시를 보자.

어레이나 스트링, 단일 연결 리스트, 이중 연결 리스트 등에서 한 쌍의 값을 탐색하거나 조건에 맞는 무언가를 탐색한다는 것. 보통은 한 쌍은 탐색한다. 그리고 두가지의 참조를 사용한다. 

---

## An Example

Write a function called **sumZero** which accepts a **sorted** array of integers. The function should find the **first** pair where the sum is 0. Return an array that includes both valus that sum to zero or undefined if a pair does not exist

<img width="586" alt="스크린샷 2021-12-27 오후 4 28 13" src="https://user-images.githubusercontent.com/80245801/147448953-c8e5dd96-7d6a-4611-8996-4e6c42f305f8.png">
정렬된 정수로 구성된 배열을 입력하는 sumZero라는 이름의 함수를 만드세요. 

→ 이 배열은 순서대로 낮은 것부터 높은 것까지로 정렬되어야 한다.

함수는 합이 0인 첫번째 쌍의 정수를 구해야 합니다. 

→ 한 숫자와 다른 숫자를 더했을 때 0이 되는 첫번째 정수쌍을 말하고 있다.

→ 두개의 포인터를 사용하자.

---

<img width="485" alt="스크린샷 2021-12-27 오후 4 31 25" src="https://user-images.githubusercontent.com/80245801/147448990-c25691ab-5d40-4f22-a66e-fc1304f5bba5.png">


간단한 답안으로, 중첩된 루프를 가지며 빅오(n제곱)의 시간 복잡도를 가진다.

---

<img width="493" alt="스크린샷 2021-12-27 오후 4 40 55" src="https://user-images.githubusercontent.com/80245801/147449045-d1f3168f-8468-4221-b5ed-868e27f08d1e.png">

```tsx
function sumZero(arr) {
    let left = 0;
    let right = arr.length - 1;
    while (left < right) {
        let sum = arr[left] + arr[right];
        if (sum === 0) {
            return [arr[left], arr[right]];
        } else if (sum > 0) {
            right--;
        } else {
            left++;
        }
    }
}
```

이 예시는 두개의 포인터를 사용했다. 하나는 왼쪽 끝부터, 하나는 오른쪽 끝부터 중앙을 향해 움직였다. 

이게 유일한 정답은 아니다. 다음번에는 양쪽에서 동시에 움직이는 게 아니라 같은 방향에서 시작해서 움직이는 문제를 보자(왼쪽에만 두개의 포인터가 있는 식).
