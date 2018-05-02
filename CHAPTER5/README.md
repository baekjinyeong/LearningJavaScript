# 표현식과 연산자

`결과를 명시적으로 반환하는 것이 표현식 이다.`

표현식은 **값**이 된다. 그 결과를 다른 표현식에 결합해서 다른 값을 얻을 수 있다. 

그 값을 또 다른 표현식에 결합해서 또 다른 값을 얻는 식으로 이어질 수 있다. 

표현식이 아닌 문은 이런식으로 결합할 수 없다. 

**표현식은 값이 되므로 할당에 쓸 수 있다.**

즉 표현식의 결과를 변수나 상수, 프로퍼티에 할당할 수 있다.

```js
let x;
x = 3 * 5; // 곱셈표현식 3*5 = 15, 할당표현식 x = 3*5 
```

표현식은 대부분 연산자표현식이다.

값이 되는 것은 모두 표현식이므로, **변수와 상수, 리터럴**도 모두 표현식이다.


# 1. 연산자

표현식이 값이 되는 것 이라면 연산자는 **값을 만드는 행동** 이다.
> **Tip:** 연산자는 하나 이상의 피연산자가 있어야 결과를 낼 수 있다. ex) 1 + 2


# 2. 산술연산자

 - 단항플러스 (+X //X가 숫자가 아니면 숫자로 변환을 시도)
```js
const s;
const y = 3 + +s; 
// y는 8, 단항플러스(+)를 사용하지 않았다면, 
// 문자열 병합으로 인해 값이 "35"가 된다.
```
- 단항부정 (-X //X의 부호를 바꾼다. X가 5이면 -X는 -5이다.)
```js
const x = 5;
const y = 3 - -x;  // y는 8
```
- 전위증가, 전위감소 ( ++X, --X //X에서 1을 더하거나 뺀 다음 평가한다.)
- 후위증가, 후위감소 ( ++X, --X //X의 값을 평가한 다음 1을 더하거나 빼준다.)
```js
let x = 2;
const r1 = x++ + x++; // 결과 2 + 3 = 5, x = 4
const r2 = ++x + ++x; // 결과 5 + 6 = 11, x = 6
```
```js
let y = 10;
const r3 = y-- + y--; // 결과 10 + 9 = 19, y = 8
const r4 = --y + --y; // 결과 7 + 6 = 13, y = 6
```
> **Tip:** 증가와 감소 연산자는 덧셈보다 먼저 실행된다.


# 3. 연산자 우선순위
- 연산자의 우선순위가 높을수록 먼저 실행된다.
- 연산자 우선 순위에 따라 결정된 계산 순서를 바꾸려면 괄호를 사용한다.
- 우선순위가 같은 연산자들은 오른쪽에서 왼쪽으로 또는 왼쪽에서 오른쪽으로 평가한다.

```js
var num = 10;

if(5 == num / 2 && (2 + 2 * num).toString() === "22") {
    document.write(true);
}
    // Output:
    // true
```


# 4. 비교연산자
비교연산자는  `일치함(===), 동등함(==), 대소관계` 의 세 가지 타입으로 나뉜다.
 
 - 일치함 
	 - 두 값이 같은 객체를 가리키거나, 같은 타입이고 값도 같다면 값이 일치한다고 함
	 - `두 값이 일치할 경우 (===), 그 반대인 경우 (!==)`
  - 동등함
	 - 두 값이 같은 객체를 가리키거나 같은 값을 갖도록 변환할 수 있다면 동등하다고 함
	 - 문자열 "33"은 숫자 33으로 **변환할 수 있으므로 동등**하지만, 
	    **타입이 다르므로 일치하지 않는다.**
     - `두 값이 동등할 경우 (==), 그 반대인 경우 (!=)`
 
```js
const n = 5;
const s = "5";

n === s; // false
n !== s; // true
n == s; // true
n != s; // false

const a = {name: "an object"};
const b = {name: "an object"};

a === b; // false , 객체는 항상 다르다.
```


# 5. 숫자비교
> **caution:**
특별한 숫자형 값 NaN은 그 자신을 포함하여 무엇과도 같지 않다.

즉 NaN === Nan , Nan == NaN은 모두 false이다.


# 6. 문자열 병합
```js
3 + 5 + "8" 
// 문자열 "88"이 된다.
// 3 + 5 를 덧셈으로 판단 , 8 + "8" 을 문자열 병합으로 판단
 
"3" + 5 + 8 
// 문자열 "358"이 된다.
// "3" + 5 를 병합으로 판단, "35" + 8 또한 병합으로 판단
```

# 7. 참 같은 값과 거짓 같은 값
자바스크립트에서는 모든 데이터 타입을 참 같은 값과 거짓 같은 값으로 나눌 수 있다.

**거짓같은 값**

 - undefined
 - null
 - false
 - 0
 - NaN
 - ' ' (빈 문자열)
 
 **참 같은 값**
 
 - 모든 객체, value() 메서드를 호출했을 때 false를 반환하는 객체도 참 같은 값에 속한다.
 - 배열, 빈 배열도 참 같은 값에 속한다.
 - 공백만 있는 문자열 (" " 등)
 - 문자열 "false"

# 8. AND, OR, NOT

- 8.1 단축평가
    - 자바스크립트에서는 단축평가가 일어납니다.
    - x의 값이 false라면 x && y의 값은 y에 상관없이 false를 가지게 된다.
    - 두 값을 모두 평가하지 않아도 될 때에 단축평가가 일어난다.
    - 단축평가가 일어나면 확인할 필요가 없는 피연산자에 부수효과가 있더라도 효과가 발생하지 않는다.

```js
const foo = true; // 첫번째 피연산자
let bar = 0;
const result = foo || bar++; // 단축평가가 일어남
// 세번째 행에서 단축평가가 일어나므로, result값은 true가 된다.
```

- 8.2 피연산자가 불리언이 아닐 때 논리 연산자가 동작하는 방법
    - 객체는 항상 참 같은 값으로 평가된다. 따라서 suppliedOptions가 객체이면 options는 suppliedOptions를 가리키게 된다.
    - 옵션이 제공되지 않으면, 즉 suppliedOptions가 null 이나 undefined라면 options는 기본값을 갖게된다.
```js
 const options = suppliedOptions || {name: "Defult"}
```

- 8.3 삼항연산자
    - 세 개의 피연산 함수를 취할 수 있는 유일한 자바스크립트 연산자이다.
    - if 문의 축약형으로 빈번히 사용된다.
    - 삼항 연산자는 if / else 문을 사용하는 함수를 반환하는 데 적합하다.
    - 다중 삼항(ternary) 평가도 가능하다.
```js
function getFee(isMember) {
  return (isMember ? "$2.00" : "$10.00");
}
```

```js
// 다중 삼항(ternary)
var firstCheck = false,
    secondCheck = false,
    access = firstCheck ? "Access denied" : secondCheck ? "Access denied" : "Access granted";

    // "Access granted"
```

```js
var now = new Date();
var greeting = "Good" + ((now.getHours() > 17) ? " evening." : " day.");

// 현재 시각이 오후 6시 이후이면 이 예제는 "Good evening."이라는 문자열을 만든다.
```

- 8.4 쉼표연산자
    - 쉼표연산자는 표현식을 결합하여 두 표현식을 평가한 후, 두번째 표현식의 결과를 반환한다.
    - for 루프의 증분 식에서 가장 일반적으로 사용
    - , 연산자를 사용하면 여러 개의 식이 한 개의 식으로 처리되므로 두 변수 모두 증가할 수 있다.

```js
let x = 0, y = 10, z;
z = (x++, y++)

// x 와 y는 모두 1만큼 늘어났지만, z의 값은 10이다. 이 값은 y++ 가 반환한 값이다.
// 쉼표연산자는 우선순위가 가장 낮은 연산자이므로 괄호를 사용.
```

```js
j=25;
for (i = 0; i < 10; i++, j++)
{
   k = i + j;
}
```

# 9. 연산자 그룹

- 9.1 typeof연산자
    - `typeof operand 또는 typeof (operand)`
    - typeof 연산자는 피연산자의 타입을 나타내는 문자열을 반환한다.  
    - `operand` 는 어떤 타입인지 반환될 문자열, 변수, 키워드,또는 객체이다. (괄호 표현은 선택사항)

```js
var myFun = new Function("5 + 2");
var shape = "round";
var size = 1;
var today = new Date();

// typeof 연산자는 이 변수들에 대하여 다음과 같은 값을 반환

typeof myFun;     // returns "function"
typeof shape;     // returns "string"
typeof size;      // returns "number"
typeof today;     // returns "object"
typeof dontExist; // returns "undefined"
```

# 10. 해체 할당
- 객체나 배열을 변수로 해체 할 수 있다.
- 배열의 값이나 객체의 속성을 별개의 볕수로 추출할 수 있게 하는 자바스크립트 식이다.
- 다른 곳에서 가져온 객체나 배열에서 원하는 요소를 뽑아내야 할 때 나타난다.

- 객체해체
    - 객체를 해체할 때는 반드시 변수 이름과 객체의 프로퍼티 이름이 일치해야 한다.

```js
// 객체선언
const obj = {b: 2,c: 3,d: 4};

// 해체할당
const {a,b,c} = obj;
a; // undefined: obj에는 "a" 프로퍼티가 없다.
b; // 2
c; // 3
d; // ReferenceError: "d"는 정의되지 않았다.
```

- 객체 해체는 할당만으로 이뤄질 수도 있지만, 그렇게 하려면 반드시 괄호를 써야한다.
```js
const obj = {b: 2,c: 3,d: 4};
let a,b,c;

// 에러
{a,b,c} = obj;

// 동작
({a,b,c} = obj);
```

- 새로운 변수 이름으로 할당할 수 있다.
```js
const o = {p: 42, q: true};
const {p: foo, q: bar};

foo; // 42
bar; // true
```

- 배열해체

- 배열을 해체할 때 변수 이름을 마음대로 쓸 수 있으며, 이들은 배열 순서대로 대응한다.
```js
// 배열선언
const arr = [1,2,3];

// 베열 해체 할당
let [x,y] = arr;
x; // 1
y; // 2
z; // ReferenceError : "z"는 정의되지 않았다.

// x 는 첫번째 요소값을, y는 두번째 요소값을 할당.
// 그 뒤의 요소는 모두 버려진다.
```

```js
// 배열선언
const arr = [1,2,3,4,5];
let [x,y, ...rest] = arr;
x; // 1
y; // 2
rest; // [3,4,5]

// 확산연산자(...)를 사용하면 남은 요소를 새 배열에 할당할 수 있다.
```

- 배열해체를 활용하면 변수의 값을 서로 바꿀 수 있다.
```js
// 배열선언
let a = 5, b = 10;
[a, b] = [b, a];
a; // 10
b; // 5
```

- 함수가 배열을 반환하는 경우에 해체할당된 배열 값을 통해 작업을 간결하게 할 수 있다.
```js
function f(){
    return [1,2];
}

// 배열해체
var a, b;
[a, b] = f();
a; // 1
b; // 2
```

# 11. 템플릿 문자열과 표현식

- 템플릿 문자열을 생성하려면 작은따옴표나 큰따옴표 대신에 역따옴표(`)를 사용하여 문자열을 묶는다.
- $ 문자는 템플릿 문자열 내에서 자리 표시자를 지정하는 데 사용된다.
- 전달되는 원시 문자열 값에 액세스해야 할 경우 태그가 지정된 템플릿 함수에 전달된 첫 번째 인수는 전달된 문자열의 원시 문자열 형식을 반환하는 raw 속성을 지원한다.

```js
function buildURL(strArray, ...valArray) {  
    console.log(strArray.raw);  
}  

var lang = "en-us";  
var a = "library";  
var b = "dn771551.aspx";  

// Call the tagged template function.  
var url = buildURL`http://msdn.microsoft.com/${lang}/${a}/${b}`;

// Ouput:
// http://msdn.microsoft.com/library/dn771551.aspx
```

# 12. 표현식과 흐름 제어 패턴

- 12.1 if...else 문을 3항 연산자로 바꾸기

```js
if(isPrime(n)){
    label = 'prime';
} else {
    label = 'non-prime';
};

// 3항 연산자로 바꾸기
label = isPrime(n) ? 'prime' : 'none-prime';
```

```js
var func1 = function( .. ) {
  if (condition1) { return value1 }
  else if (condition2) { return value2 }
  else if (condition3) { return value3 }
  else { return value4 }
}

// 3항 연산자로 바꾸기
var func2 = function( .. ) {
  return condition1 ? value1
       : condition2 ? value2
       : condition3 ? value3
       :              value4
}

// if / else 문을 대체하는 삼항연산자가 return을 여러 번 사용하고 if 블록 내부에서 한줄만 나올때 return을 대체 할 수 있는 좋은 방법이된다.
```

- 12.2 if 문을 단축평가하는 OR 표현식으로 바꾸기

```js
if(!options) options = {};

// 단축평가
options = options || {};
```