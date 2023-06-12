---
layout: post
title:  " PythonTest 2일차"
---


정수 내림차순으로 배치하기
```python
#join 함수
#'구분자'.join(리스트)
#''.join(리스트)를 이용하면 매개변수로 들어온 ['a', 'b', 'c'] 이런 식의 리스트를 'abc'의 문자열로 합쳐서 반환해주는 함수

문제 설명
함수 solution은 정수 n을 매개변수로 입력받습니다. 
n의 각 자릿수를 큰것부터 작은 순으로 정렬한 새로운 정수를 리턴해주세요. 
예를들어 n이 118372면 873211을 리턴하면 됩니다.

제한 조건
n은 1이상 8000000000 이하인 자연수입니다.

입출력 예
n	      return
118372	873211

문제 풀이
def solution(n):
    answer = list(str(n))
    answer.sort(reverse=True)
    return int(''.join(answer))
```


하샤드 수
```python
문제 설명
양의 정수 x가 하샤드 수이려면 x의 자릿수의 합으로 x가 나누어져야 합니다. 
예를 들어 18의 자릿수 합은 1+8=9이고, 18은 9로 나누어 떨어지므로 18은 하샤드 수입니다. 
자연수 x를 입력받아 x가 하샤드 수인지 아닌지 검사하는 함수, solution을 완성해주세요.

제한 조건
x는 1 이상, 10000 이하인 정수입니다.

입출력 예
x	  return
10	true
12	true
11	false
13	false

입출력 예 설명
입출력 예 #1
10의 모든 자릿수의 합은 1입니다. 10은 1로 나누어 떨어지므로 10은 하샤드 수입니다.

입출력 예 #2
12의 모든 자릿수의 합은 3입니다. 12는 3으로 나누어 떨어지므로 12는 하샤드 수입니다.

입출력 예 #3
11의 모든 자릿수의 합은 2입니다. 11은 2로 나누어 떨어지지 않으므로 11는 하샤드 수가 아닙니다.

입출력 예 #4
13의 모든 자릿수의 합은 4입니다. 13은 4로 나누어 떨어지지 않으므로 13은 하샤드 수가 아닙니다.

문제 풀이
def solution(x):
    answer = [int(i) for i in str(x)]
    if int(x) % sum(answer) == 0:
        return True
    else:
        return False
        
다른 사람 풀이
def Harshad(n):
    return n%sum(int(x) for x in str(n)) == 0
```


두 정수 사이의 합
```python
문제 설명
두 정수 a, b가 주어졌을 때 a와 b 사이에 속한 모든 정수의 합을 리턴하는 함수, solution을 완성하세요.
예를 들어 a = 3, b = 5인 경우, 3 + 4 + 5 = 12이므로 12를 리턴합니다.

제한 조건
a와 b가 같은 경우는 둘 중 아무 수나 리턴하세요.
a와 b는 -10,000,000 이상 10,000,000 이하인 정수입니다.
a와 b의 대소관계는 정해져있지 않습니다.

입출력 예
a	b	return
3	5	12
3	3	3
5	3	12

문제 풀이
def solution(a, b):
    if a<=b:
        return sum(i for i in range(a,b+1))
    else:
        return sum(i for i in range(b, a+1))


다른 사람 풀이
def adder(a, b):
    return sum(range(min(a, b), max(a, b)+1))
```


콜라츠 추측
```python
문제 설명
1937년 Collatz란 사람에 의해 제기된 이 추측은, 주어진 수가 1이 될 때까지 다음 작업을 반복하면, 
모든 수를 1로 만들 수 있다는 추측입니다. 작업은 다음과 같습니다.

1-1. 입력된 수가 짝수라면 2로 나눕니다. 
1-2. 입력된 수가 홀수라면 3을 곱하고 1을 더합니다. 
2. 결과로 나온 수에 같은 작업을 1이 될 때까지 반복합니다. 

예를 들어, 주어진 수가 6이라면 6 → 3 → 10 → 5 → 16 → 8 → 4 → 2 → 1 이 되어 총 8번 만에 1이 됩니다. 
위 작업을 몇 번이나 반복해야 하는지 반환하는 함수, solution을 완성해 주세요. 
단, 주어진 수가 1인 경우에는 0을, 작업을 500번 반복할 때까지 1이 되지 않는다면 –1을 반환해 주세요.

제한 사항
입력된 수, num은 1 이상 8,000,000 미만인 정수입니다.

입출력 예
n	        result
6	         8
16	       4
626331	  -1

입출력 예 설명
입출력 예 #1
문제의 설명과 같습니다.

입출력 예 #2
16 → 8 → 4 → 2 → 1 이 되어 총 4번 만에 1이 됩니다.

입출력 예 #3
626331은 500번을 시도해도 1이 되지 못하므로 -1을 리턴해야 합니다.

문제 풀이
def solution(num):
    itr = 0

    while True:
        if num == 1:
            break
        if itr == 500:
            break
        if num % 2 == 0:
            num = num / 2
            itr += 1
        else:
            num = num * 3 + 1
            itr += 1

    return itr if itr != 500 else -1


다른 사람 풀이
def collatz(num):
    for i in range(500):
        num = num / 2 if num % 2 == 0 else num*3 + 1
        if num == 1:
            return i + 1
    return -1
    
다른 사람 풀이
def solution(num):
    for i in range(500):
        if num == 1:
            return i
        elif num % 2 == 0:
            num = num / 2
        else:
            num = num * 3 + 1
```


