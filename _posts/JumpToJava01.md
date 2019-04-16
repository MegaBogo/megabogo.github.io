# 3,자료형

## Number
1. 정수
2. 실수
8. 8진수와 16진수
4. 숫자연산
5. 증감연산

## boolean
1. true / false

## char
- 한 개의 문자 값에 대한 자료형
문자값을 '(단일 인용부호)로 감싸주어야 한다는 점

## String
```Java
String a = "Happy Java";
String b = new String("Happy Java"); 
```
보통 문자열을 표현할 때는 가급적 리터럴(literal)방식을 사용하는 것이 좋다.
그 이유는 가독성에 이점, 컴파일 시(new생성으로 객체가 2번 생성되지 않음) 최적화에 도움을 줌

```Java
StringBuffer sb = new StringBuffer();
sb.append("hello");
sb.append("~~~");
sb.append('Jumb to Java");
```

StringBuffer 자료형은 String자료형보다 무거운 편.
String을 사용하는 것보다 메모리 사용량도 많고 속도도 느림.
따라서 문자열 추가나 변동등의 작업이 많은 경우에는 StringBuffer 
문자열 변경 작업이 거의 없는 경우는 String사용하는 것이 유리하다.

## Array
### 배열이란 자료형의 종류가 아닌 자료형의 집합이다.
```Java
int[] odds = {1,3,5,9};
String[] weeks = {"월","화","수","목","금","토","일"};
```

### 배열변수를 만들때에는 반드시 길이값이 필요하다
```Java
//길이가 없으므로 컴파일 오류 발생
String[] weeks = new String[];
```

### 배열의 값 접근은 인덱싱을 이용
 ```Java
 int[] odds = {1,3,5,9};
 System.out.println(odds[2]);
 ```
 
 ### 배열길이 값이 없는 경우 발생하는 오류
 ```Java
 //ArrayOutOfBoundsException`
 String[] weeks = new String[7];
 weeks[8] = "끝";
 ```

## List
리스트는 배열과 비슷한 자바의 자료형으로 배열보다 편리한 기능을 가지고 있다.
배열의 크기는 정해져 있다
배열의 크기를 명확하게 알 수 있는 경우도 있지만 알 수 없는 경우도 있다.

List는 동적으로 자료형의 갯수가 가변할때 유용하다.

### List컬렉션 클래스에 속하는 클래스는 다음과 같다.
```Java
ArrayList<String> arrayList = new ArrayList<>();
LinkedList<String> linkedList = new LinkedList<>();
Vector<String> vector = new Vector<>();
Stack<String> stack = new Stack<>();
```
Vector : 동기화 기능이 제공되는 가변이 가능한 자료 구조
ArrayLikst : 동기화가 제공되지 않음. 데이터 검색에 유리하며 추가,삭제는 성능을 고려
LinkedList : ArrayList에 비해 데이터의 추가, 삭제에 유리하며 데이터 검색 시에는 성능을 고려
[자료구조 LinkedList VS ArrayList에 대한 포스팅](https;//www.nextree.co.kr/p6506)

```Java
ArrayList<String> pitches = new ArrayList<>();

//Add
pitches.add("121");
pitches.add("129");
pitches.add("125");

//Get
pitches.get(1);

//Size
pitches.size();

//Contains
pitches.contains("129");

//Remove
pitches.remove(0);
pitches.remove("129");

```

