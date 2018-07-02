# 배열과 배열 처리

- 배열이 사용되는 경우
	- 타입의 데이터를 연속된 공간에 저장
	- 각 데이터 저장위치는 인덱스를 부여해서 접근 하고 싶을 때 사용

- 배열의 장점
	- 단일 데이터(Single data)가 아닌 다수의 데이터(Multiple data) 저장
	- 연관있는 데이터를 함께 변수에 저장하므로 데이터를 찾는데 용이

## 배열 요소 조작

- 배열의 처음이나 끝에서 요소 하나를 추가하거나 제거하기 **(push, pop)**
	- **push** : 배열의 끝에 요소를 추가한다.
	```js
	var arr = ["apple","banana","orange"],
			push = arr.push("grape");
	
	console.log(arr); // ["apple","banana","orange","grape"]
	```

	- **pop** : 배열의 마지막 요소를 제거한다.
	```js
	var arr = ["apple","banana","orange","grape"],
			pop = arr.pop();
	
	console.log(arr); // ["apple","banana","orange"]
	```

- 배열의 끝에 여러 요소 추가하기 **(concat)**
	- 다수의 배열을 하나로 합치고, 병합된 배열을 반환한다.
	```js
	var arr1 = [1,2,3];
	var arr2 = [4,5,6];
	var arr3 = [7,8,9];

	var array = arr1.concat(arr2, arr3);
	console.log(array); // 1,2,3,4,5,6,7,8,9
	```
- 배열 일부 가져오기 **(slice)**
	- `arr.slice(start, end)`
	```js
	var arr = [ 'One', 'Two', 'Three', 'Four', 'Five', 'Six' ],
			slice = arr.slice( 1, 4 );
	console.log( slice ); // Two, Three, Four
	```

	```js
	var arr = [ 'One', 'Two', 'Three', 'Four', 'Five', 'Six' ],
			slice = arr.slice(2);
	console.log( slice ); // Three, Four, Five, Six
	```

	- 값이 음수면 마지막 요소를 기준으로 선택
	```js
	var arr = [ 'One', 'Two', 'Three', 'Four', 'Five', 'Six' ],
			slice = arr.slice(-4, -1);
	console.log( slice ); // Three, Four, Five
	```
- 임의의 위치에 요소 추가하거나 제거하기 **(splice)**
- 배열 안에서 요소 교체하기 **(copyWithin - es6 도입)**
- 특정 값으로 배열 채우기 **(fill - es6 도입)**
- 배열의 정렬 **(sort)**
	- 모든 원소를 문자열로 취급해 정렬하기 때문에 비교 함수를 직접 만들어서 정렬 로직을 구현해야 한다.
	```js
	var numbers = [10,9,8,7,6,5,4,3,2,1];

	numbers.sort(function(a,b){
		return a-b;
	});

	console.log(numbers); // 1,2,3,4,5,6,7,8,9,10
	```
- 배열의 역순 정렬 **(reserse)**

## 배열 검색

- **indexOf**
- **lastIndexOf**
- **findIndex**
- **findLastIndex**
- **some**
	- 배열 요소 중에서 하나라도 특정 조건을 만족하는지 알고 싶을 때 사용한다.
	- some 은 일부만 만족해도 true를 return 한다.
	```js
	var data = [1, 2, 3, 4, 5];
	var num = data.some(function (val) {
		return val % 2 != 0;
	});

	console.log(num); // true
	```

- **every**
	- 배열의 모든 요소가 특정 조건을 만족하는지 알고 싶을 때 사용한다.
	- every 가 배열의 모든 값이 조건을 만족해야 true를 return 한다.
	```js
	var data = [1, 2, 3, 4, 5];
	var num = data.every(function (val) {
		return val % 2 != 0;
	});

	console.log(num); // false
	```

## **map**과 **filter**

- **map**
- **filter**

## 배열의 마법 **reduce**

- **reduce**

## 삭제되거나 정의되지 않는 요소들

## 문자열 병합

- **Array.prototype.join**
