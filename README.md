# PCCE Python 핵심 문법 & 메서드 정리

> PCCE 및 프로그래머스 코딩테스트 입문 문제를 풀 때 자주 사용하는 파이썬 문법과 메서드 정리

---

# 1. `len()` — 길이 구하기

문자열이나 리스트의 길이를 구한다.

```python
arr = [10, 20, 30]
print(len(arr))
# 3

s = "hello"
print(len(s))
# 5
```

자주 사용하는 형태:

```python
for i in range(len(arr)):
    print(arr[i])
```

---

# 2. `range()` — 반복 범위 만들기

```python
range(끝)
range(시작, 끝)
range(시작, 끝, 간격)
```

## 기본

```python
for i in range(5):
    print(i)
```

결과:

```text
0
1
2
3
4
```

## 시작값 지정

```python
range(1, 6)
```

```text
1, 2, 3, 4, 5
```

## 간격 지정

```python
range(2, 11, 2)
```

```text
2, 4, 6, 8, 10
```

## 역순

```python
range(10, 0, -1)
```

```text
10, 9, 8, ..., 1
```

### 핵심

```python
range(1, 5)
```

에서 `5`는 포함하지 않는다.

---

# 3. 슬라이싱

기본 형태:

```python
데이터[시작:끝:간격]
```

> 시작 인덱스는 포함
> 끝 인덱스는 포함하지 않음

```python
arr = [1, 2, 3, 4, 5]
```

## 특정 범위

```python
arr[1:4]
# [2, 3, 4]
```

## 처음부터

```python
arr[:3]
# [1, 2, 3]
```

## 특정 위치부터 끝까지

```python
arr[2:]
# [3, 4, 5]
```

## 마지막 값

```python
arr[-1]
# 5
```

## 뒤에서 3개

```python
arr[-3:]
# [3, 4, 5]
```

## 마지막 2개 제외

```python
arr[:-2]
# [1, 2, 3]
```

## 2칸씩

```python
arr[::2]
# [1, 3, 5]
```

## 뒤집기

```python
arr[::-1]
# [5, 4, 3, 2, 1]
```

문자열에도 동일하게 사용 가능하다.

```python
s = "hello"

print(s[::-1])
# olleh
```

### 특정 인덱스부터 특정 인덱스까지 포함

```python
numbers[num1:num2 + 1]
```

예:

```python
numbers = [1, 2, 3, 4, 5]

print(numbers[1:4])
# [2, 3, 4]
```

---

# 4. `append()` — 리스트에 값 추가

```python
arr = []

arr.append(10)
arr.append(20)

print(arr)
# [10, 20]
```

코딩테스트에서 자주 사용하는 패턴:

```python
answer = []

for i in numbers:
    if i % 2 == 0:
        answer.append(i)
```

조건을 만족하는 값만 새로운 리스트에 저장한다.

---

# 5. `replace()` — 문자열 변경 / 제거

```python
s = "banana"

print(s.replace("a", ""))
# bnn
```

특정 문자 제거:

```python
s.replace("a", "")
```

`""`는 빈 문자열이므로 해당 문자가 제거된다.

## 주의

문자열은 직접 수정되지 않는다.

잘못된 코드:

```python
answer.replace("a", "")
```

올바른 코드:

```python
answer = answer.replace("a", "")
```

예: 모음 제거

```python
def solution(my_string):
    answer = my_string

    for ch in "aeiou":
        answer = answer.replace(ch, "")

    return answer
```

---

# 6. `upper()` / `lower()` — 대소문자 변환

## 대문자로 변환

```python
"a".upper()
# "A"
```

```python
"hello".upper()
# "HELLO"
```

## 소문자로 변환

```python
"A".lower()
# "a"
```

```python
"HELLO".lower()
# "hello"
```

---

# 7. `isupper()` / `islower()` — 대소문자 검사

```python
"A".isupper()
# True
```

```python
"a".islower()
# True
```

