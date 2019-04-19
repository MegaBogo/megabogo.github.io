# package cafe

집가서 정리핮,

Program

```java
public class Program {
  public static void main(String[] args) {
    Store store = new Store();
    Barista barista = new Barista(store);
    Customer cus = new Customer();
    
    barista.sayHi();
    cus.order(store.getMenu());
    
    int price = barista.orderConfirmation(cus.getOrderList());
    int orderNum = 0;
    if(cus.isMoney(price)) {
      orderNum = barista.paymentRequest(cus, price);
    }
    if(orderNum > 0) {
      cus.recevieBell(store.addBell(orderNum, cus));
      store.addTrayList(orderNum, barista.produce(orderNum));
      cus = store.callCustomer(orderNum);
      cus.setTray(barista.giveTray(cus.getBell()));
      cus.eat();
    }
  }
}

```

domain.Barista.java
```java
public class Barista {
  private Store store;
  public Barista() {
  
  }
  public Barista(Store store) {
    this.store = store;
  }
  public void sayHi() {
    store.hiRule();
  }
  public Tray produce(int orderNum) {
    Stack<Item> produces = store.getOrderItem(orderNum);
    Tray tray = new Tray(orderNum);
    for(Item item : produces) {
      System.out.println(item.name()+"음료완성");
      tray.add(item.name());
    }
    return tray;
  }
  public int orderConfirmation(Stack<Item> orderList) {
    int price = 0;
    for(Item item : orderList) {
      price += item.getPrice();
      SYstem.out.println(item.name());
    }
    if(price > 0)
      System.out.printf("총 결제 금액은 %d원입니다.￦n", price);
    return price;  
  }
  public Tray giveTray(Bell bell) {
    return store.getRay(bell.getNum());
  }
  public boolean payment(int price) {
    boolean success = false;
    if((price > 0) {
      success = true;
    }
    return success;
  }
  public int paymentRequest(Customer cus, int price) {
    int num = 0;
    if(payment(price)) {
      num = store.addOrderHistory(cus.getOrderList());
    } else {
      System.out.println("결제를 실패했습니다,.");
    }
    return num;
  }
}
```
domain.Bell.java
```
public class Bell {
  private int num;
  private Customer cus;
  public Bell() {
  
  }
  public Bell(int num, Customer cus) {
    this.num = num;
    this.cus = cus;
  }
  public Customer call() {
    return cus;
  }
  public void setNum(int num) {
    this.num = num;
  }
}
```
domain.Customer.java
```java
public class Customer {
  private Stack<Product.Item> orderList;
  private int money;
  private int money;
  private Bell bell;
  private Tray tray;
  
  public Customer() {
    this.orderList = new Stack<>();
    this.money = 100000;
  }
  public Stack<Product.Item> getOrderList() {
    return orderList;
  }
  public Stack<Product.Item> order(HashMap<String, Product> menu) {
    Scanner scan = new Scanner(System.in);
    String text = null;
    boolean sw = true;
    while(sw) {
      text = scan.next();
      if(text.equals("exit"00 {
        sw = false;
      } else {
        if(menu.containsKey(text)) {
          orderList.push(menu.get(text).getItem());
        }
      }
    }
    return orderList;
  }
  public void recevieBell(Bell bell) {
    this.bell = bell;
  }
  public boolean isMoeny(int price) {
    if(money >= price) {
      this.moeny -= price;
      return true;
    }
    System.out.println("다음에 올게요,,,,,");
    
    return false;
  }
  public void setTray(Tray tray) {
    this.tray = tray;
  }
  public Bell getBell() {
    return bell;
  }
  public void eat() {
   tray.getFoods();
  }
}
```
domain.Menu.java
```java
public class Menu {
  private HashMap<String, Product> menu;
  public Menu() {
    this.menu = this.generateProducts();
  }
  private HashMap<String, Product> generateProducts() {
    HashMap<String, Product> products = new HashMap<>();
    for(Product.Item item : Item.values()) {
      products.put(item.name(), new Product(item));
    }
    return products;
  }
  public HashMap<String, Product> getProduct() {
    return menu;
  }
}
```
domain.Product.java
```java
public class Product {
  private Item item;
  public Product() {
  
  }
  public Product(Item item) {
    this.item = item;
  }
  public Item getItem() {
    return item;
  }
  public void setItem(Item item) {
    this.item = item;
  }
  public enum Item {
    a("커피",1500);
    private String type;
    private int price;
    
    private Item() {
    
    }
    private Item(String type, int price) {
      this.type = type;
      this.price = price;
    }
    pulic String getType() {
      return type;
    }
    public int getPrice() {
      return price;
    }
  }
}
```
domain.Store.java
```java
public class Store {
  private String name;
  private HashMap<String, Product> menu;
  private HashMap<Integer, Tray> trayList;
  private TreeMap<Integer, Stack<Item>> orderHistory;
  
  pulic Store() {
    this.name = "보고";
    this.menu = new Menu().getProduct();
    this.orderHistory = new TreeMap<>();
    this.bells = new Stack<>();
  }
  public void showMenu() {
    for(String key : menu.keySet()) {
      Product product = menu.get(key);
      System.out.printf("%s --- %d원￦n", product.getItem().name, product.getItem.getPrice());
    }
  }
  public HashMap<String, Product> getMenu() {
    return menu;
  }
  public void hiRule() {
    System.out.println("안녕하세요"+name+"입니다.");
    System.out.println("메뉴판을 보고 주문을 해주세");
    this.showMenu();
  }
  public void addTrayList(int key, Tray tray) {
    trayList.put(key, tray);
  }
  public HashMap<Integer, Tray> getTrayList() {
    return trayList;
  }
  public Tray getRay(int i) {
    return trayList.get(i);
  }
  public int addOrderHistory(Stack<item> item) {
    int num = orderHistory.size()+1;
    orderHistory.put(num,item);
    return num;
  }
  public Customer call(int orderNum) {
    System.out.println("주문번호");
    return bells.get(orderNum-1).call();
  }
  public String getName() {
    return this.name;
  }
  public Stack<item> getOrderItem(int num) {
    return orderHistory.get(num);
  }
  public Bell addBell(int orderNum, Customer cus) {
    Bell bell = new Bell(orderNum,cus);
    bells.push(bell);
    return bell;
  }
}
```
domain.Tray.java
```java
pubic class Tray {
  private Stack<String> foods;
  private Integer num;
  public Tray() {
  
  }
  public Tray(int num) {
    this.num = num;
    foods = new Stack<>();
  }
  public void add(String food) {
    foods.push(food);
  }
  public void getFoods() {
    for(String food : foods) {
      System.out.println(food="냠냠냠");
    }
  }
}

```
