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