대소문자 서로 바꾸기:

```python
answer = ""

for ch in my_string:
    if ch.isupper():
        answer += ch.lower()
    else:
        answer += ch.upper()
```

---

# 8. `swapcase()` — 대소문자 한 번에 바꾸기

```python
"AbCd".swapcase()
# "aBcD"
```

```python
def solution(my_string):
    return my_string.swapcase()
```

---

# 9. `isdigit()` — 숫자인지 검사

```python
"1".isdigit()
# True
```

```python
"a".isdigit()
# False
```

문자열에서 숫자만 추출:

```python
answer = []

for ch in my_string:
    if ch.isdigit():
        answer.append(int(ch))
```

---

# 10. `isalpha()` — 문자인지 검사

```python
"a".isalpha()
# True
```

```python
"3".isalpha()
# False
```

문자만 추출:

```python
answer = ""

for ch in my_string:
    if ch.isalpha():
        answer += ch
```

---

# 11. `isalnum()` — 문자 또는 숫자인지 검사

```python
"abc123".isalnum()
# True
```

```python
"abc!".isalnum()
# False
```

---

# 12. `sort()` — 리스트 자체 정렬

```python
arr = [3, 1, 5, 2]

arr.sort()

print(arr)
# [1, 2, 3, 5]
```

내림차순:

```python
arr.sort(reverse=True)
```

결과:

```python
[5, 3, 2, 1]
```

---

# 13. `sorted()` — 정렬된 새 리스트 반환

```python
arr = [3, 1, 2]

answer = sorted(arr)

print(answer)
# [1, 2, 3]
```

## `sort()`와 차이

```python
arr.sort()
```

→ 원본 리스트 자체 변경

```python
sorted(arr)
```

→ 정렬된 새로운 리스트 반환

---

# 14. `sum()` — 합계

```python
arr = [1, 2, 3, 4]

print(sum(arr))
# 10
```

평균:

```python
average = sum(arr) / len(arr)
```

---

# 15. `max()` / `min()`

```python
arr = [3, 8, 1, 5]

print(max(arr))
# 8

print(min(arr))
# 1
```

---

# 16. `count()` — 개수 세기

리스트:

```python
arr = [1, 2, 1, 3, 1]

print(arr.count(1))
# 3
```

문자열:

```python
print("banana".count("a"))
# 3
```

---

# 17. `in` / `not in` — 포함 여부 확인

```python
"a" in "apple"
# True
```

```python
3 in [1, 2, 3]
# True
```

## 모음 검사

```python
if ch in "aeiou":
    print("모음")
```

## 모음이 아닌 문자만 저장

```python
answer = ""

for ch in my_string:
    if ch not in "aeiou":
        answer += ch
```

---

# 18. `%` — 나머지

## 짝수

```python
n % 2 == 0
```

## 홀수

```python
n % 2 == 1
```

## 나누어떨어지는지 확인

```python
n % i == 0
```

예: 약수 개수 구하기

```python
answer = 0

for i in range(1, n + 1):
    if n % i == 0:
        answer += 1
```

---

# 19. `//` — 몫

```python
10 // 3
# 3
```

```python
10 % 3
# 1
```

정리:

```text
/   → 일반 나눗셈
//  → 몫
%   → 나머지
```

---

# 20. `split()` — 문자열 나누기

```python
s = "apple banana orange"

print(s.split())
```

결과:

```python
["apple", "banana", "orange"]
```

특정 문자 기준:

```python
s = "2026-09-07"

print(s.split("-"))
# ["2026", "09", "07"]
```

---

# 21. `join()` — 문자열 합치기

```python
arr = ["a", "b", "c"]

print("".join(arr))
# abc
```

공백을 넣어서:

```python
print(" ".join(arr))
# a b c
```

문자열을 리스트에 모은 후 한 번에 합칠 때 유용하다.

```python
answer = []

for ch in my_string:
    if ch.isalpha():
        answer.append(ch)

return "".join(answer)
```

