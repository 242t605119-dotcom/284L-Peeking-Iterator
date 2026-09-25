# LeetCode 284 - Peeking Iterator

## Problem Statement

Given an Iterator class, design a PeekingIterator that supports the following operations:

* `peek()` - Returns the next element without moving the iterator.
* `next()` - Returns the next element and moves the iterator forward.
* `hasNext()` - Returns `True` if there are still elements remaining.

The iterator should allow us to see the next element without actually consuming it.

---

## Example

```text
Input:
[1, 2, 3]

Operations:
peek()
next()
peek()
next()
hasNext()

Output:
1
1
2
2
True
```

### Explanation

Initially:

```text
[1, 2, 3]
 ^
```

Calling `peek()` returns `1`, but the iterator does not move.

Calling `next()` returns `1` and moves to `2`.

Calling `peek()` now returns `2` without moving.

---

## Approach

We maintain one extra variable called `next_value`.

This variable stores the next element that should be returned.

When the `PeekingIterator` is created:

1. Get the first element from the original iterator.
2. Store it in `next_value`.

### `peek()`

Simply return `next_value`.

The iterator does not move.

### `next()`

1. Store the current `next_value`.
2. Move the original iterator forward.
3. Store the new next element in `next_value`.
4. Return the stored value.

### `hasNext()`

Check whether `next_value` is available.

---

## Algorithm

### Initialization

1. Store the original iterator.
2. If an element exists, store the first element in `next_value`.
3. Otherwise, store `None`.

### Peek

1. Return `next_value`.
2. Do not modify the iterator.

### Next

1. Store the current `next_value`.
2. Get the next element from the original iterator.
3. Update `next_value`.
4. Return the stored element.

### HasNext

Return whether `next_value` contains an element.

---

## Example Walkthrough

Suppose:

```text
[1, 2, 3]
```

Initially:

```text
next_value = 1
```

### Operation: `peek()`

```text
Returns: 1
next_value = 1
```

The iterator does not move.

### Operation: `next()`

```text
Returns: 1
next_value = 2
```

### Operation: `peek()`

```text
Returns: 2
next_value = 2
```

### Operation: `next()`

```text
Returns: 2
next_value = 3
```

### Operation: `hasNext()`

```text
Returns: True
```

---

## Why This Works

The important idea is to keep the next element in a temporary variable.

Normally, calling `next()` consumes an element.

With `next_value`, we already know what the next element is, so `peek()` can return it without consuming it.

---

## Time Complexity

Each operation performs a constant amount of work.

**Time Complexity:** `O(1)` per operation.

---

## Space Complexity

We store only one extra element.

**Space Complexity:** `O(1)` auxiliary space.

---

## Key Concept

The main concept used in this problem is **Iterator Design**.

The important technique is maintaining a **look-ahead value** so that the next element can be viewed without advancing the iterator.

---

## Language

Python

## LeetCode Problem

284 - Peeking Iterator

## Author

T. Nandhini
