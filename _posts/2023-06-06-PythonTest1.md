---
layout: post
title:  " PythonTest 1일차"
---


약수의 합
```python
문제 설명
정수 n을 입력받아 n의 약수를 모두 더한 값을 리턴하는 함수, solution을 완성해주세요.

제한 사항
n은 0 이상 3000이하인 정수입니다.

입출력 예
n	  return
12	28
5	  6

입출력 예 설명
입출력 예 #1
12의 약수는 1, 2, 3, 4, 6, 12입니다. 이를 모두 더하면 28입니다.

입출력 예 #2
5의 약수는 1, 5입니다. 이를 모두 더하면 6입니다.

문제 풀이
def solution(n):
    return sum([i for i in range(1,n+1) if n%i ==0])
    

```



평균 구하기
```python
문제 설명
정수를 담고 있는 배열 arr의 평균값을 return하는 함수, solution을 완성해보세요.

제한사
arr은 길이 1 이상, 100 이하인 배열입니다.
arr의 원소는 -10,000 이상 10,000 이하인 정수입니다.

입출력 예
arr	      return
[1,2,3,4]	2.5
[5,5]   	5

문제 풀이
def solution(arr):
    return(sum(arr)/len(arr))
```



짝수와 홀수
```python
문제 설명
정수 num이 짝수일 경우 "Even"을 반환하고 홀수인 경우 "Odd"를 반환하는 함수, solution을 완성해주세요.

제한 조건
num은 int 범위의 정수입니다.
0은 짝수입니다.

입출력 예
num	return
3 	"Odd"
4	  "Even"

문제 풀이
def solution(num):
    if num%2 == 0:
        return 'Even'
    else:
        return 'Odd'
```



x만큼 간격이 있는 n개의 숫자
```python
문제 설명
함수 solution은 정수 x와 자연수 n을 입력 받아, x부터 시작해 x씩 증가하는 숫자를 n개 지니는 리스트를 리턴해야 합니다. 
다음 제한 조건을 보고, 조건을 만족하는 함수, solution을 완성해주세요.

제한 조건
x는 -10000000 이상, 10000000 이하인 정수입니다.
n은 1000 이하인 자연수입니다.

입출력 예
x 	n	  answer
2 	5	  [2,4,6,8,10]
4	  3 	[4,8,12]
-4	2	  [-4, -8]

문제 풀이
def solution(x, n):
    return [x + x * i for i in range(n)]
```



자연수 뒤집어 배열로 만들기
```python
#map(변환 함수, 대상 리스트)

문제 설명
자연수 n을 뒤집어 각 자리 숫자를 원소로 가지는 배열 형태로 리턴해주세요.
예를들어 n이 12345이면 [5,4,3,2,1]을 리턴합니다.

제한 조건
n은 10,000,000,000이하인 자연수입니다.

입출력 예
n   	return
12345	[5,4,3,2,1]

문제 풀이
def solution(n):
    return [int(i) for i in str(n)][::-1]
    
다른 사람 풀이
def digit_reverse(n):
    return list(map(int, reversed(str(n))))
```



정수 제곱근 판별
```python
문제 설명
임의의 양의 정수 n에 대해, n이 어떤 양의 정수 x의 제곱인지 아닌지 판단하려 합니다.
n이 양의 정수 x의 제곱이라면 x+1의 제곱을 리턴하고, n이 양의 정수 x의 제곱이 아니라면 -1을 리턴하는 함수를 완성하세요.

제한 사
n은 1이상, 50000000000000 이하인 양의 정수입니다.

입출력 예
n	  return
121	144
3	  -1

입출력 예 설명
입출력 예#1
121은 양의 정수 11의 제곱이므로, (11+1)를 제곱한 144를 리턴합니다.

입출력 예#2
3은 양의 정수의 제곱이 아니므로, -1을 리턴합니다.

문제 풀이
def solution(n):
    sqrt = n ** (1/2)
    if sqrt % 1 == 0:
        return (sqrt + 1) ** 2
    else:
        return -1
```



문자열을 정수로 바꾸기
```python
문제 설명
문자열 s를 숫자로 변환한 결과를 반환하는 함수, solution을 완성하세요.

제한 조건
s의 길이는 1 이상 5이하입니다.
s의 맨앞에는 부호(+, -)가 올 수 있습니다.
s는 부호와 숫자로만 이루어져있습니다.
s는 "0"으로 시작하지 않습니다.

입출력 예
예를들어 str이 "1234"이면 1234를 반환하고, "-1234"이면 -1234를 반환하면 됩니다.
str은 부호(+,-)와 숫자로만 구성되어 있고, 잘못된 값이 입력되는 경우는 없습니다.

문제 풀이
def solution(s):
    if 1 <= len(str(s)) <= 5:
    	return int(str(s))
    else:
        return 1
    
다른 사람 풀이
1.
def strToInt(str): 
    result = 0
    for idx, number in enumerate(str[::-1]):
        if number == '-':
            result *= -1
        else:
            result += int(number) * (10 ** idx)
    return result
#풀이
'''
str[::-1]은 주어진 스트링을 거꾸로 만들어 버립니다. 그 다음에 enumerate 함수를 이용하여 한 글자당 인덱스를 배정해서 각 자리에 10의 지수만큼 곱해서 더해주는 거네요. 예를 들면 "-1234"는 str[::-1]에 의해 "4321-"가 되고 4 * (10 ** 0) + 3 * (10 ** 1) + 2 * (10 **2) + 1 * (10 ** 3)를 한 이후에 "-" 는 이 숫자를 마이너스로 만들어 버립니다.
'''
2.
def strToInt(str):
    result = int(str)
    return result
```