---

# 22. 형변환

## `int()`

문자열 → 정수

```python
int("123")
# 123
```

## `str()`

숫자 → 문자열

```python
str(123)
# "123"
```

## `list()`

문자열 → 리스트

```python
list("abc")
# ['a', 'b', 'c']
```

---

# 23. `map()`

여러 값을 한 번에 형변환할 때 사용한다.

```python
a, b = map(int, input().split())
```

입력:

```text
10 20
```

결과:

```python
a = 10
b = 20
```

리스트로 받기:

```python
arr = list(map(int, input().split()))
```

---

# 24. 문자열 반복 `*`

문자열 전체 반복:

```python
"abc" * 3
# "abcabcabc"
```

문자 하나씩 반복:

```python
answer = ""

for ch in "apl":
    answer += ch * 3

print(answer)
# aaappplll
```

---

# 25. `reverse()` / `[::-1]`

리스트 자체를 뒤집기:

```python
arr.reverse()
```

슬라이싱으로 뒤집기:

```python
arr[::-1]
```

문자열:

```python
"hello"[::-1]
# "olleh"
```

---

# 26. `set()` — 중복 제거

```python
arr = [1, 1, 2, 2, 3]

print(set(arr))
# {1, 2, 3}
```

중복을 제거한 값의 개수:

```python
len(set(arr))
# 3
```

> `set`은 순서를 유지해야 하는 문제에서는 주의해서 사용한다.

순서를 유지하면서 중복 제거:

```python
answer = ""

for ch in my_string:
    if ch not in answer:
        answer += ch
```

---

# 27. `enumerate()` — 인덱스와 값 동시에 사용

```python
arr = ["a", "b", "c"]

for i, value in enumerate(arr):
    print(i, value)
```

결과:

```text
0 a
1 b
2 c
```

아래 코드와 비슷하다.

```python
for i in range(len(arr)):
    print(i, arr[i])
```

---

# 28. `abs()` — 절댓값

```python
abs(-5)
# 5
```

두 수의 차이:

```python
abs(a - b)
```

거리 또는 차이를 계산하는 문제에서 자주 사용한다.

---

# 29. `math.ceil()` — 올림

```python
import math

math.ceil(1.2)
# 2
```

예: 피자 최소 판 수

```python
import math

def solution(slice, n):
    return math.ceil(n / slice)
```

정수 연산으로도 가능:

```python
def solution(slice, n):
    return (n + slice - 1) // slice
```

## 주의

```python
round()
```

는 올림이 아니다.

```python
round(1.2)
# 1
```

"최소 몇 개 필요한가?" 문제에서는 `round()`를 사용하면 안 되는 경우가 많다.

---

# 30. `math.gcd()` — 최대공약수

```python
import math

math.gcd(12, 8)
# 4
```

분수 약분 등에 사용할 수 있다.

```python
a = 6
b = 8

g = math.gcd(a, b)

a //= g
b //= g

print(a, b)
# 3 4
```

---

# 31. 딕셔너리 `get()`

값의 등장 횟수를 셀 때 유용하다.

```python
arr = [1, 2, 1, 1, 3]

count = {}

for x in arr:
    count[x] = count.get(x, 0) + 1

print(count)
```

결과:

```python
{
    1: 3,
    2: 1,
    3: 1
}
```

```python
count.get(x, 0)
```

의 의미:

* `x`가 존재 → 기존 값 반환
* `x`가 없음 → `0` 반환

---

# 32. `key=lambda` — 기준을 정해서 정렬

```python
data = [
    [1, 30],
    [2, 10],
    [3, 20]
]
```

두 번째 값을 기준으로 정렬:

```python
data.sort(key=lambda x: x[1])
```

결과:

```python
[
    [2, 10],
    [3, 20],
    [1, 30]
]
```

PCCE 후반부 데이터 처리 문제에서 알아두면 유용하다.

---

