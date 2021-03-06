# 자바의 날개 달기
## 정적 변수와 메소드 (static)
```
static키워드를 붙이면 자바는 메모리 할당을 딱 한번만 하게 되어
메모리 사용에 이점을 볼 수 있게 된다.

static을 사용하는 또 한가지 이유로 공유의 개념을 들 수 있다.
static으로 설정하면 같은 곳의 메모리 주소만을 바라보기 때문에
변수의 값을 공유하게 되는 것이다.

스태틱 변수는 스태틱 메소드로 접근이 가능하다.
스태틱 메소드 안에서는 인스턴스 변수 접근이 불가능하다.

보통 스태틱 메소드는 유틸리티 성 메소드를 작성할 때 많이 사용된다.
예를 들어 "오늘의 날짜 구하기", "숫자에 콤마 추가하기"등의 메소드를 작성할 때에는
클래스 메소드를 사용하는 것이 유리하다.
```


```java
public class Counter {
  static int staticCount = 0;
  int count = 0;
  
  Counter() {
    this.staticCount++;
    this.count++;
  }
  public int getCount() {
    return count;
  }
  public static int getStaticCount() {
    return staticCount;
  }
  public static void main(String[] args) {
    Counter c1 = new Counter();
    
    System.out.println(c1.getCount());
    System.out.println(Counter.getStaticCount());
    
    Counter c2 = new Counter();
    
    System.out.println(c2.getCount());
    System.out.println(Counter.getStaticCount());
  }
}
```
