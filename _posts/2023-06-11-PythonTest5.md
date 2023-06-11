---
layout: post
title:  " PythonTest 5일차"
---




숫자 문자열과 영단어
```python
#enumerate
for eng in enumerate(["zero", "one", "two"]):
    print(eng)
#출력 결과
(0, 'zero')
(1, 'one')
(2, 'two')

for idx, eng in enumerate(["zero", "one", "two"]):
    print(idx, eng)
#출력 결과
0 zero
1 one
2 two


#replace
a = 'hello world'
>>> a.replace('hello','hi')
hi world

'oxoxoxoxox'.replace('ox', '*')
*****


문제 설명

네오와 프로도가 숫자놀이를 하고 있습니다. 
네오가 프로도에게 숫자를 건넬 때 일부 자릿수를 영단어로 바꾼 카드를 건네주면 프로도는 원래 숫자를 찾는 게임입니다.

다음은 숫자의 일부 자릿수를 영단어로 바꾸는 예시입니다.
1478 → "one4seveneight"
234567 → "23four5six7"
10203 → "1zerotwozero3"
이렇게 숫자의 일부 자릿수가 영단어로 바뀌어졌거나, 혹은 바뀌지 않고 그대로인 문자열 s가 매개변수로 주어집니다. 
s가 의미하는 원래 숫자를 return 하도록 solution 함수를 완성해주세요.

참고로 각 숫자에 대응되는 영단어는 다음 표와 같습니다.

숫자	영단어
0	    zero
1	    one
2	    two
3	    three
4	    four
5	    five
6	    six
7   	seven
8	    eight
9   	nine

제한 조건
1 ≤ s의 길이 ≤ 50
s가 "zero" 또는 "0"으로 시작하는 경우는 주어지지 않습니다.
return 값이 1 이상 2,000,000,000 이하의 정수가 되는 올바른 입력만 s로 주어집니다.

입출력 예
s	                  result
"one4seveneight"	  1478
"23four5six7"	      234567
"2three45sixseven"	234567
"123"	123

입출력 예 설명
입출력 예 #1
문제 예시와 같습니다.

입출력 예 #2
문제 예시와 같습니다.

입출력 예 #3
"three"는 3, "six"는 6, "seven"은 7에 대응되기 때문에 정답은 입출력 예 #2와 같은 234567이 됩니다.
입출력 예 #2와 #3과 같이 같은 정답을 가리키는 문자열이 여러 가지가 나올 수 있습니다.

입출력 예 #4
s에는 영단어로 바뀐 부분이 없습니다.

문제 풀이
첫번째 풀이
def solution(s):
    num = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    word = [zero, one, two, three, four, five, six, seven, eight, nine]
    answer = 0
    
    for i in s:
        if i.isdigit == 0: #숫자로만 이루어진 것이 아닌 경우
            answer += 
        else:
            answer += i
            
    return answer
    
두번째 풀이
def solution(s):
    word = ["zero", "one", "two", "three", "four", "five", "six", "seven", "eight", "nine"]
    
    for idx, words in enumerate(word):
        s = s.replace(words, str(idx))
    return int(s)

다른 사람 풀이
num_dic = {"zero":"0", "one":"1", "two":"2", "three":"3", "four":"4", "five":"5", "six":"6", "seven":"7", "eight":"8", "nine":"9"}

def solution(s):
    answer = s
    for key, value in num_dic.items():
        answer = answer.replace(key, value)
    return int(answer)
```


