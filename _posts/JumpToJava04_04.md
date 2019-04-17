# 자바에 날개를 달자
## 에외처리
유연한 프로그래밍을 위한 예외처리

FoolException.Java
```java
public class FoolException extends RuntimeException{
  /*
  * RuntimeException : 실행 시 발생하는 예외
  * Exception : 컴파일 시 발생하는 예외
  * 즉 Exception은 프로그램 작성 시 이미 에측가능한 예외를 작성할 떄 사용하고
  * RuntimeException은 발생 할수도 발생 안 할수도 있는 경우 작성.
  *
  * 다른말로
  * Exception을 Checked Exception
  * RuntimeException을 UnChecked Exception이라고도 한다.
 * /
}
```

TestException
```java
public class TestException {
  public void shouldBeRun() {
    System.out.println("ok thanks.");
  }
  // throws라는 구문을 이용하여 예외를 뒤로 미루기
  public void sayNick(String nick) throws FoolException {
    if("fool".equals(nick)) {
      throw new FoolException();
    }
    System.out.println("당신의 별명은 "+nick+"입니다,");
  }
  
  public static void main(String[] args) {
    TestException test = TestException();
    int c;
    try {
      c = 4/0;
    } catch (ArithmeticException e) {
    } finally {
      test.shouldBeRun();
    }
    try {
      test.sayNick("fool");
      test.sayNick("geniuous");
    } catch (FoolException e) {
      System.out.println("Foolexception이 발생했습니다.");
    }
  }
}
```

정리
```java
try {
 //실행구간
} catch (ArithmeticException e) {
 //예외가 발생하면 예외에 해당되는 catch문이 수행
} finally {
  //예외가 발생하더라도 반드시 실행되어야 하는 부분
}
```

FoolException처리를 sayNick메소드에서 하는것이 좋을까?
아니면 main메소드에서 하는것이 좋을까?

- sayNick메소드에서 예외를 처리하는 경우
test.sayNick("fool"); ; FoolException이 발생 후
그 다음 문장인 test.sayNick("geniuous");이 수행

하지만 main메소드에서 처리를 한 경우
test.sayNick("fool");에서 이미 예외가 발생하여
catch로 바져버리기 때문에
test.sayNick("geniuous");이 수행되지 않음.
 
`트랜잭션` 하나의 작업 단위
트랜잭션 관리를 잘해야한다.
예외처리를 할때 부분만 알아서는 안되고 전체를 관통하여
모두 알아야만 정확히 할 수 있다

`점프투자바 예외처리 마지막 부분`
