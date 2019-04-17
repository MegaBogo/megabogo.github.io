# 3.자료형

## Number
1. 정수
1. 실수
1. 8진수와 16진수
1. 숫자연산
1. 증감연산

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

for(String s : pitches) {
 System.out.println(s);
}
```

## Generics (제네릭스)
자바 J2SE 5.0 이후에 도입된 개념

```Java
ArrayList<String> aList = new ArrayList<String>();
ArrayList aList = new ArrayList();
```
두개의 차이는 자료형 타입 바로 옆에 <E>이 잇느냐 없느냐의 차이.
제네릭스를 이용하면 좀 더 명확한 타입체크가 가능하다.
 
 ### 제네릭스를 사용하지 않는 경우 
 ```Java
 ArrayList aList - new ArrayList();
 aList.add("hello");
 aList.add('java");
 
 String hello = (String) aList.get(0); 
 ```
 
 ### 제네릭스를 사용했을 경우
```Java
ArrayList<String> aList = new ArrayList<>();
aList.add("java");
String java = aList.get0);
```

#### 제네릭스를 사용했을때와 안했을때의 차이
제네릭스를 사용하지 않을 경우에 ArrayList안에 추가 도는 객체는 Object자료형으로 인식한다.
참고고로 Object자료형은 모든 객체가 상속하고 있는 가장 기본적인 자료형
그렇기 때문에 제네릭스를 사용하지 않을 경우 값을 넣을 때는 문제가 되지 않는다.
하지만 값을 가져오는 경우에는 항상 형변환을 해 주어야 한다.
또한, 선언한 String외에 다른 객체도 넣을 수 있기 때문에,
형변환 과정에서 잘못된 형변환으로 인한 오류가 발생할 소지가 있다.

이러한 점이 제네릭스의 탄생 이유이기도 하다
제네릭스로 자료형을 선언하기만 하면 그 이후로는 자료형에 대한
형변환 과정이 필요없다.
그 이유는 이미 컴파일러가 aList에는 반드시 String자료형만 추가 되어야 함을 알기 때문.

## Map
자바의 맵은 대응관계를 쉽게 표현할 수 있게 해주는 자료형이다.
["이름"="홍길동", "생일"="1212"]

자료형으로 Associative array, Hash라고 불린다.

맵은 사전과 비슷하다.
Map은 Key와 Value라는 것을 한 쌍으로 갖는 자료형이다.

맵은 리스트나 배열처럼 순차적으로(sequential) 해당 요소 값을 구하지 않고
Key를 통해 value을 얻어내기 때문에 순차적으로 모두 검색하는 것이 아니라
값이 있는 곳만을 펼쳐보는 것이다.


### put
map에 key와 value을 입력하기 위한 메소드
```
HashMap<String, String> map = new HashMap<>();
map.put('people", "사람"0;
```

### get
key에 해당되는 값을 얻기 위한 메소드
```
HashMap<String, String> map = new HashMap<>();
map.get("people");
```

### containsKey
map에 해당 key가 있는지에 따라 boolean값으로 리턴

```
HashMap<String, String> map = new HashMap<>();
map.containsKey("people");
```

### remove
key값에 해당되는 아이템(key, value)을 삭제 후 그 value값을 리턴
```
map.remove("people");
```

### size
size메소드는 Map의 갯수를 리턴
```
map.size();
```

### LinkedHashMap? TreeMap??
Map의 가장 큰 특징은 순서에 의존하지 않고 key로 value를 가져오는데 있다.
하지만 가끔은 Map에 입력된 순서대로 데이터를 가져오고 싶은 경우도 있고
때로는 입력된 Key에 의해 소트된 데이터를 가져오고 싶을 수도 있을 것 이다.

이런 경우에는 LinkedHashMap과 TreeMap을 사용하는 것이 유리하다.

LinkedHashMap : 입력된 순서대로 값을 출력해주는 특징
TreeMap : 입력된 Key의 소트순으로 데이터가 출력

```Java
LinkedHashMap<String, String> linkedHashMap = new LinkedHashMap<>();

linkedHashMap.put("a10", "zzz');
linkedHashMap.put("a41", "zzz');
linkedHashMap.put("a20", "zzz');
linkedHashMap.put("a40", "zzz');

for(String key : linkedHashMap.keySet()) {
  System.out.printf("%s:%s\n", key, linkedHashMap.get(key));
}

TreeMap<String, String> treeMap = new TreeMap<>();
treeMap.put("z11", "sdff");
treeMap.put("z01", "sdff");
treeMap.put("z31", "sdff");

for(String key : treeMap.keySet()) {
  System.out.printf("%s:%s\n", key, treeMap.get(key));
}
```