문자열 내 마음대로 정렬하기
```python
#lambda
(lambda x: x + 10)(1) 
> 11


a = [(1, 2), (5, 1), (0, 1), (5, 2), (3, 0)]

c = sorted(a, key = lambda x : x[0]) 

c = [(0, 1), (1, 2), (3, 0), (5, 1), (5, 2)]

d = sorted(a, key = lambda x : x[1]) 

d = [(3, 0), (5, 1), (0, 1), (1, 2), (5, 2)]


-를 붙이면, 현재와 반대차순으로 정렬된다.
e = sorted(a, key = lambda x : (x[0], -x[1])) 
=> [(0, 1), (1, 2), (3, 0), (5, 2), (5, 1)]

f = sorted(a, key = lambda x : -x[0]) 
=> [(5, 1), (5, 2), (3, 0), (1, 2), (0, 1)])


뒤에 문자 순 정렬
s = ['2 A', '1 B', '4 C', '1 A']
s.sorted(s, key=lambda x: (x.split()[1], x.split()[0]))
=> ['1 A', '2 A', '1 B', '4 C']
a_list = ['a', 'b', 'd', 'd', 'b','s']
a_counter = Counter(a_list).most_common()
=> [('b', 2), ('d', 2), ('a', 1), ('s', 1)]

# 문자 역순(아스키 값 이용)
sorted(a_counter,  key=lambda x: (-x[1], -ord(x[0])))
=> [('d', 2), ('b', 2), ('s', 1), ('a', 1)]


문제 설명
문자열로 구성된 리스트 strings와, 정수 n이 주어졌을 때, 각 문자열의 인덱스 n번째 글자를 기준으로 오름차순 정렬하려 합니다. 
예를 들어 strings가 ["sun", "bed", "car"]이고 n이 1이면 각 단어의 인덱스 1의 문자 "u", "e", "a"로 strings를 정렬합니다.

제한 조건
strings는 길이 1 이상, 50이하인 배열입니다.
strings의 원소는 소문자 알파벳으로 이루어져 있습니다.
strings의 원소는 길이 1 이상, 100이하인 문자열입니다.
모든 strings의 원소의 길이는 n보다 큽니다.
인덱스 1의 문자가 같은 문자열이 여럿 일 경우, 사전순으로 앞선 문자열이 앞쪽에 위치합니다.

입출력 예
strings	                  n	    return
["sun", "bed", "car"]   	1	    ["car", "bed", "sun"]
["abce", "abcd", "cdx"] 	2	    ["abcd", "abce", "cdx"]

입출력 예 설명
입출력 예 1
"sun", "bed", "car"의 1번째 인덱스 값은 각각 "u", "e", "a" 입니다. 이를 기준으로 strings를 정렬하면 ["car", "bed", "sun"] 입니다.

입출력 예 2
"abce"와 "abcd", "cdx"의 2번째 인덱스 값은 "c", "c", "x"입니다. 따라서 정렬 후에는 "cdx"가 가장 뒤에 위치합니다. 
"abce"와 "abcd"는 사전순으로 정렬하면 "abcd"가 우선하므로, 답은 ["abcd", "abce", "cdx"] 입니다.

문제 풀이
def solution(strings, n):
    return sorted(sorted(strings), key=lambda x:x[n])
    #x가 들어왔을때 x의n번째 index를 
```



K번째수
```python
문제 설명
배열 array의 i번째 숫자부터 j번째 숫자까지 자르고 정렬했을 때, k번째에 있는 수를 구하려 합니다.

예를 들어 array가 [1, 5, 2, 6, 3, 7, 4], i = 2, j = 5, k = 3이라면

array의 2번째부터 5번째까지 자르면 [5, 2, 6, 3]입니다.
1에서 나온 배열을 정렬하면 [2, 3, 5, 6]입니다.
2에서 나온 배열의 3번째 숫자는 5입니다.

배열 array, [i, j, k]를 원소로 가진 2차원 배열 commands가 매개변수로 주어질 때, 
commands의 모든 원소에 대해 앞서 설명한 연산을 적용했을 때 나온 결과를 배열에 담아 return 하도록 solution 함수를 작성해주세요.

제한사항
array의 길이는 1 이상 100 이하입니다.
array의 각 원소는 1 이상 100 이하입니다.
commands의 길이는 1 이상 50 이하입니다.
commands의 각 원소는 길이가 3입니다.


입출력 예
array	                  commands	                           return
[1, 5, 2, 6, 3, 7, 4]	  [[2, 5, 3], [4, 4, 1], [1, 7, 3]]	   [5, 6, 3]

입출력 예 설명
[1, 5, 2, 6, 3, 7, 4]를 2번째부터 5번째까지 자른 후 정렬합니다. [2, 3, 5, 6]의 세 번째 숫자는 5입니다.
[1, 5, 2, 6, 3, 7, 4]를 4번째부터 4번째까지 자른 후 정렬합니다. [6]의 첫 번째 숫자는 6입니다.
[1, 5, 2, 6, 3, 7, 4]를 1번째부터 7번째까지 자릅니다. [1, 2, 3, 4, 5, 6, 7]의 세 번째 숫자는 3입니다.

문제 풀이
def solution(array, commands):
    answer = []
    for i, j, k in commands:
        new_arr = sorted(array[i-1:j])
        answer.append(new_arr[k-1])
    return answer
    
다른 사람 풀이
def solution(array, commands):
    return list(map(lambda x:sorted(array[x[0]-1:x[1]])[x[2]-1], commands))
```



