---
layout: single
title: "[LeetCode] TIL LeetCode: 414"

categories: Coding_test
tag: [coding_test, LeetCode, TIL]

permalink: /coding_test/23-12-19-TIL-LeetCode

toc: true
published: true
---

# 414. Third Maximum Number

## Problem type - Array

# 🧩 Problem

![](https://velog.velcdn.com/images/devbang/post/6016cb84-96bc-434f-b3ad-7d71d4fff77d/image.png)

# 🎯 Strategy

### Understand the concept

In this problem, we are going to compare the array's value and find the third biggest number.

As we did with other problems, we will approach this in two different ways to achieve the same goal.

## Regular approach

### `max()` approach

Let's approach this by setting and comparing each number as we loop through the array.

We will set the first array item as the first maximum and two other variables to `-inf`. By doing so, we can satisfy the constraints`(-2^31 <= n <= 2^31 - 1)`.

```python
def thirdMax(self, nums: List[int]) -> int:
        max1 = nums[0]
        max2 = float('-inf')
        max3 = float('-inf')

        ...
```

Then, set the edge case checker that checks if the array length is less than three. If the array length is three or longer, we iterate through the array. If the array length is less than three, we return the max number of the array.

```python
def thirdMax(self, nums: List[int]) -> int:
        max1 = nums[0]
        max2 = float('-inf')
        max3 = float('-inf')

        if len(nums) < 3:
        	return max(nums)

        for i in range(len(nums)):
        	...
```

Inside the loop, we set the temporary variable `num` to track the current `nums[i]` value. If the current value `num` is bigger than `max1`, we set `max3 = max2`, `max2 = max1`, and `max1 = num`. What happens here is the new biggest number pushes other values.

If the number satisfies the `max2 < num < max1` condition, we have to set `max3 = max2`, `max2 = num`.

Otherwise, if the `num` is between `num2` and `num3`, we set the `num` to `num3`.

```python
def thirdMax(self, nums: List[int]) -> int:
        ...

        for i in range(len(nums)):
        	num = nums[i]

            if num > max1:
            	max3 = max2
                max2 = max1
                max1 = num

            elif num > max2 and num < max1:
            	max3 = max2
                max2 = num

            elif num > num3 and num < num2:
            	max3 = num

            ...
```

Lastly, return the `max3`, if the `max3` is not the initial value `-inf`. In the case of `max3 == -inf`, we will return `max1`.

```python
def thirdMax(self, nums: List[int]) -> int:
        ...

        for i in range(len(nums)):
        	num = nums[i]

            if num > max1:
            	max3 = max2
                max2 = max1
                max1 = num

            elif num > max2 and num < max1:
            	max3 = max2
                max2 = num

            elif num > num3 and num < num2:
            	max3 = num

       	return max3 if max3 != float('-inf') else max1
```

The time complexity is `O(n)` because the function iterates through the array only once with a single loop.

The space complexity is `O(1)`, as the code uses a constant amount of extra space regardless of the input size. The variables `max1`, `max2`, and `max3` are integers, and the function doesn't use any additional data structure.

## Pythonic approach

### `set()` approach

In Python, we have a `set` function to deduct duplicated values.

Similar to the previous solution, we will set the space for the `-inf` value and make a variable for a new list with a `set()` function.

```python
def thirdMax(self, nums: List[int]) -> int:
        n = list(set(nums))
        T = [float('-inf')] * 3

        ...
```

Then, we will loop through the new array `n`, to compare three values.

This time, we will compare the value from the back. No matter how long the array is, the `T[2]` is always the right-most number, which is the largest number.

```python
def thirdMax(self, nums: List[int]) -> int:
        n = list(set(nums))
        T = [float('-inf')] * 3

        for i in n:
        	if i > T[2]:
            	T = [T[1], T[2], i]

            ...
```

Then, we check if `i` is greater than `T[1]`. If `i` is bigger than `T[1]`, The list order will change.

If the `i` is greater than `T[0]`, we set the `i`'s position at the first place of the array.

Lastly, we return `T[0]` if it is not `-inf`, where the `-inf` is the initial value. If `T[0]` is `-inf`, it means the array length is less than three. Otherwise, we will return `T[0]`, which is the third max.

```python
def thirdMax(self, nums: List[int]) -> int:
        n = list(set(nums))
        T = [float('-inf')] * 3

        for i in n:
        	if i > T[2]:
            	T = [T[1], T[2], i]

            elif i > T[1]:
            	T = [T[1], i, T[2]]

            elif i > T[0]:
            	T = [i, T[1], T[2]]

        return T[0] if T[0] != float('-inf') else T[2]
```

The time complexity is `O(n)` because the `n = list(set(nums))` part has a time complexity of `O(n)` in the worst case. Therefore, the overall time complexity is linear with respect to the size of the input array.

The space complexity is `O(n)` where the `n` is the length of the input array `nums`. The `set()` operation creates a new list with distinct elements. In the worst case, where all elements are distinct, the space complexity is `O(n)`. The additional space used by the list `T` is constant and doesn't depend on the input size.

# 📌 Thoughts

I couldn't solve this problem due to the `float('-inf')`. The concept of `float('-inf')` was new to me, and I applied the swap technique I learned previously, but it didn't work well.

Learning new concepts is always good; after two more questions, the first chapter will be done. I will finish the first chapter in the next post and move forward.

# 💻 Solution

### `max()` approach

```python
def thirdMax(self, nums: List[int]) -> int:
        max1 = nums[0]
        max2 = float('-inf')
        max3 = float('-inf')

        if len(nums) < 3:
        	return max(nums)

        for i in nums:
        	num = nums[i]

            if num > max1:
            	max3 = max2
                max2 = max1
                max1 = num

            elif num > max2 and num < max1:
            	max3 = max2
            	max2 = num

            elif num > max3 and num < max2:
            	max3 = num

        return max3 if max3 != float('-inf') else max1
```

### `set()` approach

```python
def thirdMax(self, nums: List[int]) -> int:
        n = list(set(nums))
        T = [float('-inf')] * 3

        for i in n:
        	if i > T[2]:
            	T = [T[1], T[2], i]

            elif i > T[1]:
            	T = [T[1], i, T[2]]

            elif i > T[0]:
            	T = [i, T[1], T[2]]

        return T[0] if T[0] != float('-inf') else T[2]
```
