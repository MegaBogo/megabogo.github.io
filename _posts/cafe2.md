# cafe2
## Program.java
```java
public class Program {
  public static void main(String[] args) {
    Store store = new Store("보고카페");
    store.baristaGoToWork(new Barista("알바생1"));
    store.guset();
  }
}
```
## domain.Barista.java
```java
public class Barista {
  private String name;
  private Store store;
  
  public Barista() {
  
  }
  public Barista(String name) {
    this.name = name;
  }
  
  public void goToWork(Store store) {
    this.store = store;
  }
  pulic void sayHi() {
    store.customerManual().sayHi();
  }
  public void sayBye() {
    store.customerManual().sayBye();
  }
}
```
## domain.CustomerManual.java
```java
public class CustomerManual {
  private Store store;
  public CustomerManual() {
  
  }
  public CustomerManual(Store store) {
    this.store = store;
  }
  public void sayHi() {
    System.out.println("어서오세요! "+store.getName()+"입니다.");
    System.out.println("메뉴를 확인해주세요");
    store.showMenu();
  }
  public void sayBye() {
    System.out.println("빠이빠이");
  }
}
```
## domain.Menu.java
```java
public class Menu {
  private Stack<MenuItem> menuList;
  
  public Menu() {
    this.menuList = new Stack<>();
    menuList.push(new MenuItem("아메리카노", 1500));
    menuList.push(new MenuItem("카페라떼", 200));
    menuList.push(new MenuItem("녹차라뗴", 2300));
    menuList.push(new MenuItem("망고스무디", 3000));
    menuList.push(new MenuItem("녹차프라페", 3000));
  }
  public Stack<MenuItem> getMenuList() {
    return this.menuList;
  }
  public void show() {
    System.out.println("=====메뉴=====")
    for(MenuItem item : menuList) {
      System.out.printf("%s %d원\n", item.name, item.price);
    }
  }
}
```
## domain.MenuItem.java
```java
public class MenuItem {
  String name;
  int price;
  
  public MenuItem() {
  
  }
  public MenuItem(String name, int price) {
    this.name = name;
    this.price = price;
  }
}
```
## domain.Store.java
```java
public class Store() 
  private String name;
  private Menu menu;
  private CustomerManual customerManual;
  
  public Store() {
    this("카페");
  }
  public Store(String name)
    this.name = name;
    this.menu = new Menu();
    this.customerManual = new CustomerManual(this);
  }
  public String getName() {
    return this.name;
  }
  public CustomerManual customerManual() {
    return this.customerManual;
  }
  public void showMenu() {
    menu.show();
  }
  public void baristaGoToWork(Barista barista) {
    barista.goToWork(this);
    this.barista = barista;
  }
  public void guset() {
    barista.sayHi();
  }
}
```
