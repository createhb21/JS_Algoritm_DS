# PROBLEM SOLVING

- Understand the Provlem
- Explore Concrete Examples
- Break It Down
- Solve/Simplify
- Look Back and Refactor

# LOOK BACK & REFACTOR

Congrats on solving it, but you’re not done!

# REFACTORING QUESTIONS

- Can you check the result?
- Can you derive the result differently?
- Can you understand it at a glance?
    - 당신의 코드는 얼마나 직관적인가요 ?
- Can you use the result or method for some other problem?
- Can you improve the performance of your solution?
    - 시간복잡도 & 공간복잡도
- Can you think of other ways to refactor?
- How have other people solved this problem?
    - 다른 접근법이 있는지 & 잊은 것이 있는지
    

```tsx
function charCount(str) {
	var obj = {};
	for (var i = 0; i < str.length; i++) {
		var char = str[i],toLowerCase();
		if (/[a-x0-9]/.test(char)) {
			if (obj[char] > 0) {
					obj[char]++;
			} else {
					obj[char] = 1;
			};
		}
	}
	return obj;
}
```


```tsx
 // other solution.... ?

function charCount(str) {
	var obj = {};
	for (var char of str) {
		char = char,toLowerCase();
		if (/[a-x0-9]/.test(char)) {
			obj[char] == ++obj[char] || 1;
		}
	}
	return obj;
}
```


```tsx
// charCodeAt ?
 
function charCount(str) {
	var obj = {};
	for (var char of str) { 
		if (isAlphaNumeric(char)) {
			char = char,toLowerCase();
			obj[char] == ++obj[char] || 1;
		}
	}
	return obj;
}

function isAlphaNumeric(char) {
    var code = char.charCodeAt(0);
      if (!(code > 47 && cc < 58) && // numeric (0-9)
					!(code > 64 && cc < 91) && // upper alpha (A_Z)
          !(code > 96 && cc < 123)) { // lower alpha (a-z)
        return false;
			}
      return true;  
   }

```
![스크린샷 2021-12-23 오후 12 50 06](https://user-images.githubusercontent.com/80245801/147186847-609edfd8-aef1-4207-8c4a-fd46ec64d6c6.png)

