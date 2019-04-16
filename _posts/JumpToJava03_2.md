# 입출력
## 파일입출력
파일을 이용한 입출력 방법을 알아보자

### 파일 읽기
```java
byte[] b = new byte[1024];
FileInputStream input = new FileInputStream("경로");

int.read(b);
System.out.println(new String(b));
input.close();
```
하지만 위에처럼 하면 딱 1024바이트만 읽기때문에 정확한 길이를 모를 경우는 불편하다

#### 파일을 라인단위로 읽어보자!
```java
BufferedReader br new BufferedReader(new FileReader("경로"));
while(true){
  String line = br.readLine();
  if(line == null) break;
  System.out.println(line);
}
br.close();

```

### 파일쓰기

#### byte단위로 데이터 처리
```java
FileOutputStream fout = new FileOutputStream("경로");
fout.close();
```
FileOutputStream은 String을 byte배열로 바꾸어주는 getBytes()메소드를 이용해야하는 불편함이 있다

#### byte배열 대신 문자열을 직접
```java
FileWriter fw = new FileWriter("경로");
fw.close();
```
하지만 \r\n을 문자열끝에 덧붙여줘야하는 불편함 발생

#### \r\n을 덧붙여줌
```java
PrintWriter pw = PrintWriter9'경로")
for(int i = 1; i<11; i++) {
  String data = i+"번째 줄입니다,";
  pw.println(data);
}
pw.close();
```

