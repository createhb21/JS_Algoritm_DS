## Frequency Counter - sameFrequency

💡 Write a function called **sameFrequency.** Given two positive integers, find out if the two numbers have the same frequency of digits.

Your solution MUST have the following complexities:

Time: O(N)

Sample Input :

```1. sameFrequency(182,281) // true
2. sameFrequency(34,14) // false
3. sameFrequency(3589578, 5879385) // true
4. sameFrequency(22,222) // false`
```

```tsx
// mine
function sameFrequency(first, second) {
  let one = first.toString();
  let two = second.toString();

  if (one.length != two.length) return false;

  const lookup = {};

  for (let i = 0; i < one.length; i++) {
    let letter = one[i];
    lookup[letter] ? (lookup[letter] += 1) : (lookup[letter] = 1);
  }

  for (let i = 0; i < two.length; i++) {
    let letter = two[i];
    if (!lookup[letter]) {
      return false;
    } else {
      lookup[letter] -= 1;
    }
  }
  return true;
}
```

```tsx
// professor
function sameFrequency(num1, num2){
  let strNum1 = num1.toString();
  let strNum2 = num2.toString();
  if(strNum1.length !== strNum2.length) return false;
  
  let countNum1 = {};
  let countNum2 = {};
  
  for(let i = 0; i < strNum1.length; i++){
    countNum1[strNum1[i]] = (countNum1[strNum1[i]] || 0) + 1
  }
  
  for(let j = 0; j < strNum1.length; j++){
    countNum2[strNum2[j]] = (countNum2[strNum2[j]] || 0) + 1
  }
  
  for(let key in countNum1){
    if(countNum1[key] !== countNum2[key]) return false;
  }
 
  return true;
}
```

---

# **Frequency Counter / Multiple Pointers - areThereDuplicates**

💡 Implement a function called, **areThereDuplicates** which accepts a **variable number of arguments,** and **checks whether there are any duplicates among the arguments passed in.  You can solve this using the frequency counter pattern OR the multiple pointers pattern.

Examples:  

```1. areThereDuplicates(1, 2, 3) // false
2. areThereDuplicates(1, 2, 2) // true 
3. areThereDuplicates('a', 'b', 'c', 'a') // true
```

**Restrictions:**

Time - O(n)

Space - O(n)

**Bonus:**

Time - O(n log n)

Space - O(1)


```tsx
// mine
function areThereDuplicates(...params) {
  return new Set(params).size !== params.length;
}
```

```tsx
// professor
// 1.
function areThereDuplicates() {
  let collection = {}
  for(let val in arguments){
    collection[arguments[val]] = (collection[arguments[val]] || 0) + 1
  }
  for(let key in collection){
    if(collection[key] > 1) return true
  }
  return false;
}

// 2.
function areThereDuplicates(...args) {
  // Two pointers
  args.sort((a,b) => a > b);
  let start = 0;
  let next = 1;
  while(next < args.length){
    if(args[start] === args[next]){
        return true
    }
    start++
    next++
  }
  return false
}

// 3.
function areThereDuplicates() {
  return new Set(arguments).size !== arguments.length;
}
```

---

# **Multiple Pointers - averagePair**

💡 Write a function called **averagePair.** Given a sorted array of integers and a target average, determine if there is a pair of values in the array where the average of the pair equals the target average. There may be more than one pair that matches the average target.

**Bonus Constraints:**

Time: O(N)

Space: O(1)

Sample Input: 

```
1. averagePair([1,2,3],2.5) // true
2. averagePair([1,3,3,5,6,7,10,12,19],8) // true
3. averagePair([-1,0,3,4,5,6], 4.1) // false
4. averagePair([],4) // false`
```

```tsx
function averagePair(arr, num){
  let start = 0
  let end = arr.length-1;
  while(start < end){
    let avg = (arr[start]+arr[end]) / 2 
    if(avg === num) return true;
    else if(avg < num) start++
    else end--
  }
  return false;
}
```

---

## Multiple Pointers - isSubsequence

💡 Write a function called **isSubsequence** which takes in two strings and checks whether the characters in the first string form a subsequence of the characters in the second string. In other words, the function should check whether the characters in the first string appear somewhere in the second string, **without their order changing.**

Examples :

```
1. isSubsequence('hello', 'hello world'); // true
2. isSubsequence('sing', 'sting'); // true
3. isSubsequence('abc', 'abracadabra'); // true
4. isSubsequence('abc', 'acb'); // false (order matters)
```

Your solution MUST have AT LEAST the following complexities:

Time Complexity - O(N + M)

Space Complexity - O(1)

```tsx
// 1.
function isSubsequence(str1, str2) {
  let i = 0;
  let j = 0;
  if (!str1) return true;
  while (j < str2.length) {
    if (str2[j] === str1[i]) i++;
    if (i === str1.length) return true;
    j++;
  }
  return false;
}