# PCCE 중요도 정리

| 중요도   | 문법 / 메서드                  | 용도           |
| ----- | ------------------------- | ------------ |
| ⭐⭐⭐⭐⭐ | `range()`                 | 반복           |
| ⭐⭐⭐⭐⭐ | `len()`                   | 길이           |
| ⭐⭐⭐⭐⭐ | 슬라이싱                      | 문자열/리스트 자르기  |
| ⭐⭐⭐⭐⭐ | `%`                       | 나머지, 짝홀수, 약수 |
| ⭐⭐⭐⭐⭐ | `//`                      | 몫            |
| ⭐⭐⭐⭐⭐ | `append()`                | 리스트 추가       |
| ⭐⭐⭐⭐⭐ | `replace()`               | 문자열 변경       |
| ⭐⭐⭐⭐⭐ | `sort()` / `sorted()`     | 정렬           |
| ⭐⭐⭐⭐⭐ | `int()` / `str()`         | 형변환          |
| ⭐⭐⭐⭐  | `sum()`                   | 합            |
| ⭐⭐⭐⭐  | `max()` / `min()`         | 최댓값 / 최솟값    |
| ⭐⭐⭐⭐  | `in` / `not in`           | 포함 여부        |
| ⭐⭐⭐⭐  | `isdigit()`               | 숫자 검사        |
| ⭐⭐⭐⭐  | `isalpha()`               | 문자 검사        |
| ⭐⭐⭐⭐  | `isupper()` / `islower()` | 대소문자 검사      |
| ⭐⭐⭐⭐  | `upper()` / `lower()`     | 대소문자 변환      |
| ⭐⭐⭐⭐  | `split()`                 | 문자열 분리       |
| ⭐⭐⭐⭐  | `join()`                  | 문자열 합치기      |
| ⭐⭐⭐⭐  | `count()`                 | 개수 세기        |
| ⭐⭐⭐   | `set()`                   | 중복 제거        |
| ⭐⭐⭐   | `enumerate()`             | 인덱스 + 값      |
| ⭐⭐⭐   | `abs()`                   | 절댓값          |
| ⭐⭐⭐   | `math.ceil()`             | 올림           |
| ⭐⭐⭐   | `math.gcd()`              | 최대공약수        |
| ⭐⭐⭐   | `dict.get()`              | 빈도 계산        |
| ⭐⭐⭐   | `key=lambda`              | 기준 정렬        |

---

# 자주 틀리는 부분

## 1. `=`와 `==`

```python
angle = 90
```

→ 값을 저장

```python
angle == 90
```

→ 같은지 비교

---

# 2. `else if`가 아니라 `elif`

잘못된 코드:

```python
if angle < 90:
    pass
else if angle == 90:
    pass
```

올바른 코드:

```python
if angle < 90:
    pass
elif angle == 90:
    pass
else:
    pass
```

---

# 3. 연산 우선순위

잘못된 코드:

```python
if i + 1 % 2 == 0:
    pass
```

`%`가 `+`보다 먼저 계산된다.

올바른 코드:

```python
if (i + 1) % 2 == 0:
    pass
```

---

# 4. `range()`의 끝값은 포함하지 않는다

```python
range(1, 5)
```

결과:

```text
1, 2, 3, 4
```

1부터 5까지 원한다면:

```python
range(1, 6)
```

---

# 5. 슬라이싱도 끝값은 포함하지 않는다

```python
arr[1:4]
```

가져오는 인덱스:

```text
1, 2, 3
```

따라서 `num1`부터 `num2`까지 포함하려면:

```python
arr[num1:num2 + 1]
```

---

# 6. 문자열 메서드 결과 다시 저장하기

잘못된 코드:

```python
answer.replace("a", "")
```

올바른 코드:

```python
answer = answer.replace("a", "")
```

---

# 7. 최소 개수 문제에서 `round()` 사용 주의

예:

```text
7조각짜리 피자
사람 10명
```

