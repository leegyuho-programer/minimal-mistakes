---
layout: post
title:  "Re JS 2일차"
---

객체
```javascript
배열은 []를 사용
객체는 {}를 사용

let patient = {
  name : "jimin,
  age : 17,
  disease : "cold"
}

console.log(patient)
//결과 { name : "jimin", age : 17, disease : "cold"}

console.log(patient.name)
//결과 jimin (key값을 이용하여 값에 접근할 수 있다.)

console.log(patient["name"])
//결과 jimin

patient.name = "jk"
console.log(patient)
//결과 { name : "jk", age : 17, disease : "cold"}

patient["name"] = "jk"
console.log(patient)
//결과 { name : "jk", age : 17, disease : "cold"}

//key값 : name, age, disease
//value : jimin, 17, cold


let patientList = [{name: "jimin", age: 13}, {name: "jk", age: 25}, {name: "jhope", age: 40}]
console.log(patientList)
//결과 [{name: "jimin", age: 13}, {name: "jk", age: 25}, {name: "jhope", age: 40}]

console.log("첫번째 환자는:", patientList[0])
//결과 - 첫번째 환자는: {name: "jimin", age: 13}
```
