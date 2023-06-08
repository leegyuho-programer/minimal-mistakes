---
layout: post
title:  " PythonTest 1일차"
---




제일 작은 수 제거하기
```python
문제 설명
정수를 저장한 배열, arr 에서 가장 작은 수를 제거한 배열을 리턴하는 함수, solution을 완성해주세요. 
단, 리턴하려는 배열이 빈 배열인 경우엔 배열에 -1을 채워 리턴하세요. 
예를들어 arr이 [4,3,2,1]인 경우는 [4,3,2]를 리턴 하고, [10]면 [-1]을 리턴 합니다.



제한 조건
arr은 길이 1 이상인 배열입니다.
인덱스 i, j에 대해 i ≠ j이면 arr[i] ≠ arr[j] 입니다.

입출력 예
arr	      return
[4,3,2,1]	[4,3,2]
[10]	    [-1]

문제 풀이
def solution(arr):
    arr.remove(min(arr))

    if len(arr) == 0:
        return [-1]
    else:
        return arr
```


가운데 글자 가져오기
```python
문제 설명
단어 s의 가운데 글자를 반환하는 함수, solution을 만들어 보세요. 
단어의 길이가 짝수라면 가운데 두글자를 반환하면 됩니다.

제한 사항
s는 길이가 1 이상, 100이하인 스트링입니다.

입출력 예
s	      return
"abcde"	"c"
"qwer"	"we"

문제 풀이
def solution(s):
    if len(s) % 2 == 0:
        return s[int(len(s)/2) - 1 : int(len(s)/2) + 1]
    else:
        return s[int(len(s)/2)]
        
다른 사람 풀이
def string_middle(str):
     return str[(len(str)-1)//2 : len(str)//2 + 1]
```


수박수박수박수박수박수?
```python
문제 설명
길이가 n이고, "수박수박수박수...."와 같은 패턴을 유지하는 문자열을 리턴하는 함수, solution을 완성하세요. 
예를들어 n이 4이면 "수박수박"을 리턴하고 3이라면 "수박수"를 리턴하면 됩니다.

제한 조건
n은 길이 10,000이하인 자연수입니다.

입출력 예
n	  return
3	  "수박수"
4	  "수박수박"

문제 풀이
def solution(n):
    answer = ''
    
    for i in range(n):
        if i % 2 == 0:
            answer += '수'
        else:
            answer += '박'

    return answer
    
다른 사람 풀이
def solution(n):
    answer = "수박" * (n//2)
    if n%2 != 0:
        answer += "수"
    return answer

def solution(n):
    return "수박"*(n//2) + "수"*(n%2)
    
def solution(n):
    str = "수박"*n
    return str[:n]
```


문자열 내림차순으로 배치하기
```python
문제 설명
문자열 s에 나타나는 문자를 큰것부터 작은 순으로 정렬해 새로운 문자열을 리턴하는 함수, solution을 완성해주세요.
s는 영문 대소문자로만 구성되어 있으며, 대문자는 소문자보다 작은 것으로 간주합니다.

제한 사항
str은 길이 1 이상인 문자열입니다.

입출력 예
s	          return
"Zbcdefg"	  "gfedcbZ"

문제 풀이
def solution(s):
    s=sorted(s, reverse=True)
    return "".join(s)
    
다른 사람 풀이
def solution(s):
    s = list(s)
    s.sort(reverse = True)
    answer = ""
    for i in s:
        answer = answer + i
    return answer
```


문자열 다루기 기본
```python
#isdigit()이라는 함수를 사용하면 해당 문자열이 숫자로 이루워져 있는지 확인 할 수 있다. 

문제 설명
문자열 s의 길이가 4 혹은 6이고, 숫자로만 구성돼있는지 확인해주는 함수, solution을 완성하세요. 
예를 들어 s가 "a234"이면 False를 리턴하고 "1234"라면 True를 리턴하면 됩니다.

제한 사항
s는 길이 1 이상, 길이 8 이하인 문자열입니다.
s는 영문 알파벳 대소문자 또는 0부터 9까지 숫자로 이루어져 있습니다.

입출력 예
입출력 예
s     	return
"a234"	false
"1234"	true

문제 풀이
def solution(s):
    if (len(s) == 4 or len(s) == 6) and s.isdigit():
                return True
    else:
                return False
                
다른 사람 풀이                
def alpha_string46(s):
    return s.isdigit() and len(s) in [4,6]  #(4,6)도 가능하다
    
def solution(s):
    return s.isdigit() and (len(s)==4 or len(s)== 6)
```


행렬의 덧셈
```python
문제 설명
행렬의 덧셈은 행과 열의 크기가 같은 두 행렬의 같은 행, 같은 열의 값을 서로 더한 결과가 됩니다. 
2개의 행렬 arr1과 arr2를 입력받아, 행렬 덧셈의 결과를 반환하는 함수, solution을 완성해주세요.

제한 조건
행렬 arr1, arr2의 행과 열의 길이는 500을 넘지 않습니다.

입출력 예
arr1	          arr2	          return
[[1,2],[2,3]]	  [[3,4],[5,6]] 	[[4,6],[7,9]]
[[1],[2]]	      [[3],[4]]     	[[4],[6]]

문제 풀이
어려움.
```


직사각형 별찍기
```python
#map(변환 함수, 대상 리스트)

#input input은 파이썬의 입력 함수로 입력되는 모든 것을 문자열로 취급한다. 

#strip 문자열 메소드 중 하나로 문자열의 공백을 제거한다.
#lstrip은 왼쪽 공백 제거, rstrip은 오른쪽 공백 제거, strip은 양쪽의 공백을 모두 제거한다. 

#split 문자열 메소드 중 하나로 문자열을 분할한다.
#여러 개로 분할된 문자열은 리스트에 저장된다.
#ex)dept = "컴퓨터학과 정보통계학과 문헌정보학과 경영학과"
#print(dept.split()) # 구분자를 기준으로 문자열을 분할. default는 공백문자

문제 설명
이 문제에는 표준 입력으로 두 개의 정수 n과 m이 주어집니다.
별(*) 문자를 이용해 가로의 길이가 n, 세로의 길이가 m인 직사각형 형태를 출력해보세요.

제한 조건
n과 m은 각각 1000 이하인 자연수입니다.

예시
입력

5 3

출력

*****
*****
*****

문제 풀이

```


형 변환
```python
문제 설명


제한 조건


입출력 예


문제 풀이

```


형 변환
```python
문제 설명


제한 조건


입출력 예


문제 풀이

```