계산:

```python
10 / 7
# 1.428...
```

반올림하면:

```python
round(10 / 7)
# 1
```

하지만 실제로는 2판 필요하다.

따라서:

```python
import math

math.ceil(10 / 7)
# 2
```

---

# PCCE에서 자주 쓰는 문제 패턴

## 1. 조건을 만족하는 값 세기

```python
answer = 0

for i in numbers:
    if 조건:
        answer += 1
```

---

## 2. 조건을 만족하는 값 더하기

```python
answer = 0

for i in numbers:
    if 조건:
        answer += i
```

---

## 3. 조건을 만족하는 값 리스트에 저장

```python
answer = []

for i in numbers:
    if 조건:
        answer.append(i)
```

---

## 4. 문자열 한 글자씩 검사

```python
for ch in my_string:
    if ch.isdigit():
        ...
```

---

## 5. 특정 문자 제거

```python
answer = my_string.replace("a", "")
```

여러 문자 제거:

```python
answer = my_string

for ch in "aeiou":
    answer = answer.replace(ch, "")
```

---

## 6. 문자열에서 조건에 맞는 문자만 남기기

```python
answer = ""

for ch in my_string:
    if ch not in "aeiou":
        answer += ch
```

---

## 7. 짝수 합

```python
answer = 0

for i in range(1, n + 1):
    if i % 2 == 0:
        answer += i
```

또는:

```python
answer = sum(range(2, n + 1, 2))
```

---

## 8. 약수 개수

```python
answer = 0

for i in range(1, n + 1):
    if n % i == 0:
        answer += 1
```

---

## 9. 리스트 일부 자르기

```python
return numbers[num1:num2 + 1]
```

---

## 10. 대소문자 바꾸기

```python
answer = ""

for ch in my_string:
    if ch.isupper():
        answer += ch.lower()
    else:
        answer += ch.upper()

return answer
```

또는:

```python
return my_string.swapcase()
```

---

# 우선적으로 익힐 순서

```text
1. if / elif / else
        ↓
2. for / range
        ↓
3. %, //
        ↓
4. 문자열 인덱싱 / 슬라이싱
        ↓
5. 리스트 / append
        ↓
6. replace / upper / lower
        ↓
7. isdigit / isalpha / isupper / islower
        ↓
8. sort / sorted
        ↓
9. sum / max / min / count
        ↓
10. split / join
        ↓
11. set / enumerate
        ↓
12. 딕셔너리
        ↓
13. lambda 정렬
```

---

# 시험 직전 최소 암기 목록

```python
# 길이
len(arr)

# 반복
range(start, end, step)

# 리스트 추가
arr.append(x)

# 문자열 제거 / 변경
s = s.replace("a", "")

# 대소문자
s.upper()
s.lower()
s.swapcase()

# 검사
ch.isdigit()
ch.isalpha()
ch.isupper()
ch.islower()

# 정렬
arr.sort()
sorted(arr)

# 합계 / 최대 / 최소
sum(arr)
max(arr)
min(arr)

# 개수
arr.count(x)

# 포함 여부
x in arr
x not in arr

# 형변환
int(x)
str(x)
list(x)

# 문자열 분리 / 합치기
s.split()
"".join(arr)

# 몫 / 나머지
a // b
a % b

# 슬라이싱
arr[start:end]
arr[:n]
arr[n:]
arr[-n:]
arr[:-n]
arr[::-1]

# 중복 제거
set(arr)

# 절댓값
abs(a - b)
```

---

# 한 줄 요약

PCCE에서는 복잡한 알고리즘보다 다음 조합을 빠르게 사용할 수 있는지가 중요하다.

```text
for + if
for + range
if + %
for + append
문자열 순회 + isdigit/isupper
슬라이싱
replace
sort
sum / max / min
```

문제를 보고 위 패턴 중 어떤 것을 사용할지 바로 떠올릴 수 있도록 연습하는 것이 핵심이다.
