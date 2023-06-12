---
layout: post
title:  " PythonTest 4일차"
---




이상한 문자 만들기
```python
문제 설명
문자열 s는 한 개 이상의 단어로 구성되어 있습니다. 각 단어는 하나 이상의 공백문자로 구분되어 있습니다. 
각 단어의 짝수번째 알파벳은 대문자로, 홀수번째 알파벳은 소문자로 바꾼 문자열을 리턴하는 함수, solution을 완성하세요.

제한 사항
문자열 전체의 짝/홀수 인덱스가 아니라, 단어(공백을 기준)별로 짝/홀수 인덱스를 판단해야합니다.
첫 번째 글자는 0번째 인덱스로 보아 짝수번째 알파벳으로 처리해야 합니다.


입출력 예
s	                return
"try hello world"	"TrY HeLlO WoRlD"

입출력 예 설명
"try hello world"는 세 단어 "try", "hello", "world"로 구성되어 있습니다. 
각 단어의 짝수번째 문자를 대문자로, 홀수번째 문자를 소문자로 바꾸면 "TrY", "HeLlO", "WoRlD"입니다. 
따라서 "TrY HeLlO WoRlD" 를 리턴합니다.

문제 풀이
def solution(s):
    answer = ""
    
    idx = -1
    for i in s:
        if i == " ":
            idx = -1
            answer += " "
        else:
            idx += 1
            if idx%2 == 0:
                answer += i.upper()
            else:
                answer += i.lower()
    return answer
    
다른 사람 풀이
def solution(s):
    answer = ''
    for i in s.split(' '):
        for j in range(len(i)) :
            if j%2 ==0 :
                answer+= i[j].upper()
            else:
                answer+= i[j].lower()
        answer+=' '
    
    return answer[0:-1]

print(solution("try hello world"))
```


시저 암호
```python
문제 설명
어떤 문장의 각 알파벳을 일정한 거리만큼 밀어서 다른 알파벳으로 바꾸는 암호화 방식을 시저 암호라고 합니다. 
예를 들어 "AB"는 1만큼 밀면 "BC"가 되고, 3만큼 밀면 "DE"가 됩니다. "z"는 1만큼 밀면 "a"가 됩니다. 
문자열 s와 거리 n을 입력받아 s를 n만큼 민 암호문을 만드는 함수, solution을 완성해 보세요.

제한 조건
공백은 아무리 밀어도 공백입니다.
s는 알파벳 소문자, 대문자, 공백으로만 이루어져 있습니다.
s의 길이는 8000이하입니다.
n은 1 이상, 25이하인 자연수입니다.

입출력 예
s	        n	    result
"AB"	    1	    "BC"
"z"	      1	    "a"
"a B z"	  4	    "e F d"

문제 풀이
첫 풀이
def solution(s, n):
    answer = ""
    for i in s:
        answer += ord("i") + n
    
    return answer
    
다음 풀이
def solution(s, n):
    UPPER_ALPHA = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
    lower_alpha = "abcdefghijklmnopqrstuvwxyz"
    answer = ""
    
    for i in s:
        if i.islower():
            answer += lower_alpha[(lower_alpha.index(i) + n) % 26]
        elif i.isupper():
            answer += UPPER_ALPHA[(UPPER_ALPHA.index(i) + n) % 26]
        else:
            answer += " "
            
    return answer

다른 사람 풀이
def caesar(s, n):
    s = list(s)
    for i in range(len(s)):
        if s[i].isupper():
            s[i]=chr((ord(s[i])-ord('A')+ n)%26+ord('A'))
        elif s[i].islower():
            s[i]=chr((ord(s[i])-ord('a')+ n)%26+ord('a'))

    return "".join(s)
```
