# 3,자료형

## Number
1. 정수
2. 실수
8. 8진수와 16진수
4. 숫자연산
5. 증감연산

## boolean
1. true / false

##char
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
