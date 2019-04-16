# 입출력
## 콘솔 입출력
프로그램을 실행했더니 문자열이 출력되었다고 가정해보았을 때
사용자에게 문자열을 보여주는 것이 바로 콘솔 출력이다.

그러면 콘솔에서 사용자에게 입력을 받아보자

그전에 스트림을 먼저 이해하고 가자

### Stream
```
스트림이란?
스트림을 가장 쉽게 이해하려면 수도곡지를 생각하면 된다.
A라는 곳에서부터 B라는 곳까지 수도관이 연결되어 있고
A에서 계속 물을 보낸다면 B에서 수도꼭지를 틀때마다 물이 나오게 될 것이다.
여기서 스트림은 A수도관에서 B수도관으로 이동하는 물의 흐름이라고 할 수 있다.

프로그래밍에서는 다음과 같은 것들을 스트림이라고 할 수 있다.
파일데이터(파일은 그 시작과 끝이 있는 데이터의 스트림)
HTTP응답데이터(브라우저가 요청하고 서버가 응답하는 HTTP응답 데이터)
키보드 입력(사용자가 키보드로 입력하는 문자열은 스트림이다.)
```

### InputStream (바이트 스트림)
```Java
InputStream in = System.in;
int a;
a = in.read();
```
System.in을 통해 키보드를 입력받을 수 있다.
사용자가 'abc'을 입력하면 a라는 변수에는 97ㅇ라는 값이 들어간다.
왜 사용자는 "abc'을 입력했는데 97이라는 값이 나올까?


사용자는 "abc'라는 3byte의 데이터를 전달했지만 
read메소드는 1byte만 읽었기 때문에 a의 아스키코드값인 97이 출력되었다.

#### 그러면 사용자가 'abc'를 입력했을 때 3byte를 전부 읽고 싶다면?
```java
InputStream in = System.in;
byte[] a = new byte[3];
in.read(a);
System.out.println(a[0]);
System.out.println(a[1]);
System.out.println(a[2]);
```
읽어들인 값을 항상 아스키코드 값으로 해석해야하는 불편함이 발생.
문자값을 그대로 출력하려면??

#### 바이트 대신 문자로 입력 스트림을 읽어보자!
```java
InputStream in = System.in;
InputStreamReader reader = new InputStreamReader(in);
char[] a = char[3];
reader.read(a);
```
InputStreamReader로 byte배열 대신 char배열을 사용한다.
바이트 대신 문자로 입력 스트림을 읽었으나
고정된 길이로 스트림을 읽어야하는 불편함이 발생했다.

#### 사용자가 엔터키를 입력할 때 까지 사용자의 입력을 전부 받아들일 수 없을까?
```
InputStream in = System.in;
InputStreamReader reader = new InputStreamReader(in);
BufferedReader br = new BufferedReader(reader);
String a = br.readLine();
```

#### 정리!
```
InputStream - byte
InputStreamReader - character
BufferedReader - String
```
