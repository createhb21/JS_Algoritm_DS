## ANAGRAMS

Given two strings, write a function to determine if the second string is an anagram of the first. An anagram is a word, phrase, or name formed by rearranging the letters of another, such as cinema, formed from iceman.

<aside>
💡 이 함수는 두개의 스트링을 취하며, 두 스트링이 서로에 대한 아나그램인 경우 true를 출력합니다.

</aside>
<img width="504" alt="스크린샷 2021-12-27 오후 3 24 12" src="https://user-images.githubusercontent.com/80245801/147443981-101535b4-2f32-440f-b5ad-eaabc63022c0.png">


이것을 풀 수 있는 방법은 많지만, 여기서 떠올릴 수 있는 생각과 목표는 **이 문제를 빈도 카운터 패턴을 활용하여 풀 수 있다는 것이다.** 

이 예시는 두 개의 스트링, 두 개의 요소가 있는 완변학 활용 문제로 양쪽에서의 문자의 노출 빈도를 비교해서 그 둘이 같은지를 보고 싶은 것이다(빈도가 맞아야 한다).

---

**빈도 카운터 패턴을 활용하여 풀어보자.**

→ 루프를 사용해서 만든 객체를 활용하고 중첩되지 않는 두번째 루프를 사용하여 문제를 풀어봅시다(이러면 빅오(n)의 시간 복잡도를 유지할 수 있음)

```tsx
function validAnagram(first, second) {
    if (first.length !== second.length) {
        return false;
    }

    const lookup = {};

    for (let i = 0; i < first.length; i++) {
        let letter = first[i];
        lookup[letter] ? (lookup[letter] += 1) : (lookup[letter] = 1);
    }

    for (let i = 0; i < second.length; i++) {
        let letter = second[i];
        if (!lookup[letter]) {
            return false;
        } else {
            lookup[letter] -= 1;
        }
    }

    return true;
}
```

---

결국 빈도 카운터 패턴은...

여러 데이터가 있고 그것들을 서로 비교해야 하는 식의 문제라면, 그리고 특히 그것들이 같은 개별 데이터 조각을 가지고 있는지 봐야 한다면, 여기서 본 아나그램이든 한 배열과 다른 배열이 제곱을 제외하고 모두 같은 요소를 가지고 있는 것이들 간에 말이다. 

같은 숫자들이 있는데 순서만 다르게 있는 경우도 마찬가지이다.

하여튼 정말 여러가지로 적용해볼 수 있다.
