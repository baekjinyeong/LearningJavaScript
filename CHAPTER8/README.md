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
	- arr.slice(start, end)
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
	- arr.splice(start, b, item, item...);
	- start 위치에서 지정된 수만큼(b) 요소를 제거하고, 새 요소를 삽입(item)한다.
	```js
	var arr = ["4", "11", "2", "10", "3", "1"];
			arr.splice(2, 2, "21", "31");
	
	console.log(arr); // 4, 11, 21, 31, 1
	```
- 배열 안에서 요소 교체하기 **(copyWithin - es6 도입)**
	- arr.copyWithin(target, start, end)
	- 배열의 일부를 복사한 뒤, 동일한 배열의 다른 위치에 덮어쓰기 한 다음, 배열 자신을 반환한다.
	-	배열의 길이는 변하지 않음
	```js
	var arr = [1, 2, 3, 4, 5];

	console.log(arr.copyWithin(-3, 0, -1)); // [1, 2, 1, 2, 3]
	```

	```js
	var arr = [ 1, 2, 3, 4, 5, 6, 7 ];

	console.log(array.copyWithin(0, 3, 6)); // [4, 5, 6, 4, 5, 6, 7]
	```
- 특정 값으로 배열 채우기 **(fill - es6 도입)**
	- arr.fill (value, start, end)
	- start 와 end 매개변수는 선택사항이며 기본값은 0 과 지정한 배열객체의 길이값이다.
	- 만약 start 매개변수가 음수이면, start 의 값은 배열의 길이값을 합한 결과가 시작지점이다.
	- 만약 end 가 음수라면, end 매개변수와 배열의 길이값을 합한 결과가 종료지점이다.
	- 새 배열을 반환하지 않는다. 대신에이 함수가 적용된 배열을 수정한다.
	```js
	var arr = [1, 2, 3];
	arr.fill(4); // [4,4,4]
	```
	```js
	var arr = [1, 2, 3];
	arr.fill(4, 1, 2); // [1, 4, 3]
	```
	```js
	var arr = [1, 2, 3];
	arr.fill(4, -3, -2) // [4, 2, 3]
	```
- 배열의 정렬 **(sort)**
	- 모든 원소를 문자열(유니코드)로 취급해 정렬하기 때문에 비교 함수를 직접 만들어서 정렬 로직을 구현해야 한다.
	```js
	var numbers = [10,9,8,7,6,5,4,3,2,1];

	numbers.sort(function(a,b){
		return a-b;
	});

	console.log(numbers); // 1,2,3,4,5,6,7,8,9,10
	```
- 배열의 역순 정렬 **(reverse)**
	```js
	var arr = [0, 1, 2, 3, 4];
	var reverse = arr.reverse();

	console.log(arr); // 4, 3, 2, 1, 0
	```

## 배열 검색

- **indexOf**
	- 찾고자 하는 것과 정확히 일치(===) 하는 첫번째 요소의 인덱스를 반환한다.
	- 일치하는 값을 찾지 못하면 -1을 반환한다.
- **lastIndexOf**
	- 배열에서 뒤에서 부터 지정된 요소를 찾아 첫 번째 인덱스를 반환한다.
	- 일치하는 값을 찾지 못하면 -1을 반환한다.
- **findIndex**
	- 함수에 지정된 테스트 조건을 충족하는 첫 번째 배열 요소의 인덱스 값을 반환한다.
	- true를 반환할 때까지 배열의 각 요소에 대해 한 번씩 오름차순으로 함수를 호출한다.
	- true를 반환하는 배열의 요소가 없는 경우 findIndex에서 -1을 반환한다.
	```js
	function arr(element) {
		return element >= 15;
	}
	[12, 5, 8, 130, 44].findIndex(arr); // 3
	```
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
- 원본 배열은 건들지 않고, 그 값들만을 사용하거나 약간 변형해서 새로운 배열을 만들어야할 필요가 있을 때 유용하다.

- **map**
	- 배열 전체를 돌며 배열값을 사용해서 "또다른 배열"을 만들고 싶을 때 적합하다.
	- 요소를 일괄적으로 변경하는데 효과적이다.
	- 일정한 형식의 배열을 다른 형식으로 바꿔야 할 때 사용한다.
	- 콜백 함수의 리턴을 모아서 새로운 배열을 만드는 것이 목적이다.
	``` js
	var testArray = ["aaa", "bbb", "ccc", "ddd"];

	var newArray = testArray.map(function (item, index, array) {
		return item + "NEW";
	}); // 배열의 모든 요소에 NEW라는 문자열을 더하기, 리턴값은 새로운 배열

	console.log(testArray); // ["aaa", "bbb", "ccc", "ddd"] 원본 배열

	console.log(newArray); // ["aaaNEW", "bbbNEW", "cccNEW", "dddNEW"] 생성된 배열
	```
- **filter**
	- 배열에서 필요한 것들만 남길 목적으로 만들어졌다.
	- 삭제됐거나 값이 할당된 적이 없는 인덱스에 대해서는 호출되지 않는다.
	```js
	var arr = [12, 5, 8, 130, 44];

	function filterArray(value) {
		return value >= 10;
	}
	var filter = arr.filter(filterArray);
	console.log(filter); // [12, 130, 44]
	```

## 배열의 마법 **reduce**

- **reduce**

## 삭제되거나 정의되지 않는 요소들

## 문자열 병합

- **Array.prototype.join**
	- 배열의 모든 요소를 연결해 하나의 문자열로 만든다.
	```js
	var arr = ["A", "B", "C"];
	var number = 2;
	var number2;

	arr.push(number);

	number2 = arr.join();
	console.log(number2); // A,B,C,2
	```

	```js
	var arr = ["A", "B", "C"];
	var number = 2;
	
	arr.push(number);
	console.log(...arr); // ["A", "B", "C", 2]
	```
