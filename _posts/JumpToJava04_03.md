# 자바에 날개를 달자
## 싱글톤 패턴 (SingletonPattern)
단 `하나의 객체`만을 생성하게 강제하는 패턴
즉 클래스를 통해 생성할 수 있는 객체는 Only One 한개.

``java
class Singleton {
  private static Singleton one;
  private Stringleton() {
  }
  
  /* (1) getInstance을 호출할 때 마다 새로운 객체가 생성
  public static Singleton getInstance() {
    return new Singleton();
  }
  */
  public static Singleton getInstance() {
    if(one == null) {
      one = new Singleton();
    }
  }
}
public class SingletonPattern {
  public static void main(String[] args) {
    /* private이기 때문에 외부 클래스에서 생성자 생성 불가
    Singleton singleton = new Singleton();
    */
    
    /* (1) static메소드를 이용하여 Singleton객체를 돌려받을 수 있지만,
     * getInstance을 호출할 때 마다 새로운 객체가 생성되기 때문에
     * 싱글톤이 아님
     */
    //Singleton singleton = Singleton.getInstance(); 
    
    /*
     * one이라는 static변수를 두고
     * getInstance 메소드에서 one값이 null인 경우에만 객체를
     * 생성하도록 해서 one 객체가 단 한번만 만들어지게.
     * 이 예제로 든 싱글톤은 Thread Safe하지 않음.
     */
     Singleton singleton1 = Singleton.getInstance();
     Singleton singleton2 = Singleton.getInstance();
     
     System.out.println(singleton1 == singleton2);
  }
}
``