2016년
```python
문제 설명
2016년 1월 1일은 금요일입니다. 2016년 a월 b일은 무슨 요일일까요? 
두 수 a ,b를 입력받아 2016년 a월 b일이 무슨 요일인지 리턴하는 함수, solution을 완성하세요. 
요일의 이름은 일요일부터 토요일까지 각각 SUN,MON,TUE,WED,THU,FRI,SAT 입니다. 
예를 들어 a=5, b=24라면 5월 24일은 화요일이므로 문자열 "TUE"를 반환하세요.

제한 조건
2016년은 윤년입니다.
2016년 a월 b일은 실제로 있는 날입니다. (13월 26일이나 2월 45일같은 날짜는 주어지지 않습니다)

입출력 예
a	b	  result
5	24	"TUE"

문제 풀이
def solution(M, D):
    day = D
    month_with_day = {1:31, 2:29, 3:31, 4:30, 5:31, 6:30, 7:31, 
                      8:31, 9:30, 10:31, 11:30, 12:31}
    for m in range(1, M):
        day += month_with_day[m]
    return ["THU","FRI","SAT","SUN","MON","TUE","WED"][day%7]
    
다른 사람 풀이
def getDayName(a,b):
    month = [31, 29, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]
    day = ['FRI', 'SAT', 'SUN', 'MON', 'TUE', 'WED', 'THU']
    return day[(sum(month[:a-1])+b-1)%7]

print(getDayName(5,24))
```



모의고사
```python
문제 설명
수포자는 수학을 포기한 사람의 준말입니다. 수포자 삼인방은 모의고사에 수학 문제를 전부 찍으려 합니다. 
수포자는 1번 문제부터 마지막 문제까지 다음과 같이 찍습니다.

1번 수포자가 찍는 방식: 1, 2, 3, 4, 5, 1, 2, 3, 4, 5, ...
2번 수포자가 찍는 방식: 2, 1, 2, 3, 2, 4, 2, 5, 2, 1, 2, 3, 2, 4, 2, 5, ...
3번 수포자가 찍는 방식: 3, 3, 1, 1, 2, 2, 4, 4, 5, 5, 3, 3, 1, 1, 2, 2, 4, 4, 5, 5, ...

1번 문제부터 마지막 문제까지의 정답이 순서대로 들은 배열 answers가 주어졌을 때, 
가장 많은 문제를 맞힌 사람이 누구인지 배열에 담아 return 하도록 solution 함수를 작성해주세요.

제한 조건
시험은 최대 10,000 문제로 구성되어있습니다.
문제의 정답은 1, 2, 3, 4, 5중 하나입니다.
가장 높은 점수를 받은 사람이 여럿일 경우, return하는 값을 오름차순 정렬해주세요.

입출력 예
answers	      return
[1,2,3,4,5]	  [1]
[1,3,2,4,2]	  [1,2,3]

입출력 예 설명
입출력 예 #1
수포자 1은 모든 문제를 맞혔습니다.
수포자 2는 모든 문제를 틀렸습니다.
수포자 3은 모든 문제를 틀렸습니다.
따라서 가장 문제를 많이 맞힌 사람은 수포자 1입니다.

입출력 예 #2
모든 사람이 2문제씩을 맞췄습니다.

문제 풀이
def solution(answers):
    one = [1, 2, 3, 4, 5] * 2000
    two = [2, 1, 2, 3, 2, 4, 2, 5] * 1250
    three = [3, 3, 1, 1, 2, 2, 4, 4, 5, 5] * 1000
    answer1 = []
    answer2 = []
    answer3 = []
    
    for i in range(0,len(answers)):
        if one[i] == answers[i]:
            answer1 += str(one[i])
            
    for i in range(0,len(answers)):
        if two[i] == answers[i]:
            answer2 += str(two[i])
            
    for i in range(0,len(answers)):
        if three[i] == answers[i]:
            answer3 += str(three[i])
            
    a = len(answer1)
    b = len(answer2)
    c = len(answer3)
    
    if a > b and a > c:
        return [1]
    elif b > a and b > c:
        return [2]
    elif c > a and c > b:
        return [3]
    elif a == b and a > c:
        return [1,2]
    elif a > b and a == c:
        return [1,3]
    elif b == c and b > a:
        return [2,3]
    elif a == b == c:
        return [1,2,3]
    else:
        return 0

다른 사람 풀이
def solution(answers):
    pattern1 = [1,2,3,4,5]
    pattern2 = [2,1,2,3,2,4,2,5]
    pattern3 = [3,3,1,1,2,2,4,4,5,5]
    score = [0, 0, 0]
    result = []

    for idx, answer in enumerate(answers):
        if answer == pattern1[idx%len(pattern1)]:
            score[0] += 1
        if answer == pattern2[idx%len(pattern2)]:
            score[1] += 1
        if answer == pattern3[idx%len(pattern3)]:
            score[2] += 1

    for idx, s in enumerate(score):
        if s == max(score):
            result.append(idx+1)

    return result
```
