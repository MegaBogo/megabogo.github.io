# 자바에 날개를 달자
## Thread (쓰레드)
동작하고 있는 프로그램을 프로세스라고 한다.
보통 한 개의 프로세스는 한 가지의 일을 하지만
쓰레드를 이용하면 한 프로세스 내에서 두 가지 또는 그 이상의 일을 동시에 할 수 있다.

``java
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

``
