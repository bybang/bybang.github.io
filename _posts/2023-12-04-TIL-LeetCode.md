---
layout: single
title: "[LeetCode] TIL LeetCode: 283, 905"

categories: Coding_test
tag: [coding_test, LeetCode, TIL]

permalink: /coding_test/23-12-04-TIL-LeetCode

toc: true
published: true
---

# 283. Move Zeroes

## Problem type - Array(in-place)

## 🧩 Problem

![](https://velog.velcdn.com/images/devbang/post/f564bcdd-1044-4707-a8ee-b5fa7592357d/image.png)

## 🎯 Strategy

### The problem concept

There is not much complicated logic here, we will solve the same problem in two different ways to get used to in-place problems.

## Regular approach

### two-pointer approach

How can we track the current item in the array while we loop through?

One way that is now somewhat familiar is the two-pointer approach. We will set `k` to track the current item.

```python
def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        k = 0

        for i in range(len(nums)):
        	...
```

Then, loop through the array until `i` reaches the end. The conditional is important here, where we will switch `0` with non-zero numbers.

```python
def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        k = 0

        for i in range(len(nums)):
        	if nums[i] != 0:
            	nums[k], nums[i] = nums[i], nums[k]
                ...
```

Then, the logic `nums[k], nums[i] = nums[i], nums[k]` part is that we switch the current tracking number `nums[k]` with `nums[i]` and `nums[i]` with `nums[k]`.

Basically, what we are doing is that we swap two numbers in the array simultaneously.

Finally, we will increase the current tracking number by one to check the next number.

```python
def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        k = 0

        for i in range(len(nums)):
        	if nums[i] != 0:
            	nums[k], nums[i] = nums[i], nums[k]
                k += 1
```

The time complexity is `O(n)` because the function iterates through the array only once.

The space complexity is `O(1)`, as the code uses a constant amount of extra space regardless of the input size. The variable `k` is an integer, and the function uses no additional data structure.

## While loop approach

### Make remaining items into zeros

This time, we will iterate through the array and change the numbers first.

```python
def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        k = 0

        for num in nums:
        	if num != 0:
            	nums[k] = num
                k += 1
```

Notice we don't swap the numbers here, and loop through to check if `num` is zero.

If `num` is not zero, we will assign `num` to `nums[k]`.

Then, the array will look like this:

![](https://velog.velcdn.com/images/devbang/post/1e69703e-4932-409a-a561-f531f594bb16/image.png)

Notice that `k` became `3` when the iteration was over, and `num == 12` means the for loop checked the `num` until the end.

Now, we are going to use the `k` again to assign `0` to it since that's the desired output.

We will use the while loop to increase `k` until it reaches the end of the array. When the loop triggers, change the `nums[k]` to zero and increase `k` by one.

```python
def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        k = 0

        for num in nums:
        	if num != 0:
            	nums[k] = num
                k += 1

        while k < len(nums):
        	nums[k] = 0
            k += 1
```

The time complexity is `O(n)` because the for loop iterates the array once, and the while-loop is the independent loop; hence, at worst, it becomes `O(2n)`, and the dominant factor is `O(n)`.

The space complexity is `O(1)` as the code uses constant extra space regardless of the input size.

## 📌 Thoughts

The problem was quite simple, although I struggled to find the answer because, in my first attempt, the conditional was `if nums[i] != nums[k]:` and I chose a different fork in the road.

The second approach was refreshing, and I learned a new technique.

## 💻 Solution

### Two-pointer approach

```python
def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        k = 0

        for i in range(len(nums)):
        	if nums[i] != 0:
            	nums[k], nums[i] = nums[i], nums[k]
                k += 1
```

### Make remaining items into zeros approach

```python
def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        k = 0

        for num in nums:
        	if num != 0:
            	nums[k] = num
                k += 1

        while k < len(nums):
        	nums[k] = 0
            k += 1
```

# 905. Sort Array By Parity

## Problem type - Array(in-place)

## 🧩 Problem

![](https://velog.velcdn.com/images/devbang/post/5a17495c-8c5e-45c9-a870-e33bd996d33e/image.png)

## 🎯 Strategy

### The problem concept

The concept is pretty much the same as the previous problem, and let's practice two different approaches.

## Two-pointer approach

### for loop approach

The basic two-pointer approach starts with setting up the one-pointer.

```python
def sortArrayByParity(self, nums: List[int]) -> List[int]:
        k = 0
```

Then, loop through the array until `i` reaches the end. The conditional is checking if the current number is an even integer.

```python
def sortArrayByParity(self, nums: List[int]) -> List[int]:
        k = 0

        for i in range(len(nums)):
        	if nums[i] % 2 == 0:
            	...
```

Then, we use the swap logic `nums[k], nums[i] = nums[i], nums[k]` again and return the `nums` array.

```python
def sortArrayByParity(self, nums: List[int]) -> List[int]:
        k = 0

        for i in range(len(nums)):
        	if nums[i] % 2 == 0:
            	nums[k], nums[i] = nums[i], nums[k]
                k += 1

        return nums
```

The time complexity is `O(n)` because the function iterates through the array only once.

The space complexity is `O(1)`, as the code uses a constant amount of extra space regardless of the input size. The variable `k` is an integer, and the function uses no additional data structure.

## While loop approach

### Two-pointer while loop

The approach uses a while loop, two-pointer and swap logic.

First, set one pointer to the start point and one to the endpoint.

```python
def sortArrayByParity(self, nums: List[int]) -> List[int]:
        s, e = 0, len(nums) - 1
```

Next, we will check the first and last elements, while the point `s` is smaller than point `e`.

Start with the current number. If the `nums[s]` is an even number, we will increase `s` by one. At the same time, we check the last element to see if the first element is not an even number, and if the last element is an odd number.

```python
def sortArrayByParity(self, nums: List[int]) -> List[int]:
        s, e = 0, len(nums) - 1

        while s < e:
        	if nums[s] % 2 == 0:
            	s += 1
            elif nums[e] % 2 == 1:
            	e -= 1
            ...
```

Lastly, set the condition for `else` if both conditions fall through. The picture below will help us understand what we are doing in this step.

![](https://velog.velcdn.com/images/devbang/post/1922d0c6-e0b7-4bf6-b4a9-6930f23fdbd1/image.png)

The `nums` array was `[3,1,2,4]`, and we swapped the first and last number because the first item, `3`, is odd and the last item, `4`, is even.

After the iteration, we will return the `nums` array.

```python
def sortArrayByParity(self, nums: List[int]) -> List[int]:
        s, e = 0, len(nums) - 1

        while s < e:
        	if nums[s] % 2 == 0:
            	s += 1
            elif nums[e] % 2 == 1:
            	e -= 1
            else:
            	nums[s], nums[e] = nums[e], nums[s]
                s += 1
                e -= 1

        return nums
```

The time complexity is `O(n)` because the function uses a two-pointer approach to iterate through the array. In each iteration, the pointers `s` and `e` moves towards each other.

The space complexity is `O(1)` as the code uses a constant amount of extra space regardless of the input size.

## 📌 Thoughts

The last two pointers are something that I should get familiar with. Through these two problems, I learned how to swap the elements with an in-place approach.

## 💻 Solution

### Two-pointer for loop approach

```python
def sortArrayByParity(self, nums: List[int]) -> List[int]:
        k = 0

        for i in range(len(nums)):
        	if nums[i] % 2 == 0:
            	nums[k], nums[i] = nums[i], nums[k]
                k += 1

        return nums
```

### Two-pointer while loop approach

```python
def sortArrayByParity(self, nums: List[int]) -> List[int]:
        s, e = 0, len(nums) - 1

        while s < e:
        	if nums[s] % 2 == 0:
            	s += 1
            elif nums[e] % 2 == 1:
            	e -= 1
            else:
            	nums[s], nums[e] = nums[e], nums[s]
                s += 1
                e -= 1

        return nums
```
