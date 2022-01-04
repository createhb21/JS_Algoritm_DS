## Objectives

- 재귀가 무엇인지 정의하고 어떻게 사용되는 지를 안다.
- 재귀형 함수를 작성할 때 반드시 필요한 두 가지를 배운다.
- 콜 스택이라고 부르는 것에 대해 배운다. 또한 콜 스택과 재귀형 함수를 디버그 하는 법을 배운다.
- 헬퍼 메소드 제귀와 일반 재귀를 배우고 이 둘을 비교한다.

---

## 재귀 함수를 사용하는 이유

### What is recursion ?

- 재귀는 자기자신을 호출하는 과정이다. 즉, 재귀라고 하면 자기자신을 호출하는 함수를 말한다.

### Why do I need to know this ?

- 재귀함수 is Everywhere.
    - JSON.parse / JSON.stringify
    - document.getElementById and DOM traversal algorithms
    - Object traversal
    - We will see it with more complex data structures
    
---

💡 The call stack
  - It’s a stack data structure - we’ll talk about that later
  - Any time a function is invoked it is placed (**pushed**) on the top of the call stack
  - When Javascript sees the **return** keyword or when the function ends, the compiler will    remove(**pop**)


- 재귀 함수를 작성하게 되면 호출 스택을 가지고 작업을 해야하는 경우가 많아진다.
- 콜 스택은 자바스크립트에서 정적인 데이터 구조를 대상으로만 뒤에서 작동한다.
- You’re used to functions being pushed on the call stack and popped off when they are done
- Whene we write recursive functions, we keep pushing new functions onto the call stack !

재귀 함수는 스스로를 호출한다. 그렇다면 재귀 함수는 언제 멈출까..? 그렇지 않다면 콜 스택을 계속해서 쌓일까..?

---

## How recursive functions work

Invoke the same functions with a different input until you reach your base case !

같은 함수를 계속해서 호출한다는 것이 기본 개념이지만, 반드시 멈추는 지점이 있어야 한다. 그것이 바로 Base Case 

## Base Case(기반 조건)

기반조건이란 재귀가 멈추는 지점이다. 즉 재귀란 반드시 끝 지점이 있어야 한다. 그냥 자신을 영원히 호출하는 게 아니다. 

# So, Two essential parts of a recursive function!

- Base Case
- Different Input
    - 매번 다른 데이터(매번 목록이 바껴야 함)

---

## Example

```tsx
function countDown(num) {
	if(num <= 0) {     // BASE CASE
		console.log("All done!");
		return;     // IMPORTANT, NEED RETURN !
	}
	console.log(num);
	num--;
	countDown(num);
}
```

이 함수는 입력한 숫자에서 시작해서 숫자를 쭉 출력한다. 예를 들어 5를 입력하면 5, 4, 3, 2, 1이 출력되고 끝이 난다. 

---

## Our second recursive function

```tsx
function sumRange(num) {
8=	if(num === 1) return 1;
	return num + sumRange(num - 1);
}
```

- Can you spot the base case?
- Do you notice the different input?
- What would happen if we didn’t return?

---

## 재귀함수로 Factorial 구현

```tsx
// 1. using loop
function factorial(num) {
	let total = 1;
	for(let i = num; i > 1; i--) {
		total *= i
	}
return total;
}

// 2. using recursive
// 기반 조건과 매번 달라져야 하는 변수를 이해해보자. 
fucntion factorial(num) {
	if(num === 1) return 1;
	return num * factorial(num - 1)
}
```

---

## Where things go wrong

- No base case or Wrong base case
- Forgetting to return or returning the wrong thing!
- Stack overflow!

---

## 재귀와 함께 흔히 사용되는 헬퍼 메소드 재귀 패턴

```tsx
function outer(input) {
	let outerScopedVariable = []

	function helper(helperInput) {
		// modify the outerScopedVariable
		helper(helperInput--)
	}

	helper(input)

	return outerScopedVariable;
}
```

Another Example

- Let’s try to collect all of the odd values in an array

```tsx
function collectOddValues(arr) {
	let result = [];

	function helper(helperInput) {
		if(helperInput.length === 0) {
			return;
		}

		if(helperInput[0] % 2 !== 0) {
			result.push(helperInput[0])
		}

		helper(helperInput.slice(1))
	}

	helper(arr)

	return result;
}

// 이 방법은 배열이나 일렬로 되어 있는 다른 데이터 구조의 결과를 합칠 때 자주 사용할 수 있다. 
```

💡 헬퍼 메소드 재귀는 재귀형이 아닌 외부 함수가 재귀형인 내부 함수를 호출하는 형태


---

## 순수 재귀(PURE RECURSION)

```tsx
function collectOddValues(arr) {
	let newArr = [];
	
	if(arr.length === 0) {
		return newArr;
	}

	if(arr[0) % 2 !== 0) {
		newArr.push(arr[0])
	}

	newArr = newArr.concat(collectOddValues(arr.slice(1)));
	return newArr;
}
```

Pure recursion Tips 

- For arrays, use methods like **slice**, **the** **spread** **operator**, and **concat** that make copies of arrays so you do not mutate them
- Remember that strings are immutable so you will need to use methods like **slice**, **substr**, or **substring** to make copies of strings
- To make copies of objects use **Object.assign** or **the spread operator**
