# 자바에 날개를 달자
## Thread (쓰레드)
동작하고 있는 프로그램을 프로세스라고 한다.
보통 한 개의 프로세스는 한 가지의 일을 하지만
쓰레드를 이용하면 한 프로세스 내에서 두 가지 또는 그 이상의 일을 동시에 할 수 있다.

```java
public class TestThread extends Thread {
  int seq;
  public TestThread(int seq) {
    this.seq = seq;
  }
  public void run() {
    System.out.println(this.seq +"thread start.");
    try {
      Thread.sleep(300);
    } catch (Exception e) {
    
    }
    System.out.println(this.seq + "thread end.");
  }
  public static void main(String[] args) {
    for(int i = 0; i < 10; i++) {
      TestThread test = new TestThread(i);
      test.start();
    }
    System.out.println("main end.");
  }
}
```


### Thread Join
위에 예제를 실행하면 쓰레드가 끝나기도 전에 main end가 출력된다.
쓰레드가 종료된 후 main 메소드를 종료시키려면??
join()메소드를 이용하자.



```java
public class TestThread extends Thread {
  int seq;
  public TestThread(int seq) {
    this.seq = seq;
  }
  public void run() {
    System.out.println(this.seq +"thread start.");
    try {
      Thread.sleep(300);
    } catch (Exception e) {
    
    }
    System.out.println(this.seq + "thread end.");
  }
  public static void main(String[] args) {
    ArrayList<Thread> threads = new ArrayList<>();
    for(int i = 0; i < 10; i++) {
      TestThread test = new TestThread(i);
      test.start();
      //ArrayList threads에 쓰레드 생성시 설정된 객체를 저장.
      threads.add(t);
    }
    
    for(int i = 0; i<threads.size(); i++) {
      Thread t = threads.get(i);
      try {
        //join(()메소드는 쓰레드가 멈출때까지 기다리게 함.
        t.join();
      } catch (Exception e) {
      }
    }
    System.out.println("main end.");
  }
}
```

### Runnable인터페이스를 사용하여 Thread구현
THread를 extends하던 것에서 Runnable을 implements하도록 변경

```java
public class TestRunnable implements Runnable {
  int seq;
  public TestRunnable(int seq) {
    this.seq = seq;
  }
  @Override
  public void run() {
    System.out.println(this.seq='thread start.");
    try {
      Thread.sleep(1000);
    } catch (Exception e) {
    }
    System.out.println(this.seq_"thread end.");
  }
  
  public static void main(String[] args) {
    ArrayList<Thread> threads = new ArrayList<>();
    for(int i = 0; i < 10; i++) {
      /*
       * Thread생성하는 부분을 
       * Thread t = new TestThreadJoin(i);
       * 에서 아래와 같이 변경
       */
       Thread t = new THread(new TestRunnable(i));
       t.start();
       threads.add(t);
    }
    for(int i = 0; i<threads.size(); i++) {
      Thread t = threads.get(i);
      try {
        t.join();
      } catch (Exception e) {
      }
      System.out.println("main end,");
    }
  }
}
