This pattern involves creating a **window** which can either be an array or number from one positionto another

Depending on a certain condition, the window either increases or closes (and a new window is created)

Very useful for keeping track of a subset of data in an array/string etc.

배열이나 스트링 같은 데이터를 가지고 있고, 데이터의 연속성 하위구조를 찾을 때 유용한 패턴.

“hellothere”

만약에 서로 다른 글자가 가장 길게 이어지는 부분을 찾는 함수를 만들라고 할 때 슬라이딩 윈도우 패턴을 사용할 수 있습니다. 또한 이어서 보여줄 다른 예시는 maxSubarraySum이라는 건데요.
<img width="1311" alt="스크린샷 2021-12-27 오후 5 53 30" src="https://user-images.githubusercontent.com/80245801/147456210-6ebc0109-2ef1-4aa9-b295-c56dd99a4612.png">
위처럼 배열을 입력하면 서로 접해 있는 2개의 숫자 합 중 가장 큰 것을 출력합니다.   

- 정수로 된 배열과 n이라는 숫자를 입력하는 함수 maxSubarraySum를 만드세요.

→ 정수로 된 배열이기만 하면 됩니다. 그리고 말했듯이 숫자 하나를 입력해야 합니다. 

→ 그리고 함수는 그 배열에 있는 n개의 연속된 요소의 최대 합계를 구합니다.

---

<img width="1001" alt="스크린샷 2021-12-27 오후 6 01 38" src="https://user-images.githubusercontent.com/80245801/147456257-3d04ccea-1093-4175-af56-0d497105c808.png">

---
<img width="865" alt="스크린샷 2021-12-27 오후 6 08 25" src="https://user-images.githubusercontent.com/80245801/147456278-1bcd02e1-ee76-4a82-a05d-e49ea1a4e057.png">
