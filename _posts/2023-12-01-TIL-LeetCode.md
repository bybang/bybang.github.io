---
layout: single
title: "[LeetCode] TIL LeetCode: 1299, 26(review)"

categories: Coding_test
tag: [coding_test, LeetCode, TIL]

permalink: /coding_test/23-12-01-TIL-LeetCode

toc: true
published: true
---

# 1299. Replace Elements with Greatest Element on Right Side

## Problem type - Array(in-place)

# 🧩 Problem

![](https://velog.velcdn.com/images/devbang/post/2a603d24-dade-4c7f-b143-2265d030e51a/image.png)

# 🎯 Strategy

### Understand the concept

We aim to bring the maximum of the next numbers in the array except the current number.

We might think that we need to slice the array, but this is an in-place problem, so we must think differently.

In fact, we can simply solve this problem by reversing the current array.

## Regular approach

### two-pointer approach

How can we reverse or check the array from the last element?

Let's set the pointer `k` and `i` like the normal index. But this time, we set the `k` to negative because we want to check backwards and the `i` to the last element of the array.

```python
def replaceElements(self, arr: List[int]) -> List[int]:
	k = -1
    i = len(arr) - 1
```

Then loop through the array until `i` reaches the `0`, the first element of the array. We will set the temporary variable `tmp` to store the current element.

The next thing we need to do is each time we loop through. We will change the current element to `k`. The current element is stored in `tmp`, so we still have that value.

```python
def replaceElements(self, arr: List[int]) -> List[int]:
	k = -1
    i = len(arr) - 1

    while i >= 0:
    	tmp = arr[i]
        arr[i] = k
```

Compare the current value stored in `tmp` with `k`. If `tmp` is bigger than `k`, we will change the `k` value to the current value `k`.

![](https://velog.velcdn.com/images/devbang/post/4571a7be-5f0b-4d43-9ed5-fd9b8e81f730/image.jpeg)

```python
def replaceElements(self, arr: List[int]) -> List[int]:
	k = -1
    i = len(arr) - 1

    while i >= 0:
    	tmp = arr[i]
        arr[i] = k

        if tmp > k:
        	k = tmp
```

Lastly, at the end of each loop, we will decrease the `i` by one to iterate through the array. Once the loop is over, return the modified array.

```python
def replaceElements(self, arr: List[int]) -> List[int]:
	k = -1
    i = len(arr) - 1

    while i >= 0:
    	tmp = arr[i]
        arr[i] = k

        if tmp > k:
        	k = tmp

        i -= 1

    return arr
```

The time complexity is `O(n)` because the function iterates through the array only once.

The space complexity is `O(1)`, as the code uses a constant amount of extra space regardless of the input size. The variables `k`, `i`, and `tmp` are all integers, and the function uses no additional data structure.

## Pythonic approach

### reversed() approach

In Python, there is a more clever way to loop through the array from the last element.

The built-in function `reversed()` returns the reverse array, so we can use it to loop through like this:

```python
def replaceElements(self, arr: List[int]) -> List[int]:
	k = -1

    for i in reversed(range(len(arr))):
    	...
```

Notice we set the pointer `k` to a negative one and loop through the array from the last element.

Then, we set the current value `arr[i]` to `k`. After we assign the current value, we need to change `k`.

We should check if the `k` value is bigger than the current value, so we will compare those two.

The important thing is we have to do the above step simultaneously, in the same line.

```python
def replaceElements(self, arr: List[int]) -> List[int]:
	k = -1

    for i in reversed(range(len(arr))):
    	arr[i], k = k, max(k, arr[i])

    return arr
```

The time complexity is `O(n)` because the for loop iterates the array only once, and the `max()` has the constant time operation since it only compares two values.

The space complexity is `O(1)` as the code uses a constant amount of extra space regardless of the input size.

# 📌 Thoughts

This problem was quite hard at the beginning, but I was able to solve the problem when I saw the solution.

It was still quite hard after I saw the solution, but I understood it with the drawing. So, I could say the drawing code definitely helps to understand the algorithm.

I also learned the `reversed()` function is a built-in function, and Python users prefer to use it when they need to iterate backward.

# 💻 Solution

### Two-pointer approach

```python
def replaceElements(self, arr: List[int]) -> List[int]:
	k = -1
    i = len(arr) - 1

    while i >= 0:
    	tmp = arr[i]
        arr[i] = k

        if tmp > k:
        	k = tmp

        i -= 1

    return arr
```

### `reversed()` loop approach

```python
def replaceElements(self, arr: List[int]) -> List[int]:
	k = -1

    for i in reversed(range(len(arr))):
    	arr[i], k = k, max(k, arr[i])

    return arr
```

# 🔖 Review

As this part is the in-place array problem part, this question popped up again, so let's briefly review it.

# 🧩 Problem

![](https://velog.velcdn.com/images/devbang/post/a2179445-8e48-4a1f-926d-c7e20d22ed4a/image.png)

![](https://velog.velcdn.com/images/devbang/post/18988631-41ce-407a-a452-2e291fe08374/image.png)

# 💻 Solution

### Two-pointer approach

```python
def removeDuplicates(self, nums: List[int]) -> int:
	k = 0

    for i in range(len(nums)):
    	if nums[i] > nums[k]:
        	k += 1
        	nums[k] = nums[i]

    return k + 1
```

Notice that we return `k+1` because the assertion checks the range of `i < k` to check the expected array.

### Another loop approach

```python
def removeDuplicates(self, nums: List[int]) -> int:
	k = 0

    for num in nums:
    	if num != nums[k]:
        	nums[k+1] = num
            k += 1

    return k + 1
```

# 📌 Thoughts

Both solutions above have the time complexity of `O(n)` and the space complexity of `O(1)`.

I just learned to calculate the time complexity by importing `time` and using `time.time()`.

Reviewing the problems from the past might waste time, but it took me a little time to remember the old approach.

Hence, I think reviewing is helpful when studying algorithms and should review the solved problems from time to time.