서울에서 김서방 찾기
```python
문제 설명
String형 배열 seoul의 element중 "Kim"의 위치 x를 찾아, "김서방은 x에 있다"는 String을 반환하는 함수, solution을 완성하세요. 
seoul에 "Kim"은 오직 한 번만 나타나며 잘못된 값이 입력되는 경우는 없습니다.

제한 사항
seoul은 길이 1 이상, 1000 이하인 배열입니다.
seoul의 원소는 길이 1 이상, 20 이하인 문자열입니다.
"Kim"은 반드시 seoul 안에 포함되어 있습니다.

입출력 예
seoul	            return
["Jane", "Kim"]	  "김서방은 1에 있다"

문제 풀이
def solution(seoul):
    answer = ''

    x = seoul.index('Kim')  
    answer = '김서방은 '+str(x)+'에 있다'

    return answer

다른 사람 풀이
def findKim(seoul):
    return "김서방은 {}에 있다".format(seoul.index('Kim'))
```


나누어 떨어지는 숫자 배열
```python
sort 함수는 리스트명.sort( ) 형식으로 "리스트형의 메소드"​​이며 리스트 원본값을 직접 수정합니다.
sorted 함수는 sorted( 리스트명 ) 형식으로 "내장 함수"이며 리스트 원본 값은 그대로이고 정렬 값을 반환합니다.


문제 설명
array의 각 element 중 divisor로 나누어 떨어지는 값을 오름차순으로 정렬한 배열을 반환하는 함수, solution을 작성해주세요.
divisor로 나누어 떨어지는 element가 하나도 없다면 배열에 -1을 담아 반환하세요.

제한 사항
arr은 자연수를 담은 배열입니다.
정수 i, j에 대해 i ≠ j 이면 arr[i] ≠ arr[j] 입니다.
divisor는 자연수입니다.
array는 길이 1 이상인 배열입니다.

입출력 예
arr	        divisor	return
[5, 9, 7, 10]	5	    [5, 10]
[2, 36, 1, 3]	1	    [1, 2, 3, 36]
[3,2,6]	      10	  [-1]

입출력 예 설명
입출력 예#1
arr의 원소 중 5로 나누어 떨어지는 원소는 5와 10입니다. 따라서 [5, 10]을 리턴합니다.

입출력 예#2
arr의 모든 원소는 1으로 나누어 떨어집니다. 원소를 오름차순으로 정렬해 [1, 2, 3, 36]을 리턴합니다.

입출력 예#3
3, 2, 6은 10으로 나누어 떨어지지 않습니다. 나누어 떨어지는 원소가 없으므로 [-1]을 리턴합니다.

문제 풀이
def solution(arr, divisor):
    new_list = sorted(i for i in arr if i % divisor == 0)
    return new_list if len(new_list) > 0 else [-1]
#new_list를 arr이라고 하는 것이 더 좋았을 

다른 사람 풀이
def solution(arr, divisor):
    arr = [x for x in arr if x % divisor == 0];
    arr.sort();
    return arr if len(arr) != 0 else [-1];

def solution(arr, divisor): 
return sorted([n for n in arr if n%divisor == 0]) or [-1]

python은 or 앞이 참일경우 해당 값까지만 , 거짓일경우 뒤에 것까지 호출
```


핸드폰 번호 가리기
```python
문제 설명
프로그래머스 모바일은 개인정보 보호를 위해 고지서를 보낼 때 고객들의 전화번호의 일부를 가립니다.
전화번호가 문자열 phone_number로 주어졌을 때, 전화번호의 뒷 4자리를 제외한 나머지 숫자를 
전부 *으로 가린 문자열을 리턴하는 함수, solution을 완성해주세요.

제한 조건
phone_number는 길이 4 이상, 20이하인 문자열입니다.

입출력 예
phone_number	  return
"01033334444"	  "*******4444"
"027778888"	    "*****8888"

문제 풀이
def solution(phone_number):
    return '*' * (len(phone_number) - 4) + phone_number[-4:]
    
다른 사람 풀이
def hide_numbers(s):
    return "*"*(len(s)-4)+s[-4:]
```
