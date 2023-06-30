---
layout: post
title:  "Re JS 1일차"
---



변수
```javascript
let color = "pink"

console.log(color)
//결과 pink

let color = "pink"
let color = "black"

console.log(color)
//이렇게 하면 오류가 뜬다. let은 한번쓰면 그 다음은 let을 빼고 변수만 써주면 된다.
//ex) color = "black"


const password = "pink"
password = "black"

console.log(password)
//이렇게 하면 오류가 뜬다.
//const는 값을 고정시킨다.


let : 변수를 선언하고 재할당도 가능 언제든 값을 바꿀 수 있음
const : 변수에 한번 값을 할당하면 다시 값을 바꿀 수 없음
var : let의 옛날버전. let과 작동원리는 같으나 호이스팅과같은 문제가 있음 
```


자료형과 연산자
```javascript
자료형
String: 문자열 타입이라고도 한다. “” 큰따옴표나 ‘’ 작은따옴표 안에 들어가 있는 값을 string 타입이라고 함
숫자 : 숫자타입. 양수, 음수 소수 다 숫자 타입
boolean : 논리연산에 많이 쓰이는 타입으로 true, false 단 두개의 값만 있다.
그 외에: 배열, 객체 등…

연산자
+, -, *, /, %, ++, --
  
단축된 연산자
+=, -=, *=, /=, %/

관계 연산자
==, ===, !=, >, >=, <, <=

논리 연산자
&&, ||, !


// 증가연산
let a =1
a++ // a=a+1과같다 
console.log(a)// 2

//감소연산
let b =2 b-- // b=b-1과 같다
console.log(b) // 1 

//단축된 연산자
let c =1
c+=3 // c=c+3을 줄여서 표현한 것이다
console.log(c)//4

let d = 3
d-=2 // d=d-2를 줄여서 표현한 것이다 
console.log(d)//1

// NOT 연산자 : 어떤값의 반대되는 값을 반환 true 면 false를, false면 true를 반환 
let f = true
console.log(!f) // false 

// 같다라는 표현은 ==  
let x = 2
let y =2 console.log(x == y)// true

//다르다라는 표현은 != 
console.log(x != y)//false
```



호이스팅, let과 var의 차이
```javascript
호이스팅 : 함수가 실행되기 전에 안에 있는 변수들을 범위의 최상단으로 끌어올리는 것
인터프리터가 변수와 함수의 메모리 공간을 선언 전에 미리 할당하는 것을 의미
ex)
var a = 1
console.log(a) 
//결과 1

console.log(a)
var a = 1
console.log(a)
//결과 undefined   1
//a가 선언되기 전에 a를 호출한 경우 다른 언어면 에러가 발생하지만 javascript에서는 에러가 안나온다.
//이것이 가능한 이유는 호이스팅 때문이다.


console.log(a)
a = 1
var a
console.log(a)
//결과 undefined   1
//심지어 이것도 가능하다.


console.log(a)
//결과 에러가 발생한다. a is not defined



var는 전역변수와 지역변수의 개념이 확실치 않다.
ex)
var a = 2

function foo() {
  var b = 1

}

console.log(b)
//결과 에러가 발생한다.

for(var i = 1; i < 5; i++){
  console.log(i)
}
console.log(i)
//결과 1 2 3 4 5

이와 같이 var는 함수만 지역변수로 호이스팅이 되고 나머지는 다 전역변수로 올려버린다.(for문, if문 등등)


var a = 1
console.log(a)
var a = 2
console.log(a)
심지어 이것도 출력을 하면 1 2 가 나온다.(다른 언어였으면 변수의 이름은 절대로 중복이 안된다)




위와 같은 말도 안되는 것들 때문에 let이 나오게 됐다.
let을 사용하게 되면 모든 문제가 해결된다.
let a = 1
console.log(a)
let a = 2
console.log(a)
//이렇게 하면 에러가 발생한다.


for(let i = 1; i < 5; i++){
  console.log(i)
}
console.log(i)
//4번줄의 i는 정의되지 않았다고 뜨며 1 2 3 4가 출력된다.


console.log(a)
let a = 1
console.log(a)
//결과 에러가 발생한다.(초기화 전에 a에 접근할 수 없음)


let도 호이스팅이 가능하다.
let은 Temporal Death Zone(TDZ)라는 개념을 만들었다.
console.log(a)
let a = 1
console.log(a)
//TDZ는 이런 상황에서 a가 호이스팅으로 기억이 된건 알겠어 하지만 a 선언문이 나오기 전까진 너는 a에 접근할 수 없어.
//라는 개념이다. 일시적으로 죽은 Zone이야 라는 뜻이다. a가 선언되기 전까지는 죽은 zone이라는 뜻이다. a가 선언되기 전까지는 사용X

```



배열
```javascript
배열은 관련있는 데이터들을 하나로 묶어서 하나의 변수 아래에 저장하는 것이다.

let fruit = "banana"
let fruit2 = "apple"
let fruit3 = "grape"
let fruit4 = "mango"

let fruit = ["banana", "apple", "grape", "mango"]

console.log(fruit)
//결과 ["banana", "apple", "grape", "mango"]

console.log(fruit[0])
//결과 banana

fruit[0] = "cherry"
console.log(fruit)
//결과 ["cherry", "apple", "grape", "mango"]


//pop() : 마지막에 있는 아이템을 뺌
fruit.pop()
console.log(fruit)
결과 ["cherry", "apple", "grape"]


//push() : 마지막에 아이템을 추가함
fruit.push("pineapple")
console.log(fruit)
결과 ["cherry", "apple", "grape", "pineapple"]


//includes : 해당 아이템을 배열이 포함하고 있는지 알려
console.log(fruit.includes("apple"))
결과 true

console.log(fruit.includes("pear"))
결과 false


//indexOf() : 해당 아이템의 인덱스를 찾아줌
console.log(fruit.indexOf("apple"))
결과 1



//slice 와 splice
//slice는 기존 배열을 건들지 않는다. 그래서 fruit.slice(2) console.log(fruit) 이렇게 하면 
//["cherry", "apple", "grape", "pineapple"] 이 값이 출력된다.
//let extrafruit = fruit.slice(1,3)
//console.log(extrafruit) 이렇게 하면 ["apple", "grape"] 이렇게 출력된다.
//splice는 기존 파일을 자른다.
//상황에 맞춰서 쓰면 된다.
//ex) 잘린 값을 빼서 새 배열을 만들고 싶으면 slice

//slice() : 배열 아이템을 잘래내는 역할 
//값을 1개나 2개를 받을 수 있다. 2개를 받으면 (1, 3) 이 경우 인덱스 1부터 3이전까지 즉 2까지를 말한다.
console.log(fruit.slice(2))
//결과 ["grape", "pineapple"] (잘린 값이 반환된다)

console.log(fruit.slice(1))
//결과 ["apple", "grape", "pineapple"]

console.log(fruit.slice(1,3))
//결과 ["apple", "grape"]

//splice(시작점, 갯수) : 시작점으로부터 몇 개의 아이템을 제거하고 싶은지
fruit.splice(2,1)
console.log(fruit)
//결과 ["cherry", "apple", "pineapple"] (잘린 후의 값이 나온다)


//length : 배열 함수는 아니지만 배열의 크기를 리턴해주는 속성
let array = ["apple","banana","mango"]
console.log(array.length) 
//결과 3이 나옴, 배열에 아이템이 총 3개라서
```