// 2.
function isSubsequence(str1, str2) {
  if(str1.length === 0) return true
  if(str2.length === 0) return false
  if(str2[0] === str1[0]) return isSubsequence(str1.slice(1), str2.slice(1))  
  return isSubsequence(str1, str2.slice(1))
}
```

---

## Sliding Window - maxSubarraySum

💡 Given an array of integers and a number, write a function called **maxSubarraySum**, which finds the maximum sum of a subarray with the length of the number passed to the function.

Note that a subarray must consist of *consecutive* elements from the original array. In the first example below, [100, 200, 300] is a subarray of the original array, but [100, 300] is not.

```
1. maxSubarraySum([100,200,300,400], 2) // 700
2. maxSubarraySum([1,4,2,10,23,3,1,0,20], 4)  // 39 
3. maxSubarraySum([-3,4,0,-2,6,-1], 2) // 5
4. maxSubarraySum([3,-2,7,-4,1,-1,4,-2,1],2) // 5
5. maxSubarraySum([2,3], 3) // null
```

Constraints:

Time Complexity - **O(N)**

Space Complexity - **O(1)**


```tsx
function maxSubarraySum(arr, num){
  let maxSum = 0;
  let tempSum = 0;
  if (arr.length < num) return null;
  for(let i = 0 ; i < num; i++) {
      maxSum += arr[i]
  }
  tempSum = maxSum;
  for (let i = num; i < arr.length; i++) {
      tempSum = tempSum - arr[i - num] + arr[i];
      maxSum = Math.max(maxSum, tempSum);
  }
  return maxSum;
}
```

---

## Sliding Window - minSubArrayLen

💡 Write a function called **minSubArrayLen** which accepts two parameters - an array of positive integers and a positive integer.

This function should return the minimal length of a **contiguous** subarray of which the sum is greater than or equal to the integer passed to the function. If there isn't one, return 0 instead.Examples:

```
1. minSubArrayLen([2,3,1,2,4,3], 7) // 2 -> because [4,3] is the smallest subarray
2. minSubArrayLen([2,1,6,5,4], 9) // 2 -> because [5,4] is the smallest subarray
3. minSubArrayLen([3,1,7,11,2,9,8,21,62,33,19], 52) // 1 -> because [62] is greater than 52
4. minSubArrayLen([1,4,16,22,5,7,8,9,10],39) // 3
5. minSubArrayLen([1,4,16,22,5,7,8,9,10],55) // 5
6. minSubArrayLen([4, 3, 3, 8, 1, 2, 3], 11) // 2
7. minSubArrayLen([1,4,16,22,5,7,8,9,10],95) // 0
```
Time Complexity - O(n)

Space Complexity - O(1)


```tsx
function minSubArrayLen(nums, sum) {
  let total = 0;
  let start = 0;
  let end = 0;
  let minLen = Infinity;
 
  while (start < nums.length) {
    // if current window doesn't add up to the given sum then 
		// move the window to right
    if(total < sum && end < nums.length){
      total += nums[end];
			end++;
    }
    // if current window adds up to at least the sum given then
		// we can shrink the window 
    else if(total >= sum){
      minLen = Math.min(minLen, end-start);
			total -= nums[start];
			start++;
    } 
    // current total less than required total but we reach the end, need this or else we'll be in an infinite loop 
    else {
      break;
    }
  }
 
  return minLen === Infinity ? 0 : minLen;
}
```

---

## Sliding Window = findLongestSubstring

💡 Write a function called **findLongestSubstring,** which accepts a string and returns the length of the longest substring with all distinct characters.

```
1. findLongestSubstring('') // 0
2. findLongestSubstring('rithmschool') // 7
3. findLongestSubstring('thisisawesome') // 6
4. findLongestSubstring('thecatinthehat') // 7
5. findLongestSubstring('bbbbbb') // 1
6. findLongestSubstring('longestsubstring') // 8
7. findLongestSubstring('thisishowwedoit') // 6
```

Time Complexity - **O(n)**


```tsx
function findLongestSubstring(str) {
  let longest = 0;
  let seen = {};
  let start = 0;
 
  for (let i = 0; i < str.length; i++) {
    let char = str[i];
    if (seen[char]) {
      start = Math.max(start, seen[char]);
    }
    // index - beginning of substring + 1 (to include current in count)
    longest = Math.max(longest, i - start + 1);
    // store the index of the next char so as to not double count
    seen[char] = i + 1;
  }
  return longest;
}
```

---
