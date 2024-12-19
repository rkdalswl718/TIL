# [문제해결 03-01] 오버로딩

## 오버로딩

- 메서드도 변수와 마찬가지로 같은 클래스 내에서 서로 구별될 수 있어야 하기 때문에 각각 다른 이름을 가져야 함.
- 자바에서는 한 클래스 내에 이미 사용하려는 이름과 같은 이름을 가진 메서드가 있더라도 **매개변수의 개수 또는 타입**이 다르면, 같은 이름을 사용해서 메서들 정의 할 수 있다.
- **한 클래스 내에 같은 이름의 메서드를 여러 개 정의하는 것**을 **메서드 오버로딩**이라고 함

### 오버로딩의 조건

1. 메서드 이름이 같아야함!
2. 매개변수의 개수 또는 타입이 달라야 함.
- 반환타입은 오버로딩을 구현하는데 아무런 영향을 주지 않음.

## **println 메서드**

- 호출할 때 매개변수로 지정하는 값의 타입에 따라서 호출되는 println 메서드가 달라짐
- 예시) PrintStream 클래스
    - `println()`  매개변수 없을때, 개행문자 출력
    - `println(boolean x)` 불리언타입 변수 x 출력
    - `println(char x)` 문자타입 변수 x 출력
    - `println(char[] x)` 문자 배열 변수 x 출력
    - `println(Object x)` 객체 변수 x 출력
    - `println(String x)` 문자열 변수 x 출력
    - 등등…

예시

1. `int add(int a, int b) {}`

`long add(int a, int b) {}`

1.  `int add(int a, int b) {}`

`long add(int a, int b) {}`

1. `long add(int a, long b) {}`

`long add(long a, int b) {}`

1. `int add(int a, int b) {}`

`long add(long a, long b) {}`

`long add(int [] a) {}`

**⭐️ 같은 일을 하지만 매개변수를 달리해야하는 경우에 이와 같이 이름은 같고 매개변수를 다르게 하여 오버로딩을 구현함.**

### **사용하는 이유?**

- 메서드도 변수처럼 단지 이름만으로 구별된다면, 한 클래스내의 모든 메서드들은 이름이 달라야함 → 비효율적!!!!!!!
- println(){} printboolean(){} printstring(){} printObject() {} ..
- 근본적으로는 같은 기능을 하는 메서드들이지만 서로 다른 이름을 가져야 하기 때문에 메서드를 작성하는 쪽에서 이름을 짓기도 어렵고, 사용하는 쪽에서는 이름을 일일이 구분해서 기억해야하기 때문에 서로 부담됨
- 여러 메서드들이 println이라는 하나의 이름으로 정의될 수 있다면 기억하기도 쉽고 오류의 가능성 줄일 수 있음
- 메서드의 이름만 보고도 '이 메서드들은 이름이 같으니, 같은 기능을 하겠구나'라고 예측 가능
- 메서드의 이름을 절약할 수 있음, 메서드의 이름을 짓는데 고민을 덜 수 있는 동시에 사용되었어야 할 메서드 이름을 다른 메서드의 이름으로 사용할 수 있기 때문

걍 결론 : 효율적이고 알아보기 쉬우니까 써라

```jsx
class OverloadingTest {
	public static void main(String args[]) {
		MyMath3 mm = new MyMath3();
		System.out.println("mm.add(3, 3) 결과:"    + mm.add(3,3));
		System.out.println("mm.add(3L, 3) 결과: "  + mm.add(3L,3));
		System.out.println("mm.add(3, 3L) 결과: "  + mm.add(3,3L));
		System.out.println("mm.add(3L, 3L) 결과: " + mm.add(3L,3L));

		int[] a = {100, 200, 300};
		System.out.println("mm.add(a) 결과: " + mm.add(a));
   }
}

class MyMath3 {
	int add(int a, int b) {
		System.out.print("int add(int a, int b) - ");
		return a+b;
	}
	
	long add(int a, long b) {
		System.out.print("long add(int a, long b) - ");
		return a+b;
	}
	
	long add(long a, int b) {
		System.out.print("long add(long a, int b) - ");
		return a+b;
	}

	long add(long a, long b) {
		System.out.print("long add(long a, long b) - ");
		return a+b;
	}

	int add(int[] a) {		// 배열의 모든 요소의 합을 결과로 돌려준다.
		System.out.print("int add(int[] a) - ");
		int result = 0;
		for(int i=0; i < a.length;i++) {
			result += a[i];
		}	
		return result;
	}
}
```

## **가변인자와 오버로딩**

- 기존에는 매개변수 개수가 고정적이었으나 5버전부터 동적으로 지정해 줄 수 있게 되었으며 가변인자라고 함
- '타입... 변수명' 형식으로 선언
- 문자열 결합 함수
- 메서드 안에서 배열로 처리됨.
- `String concat(String s1, String s2) {}`
- `String concat(String s1, String s2, String s3) {}`
- `String concat(String s1, String s2, String s3, String s4) {}`
- **⭐️`String concat(String ...str)`**