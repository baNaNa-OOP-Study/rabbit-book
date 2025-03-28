# 객체의 모양을 결정하는 객체

### 📌 흔히 하는 오해와 잘못된 선입견

#### ❌ **오류 1 : 객체는 데이터를 저장하기 위한 존재다**

*   **잘못된 생각:**\
    객체는 단지 데이터를 담는 컨테이너로 생각하는 경우가 많다.

    ```java
    public class Person {
        private String name;
        private int age;

        // 단순한 getter와 setter만 있다고 생각하는 경우
    }
    ```
*   **올바른 생각:**\
    객체는 **데이터가 아니라 행동(행위)** 을 통해 협력하는 존재이다. 데이터는 협력에 필요한 최소한만 갖춰야 한다.

    ```java
    public class Person {
        private String name;

        public Person(String name){
            this.name = name;
        }

        // 행동과 책임이 존재하는 객체
        public void greet(Person friend){
            System.out.println(name + "이(가) " + friend.name + "에게 인사를 건넸습니다.");
        }
    }
    ```
* **핵심 포인트:**\
  데이터가 우선이 아니라, 행동(메서드)과 책임이 우선이다.

***

#### ❌ **오류 2 : 객체지향 설계는 클래스 간의 정적인 관계 표현이다**

*   **잘못된 생각:**\
    클래스 다이어그램을 그리고 클래스 간 상속이나 연관 관계 같은 정적인 구조에만 집중하는 경우가 많다.

    ```java
    // 클래스 관계 정의에만 집중하는 경우
    public class Customer { }
    public class Order { }
    public class Product { }
    ```
*   **올바른 생각:**\
    클래스는 객체를 만들기 위한 수단일 뿐이다. 중요한 건 클래스가 아니라 객체들이 서로 어떻게 협력하여 원하는 목적을 달성하는가다.

    ```java
    // 협력하는 객체를 생각한 구조
    public class Customer {
        public void order(Product product, Store store) {
            store.receiveOrder(product, this);
        }
    }

    public class Store {
        public void receiveOrder(Product product, Customer customer) {
            System.out.println(customer + " 고객의 " + product + " 상품 주문을 처리합니다.");
        }
    }
    ```
* **핵심 포인트:**\
  클래스의 구조가 아니라, 객체들이 **어떤 책임을 맡고 어떻게 협력**하는지를 먼저 고민하라.

***

### 📌 **올바른 객체지향 설계의 접근법**

#### ✅ **협력을 따라 흐르는 객체의 책임**

객체지향 설계는 다음과 같은 흐름으로 이루어진다.

**1️⃣ 행동(책임)을 먼저 결정하라.**

* 이 객체는 **무엇을 해야 하는가?** (행동, 책임)
* 이 객체는 **누구와 협력해야 하는가?** (협력 관계)

> _예시:_\
> 고객 객체(Customer)는 상품을 주문하는 행동(order)을 수행하고, 가게(Store)는 주문을 받는 행동(receiveOrder)을 수행한다.

**2️⃣ 행동을 수행하는 데 필요한 데이터를 고민하라.**

* 행동을 위해 객체는 **어떤 데이터를 알아야 할까?**
* 데이터는 행동을 지원하는 최소한으로 구성하라.

> _예시:_\
> 고객이 주문하려면 상품(Product)이 필요하고, 가게는 고객과 상품에 대한 정보가 필요하다.

**3️⃣ 협력과 책임이 정해진 후에 클래스 구현 방식을 결정하라.**

* 이때 비로소 클래스, 메서드, 필드 등을 정의한다.

```java
// 협력과 책임을 바탕으로 정의된 클래스들
public class Customer {
    private String name;

    public Customer(String name) {
        this.name = name;
    }

    public void order(Product product, Store store) {
        store.receiveOrder(product, this);
    }

    public String getName() {
        return name;
    }
}

public class Store {
    private String storeName;

    public Store(String storeName) {
        this.storeName = storeName;
    }

    public void receiveOrder(Product product, Customer customer) {
        System.out.println(storeName + "에서 " + customer.getName() + " 고객님의 " + product.getName() + " 상품 주문을 처리했습니다.");
    }
}

public class Product {
    private String name;

    public Product(String name) {
        this.name = name;
    }

    public String getName(){
        return name;
    }
}
```

***

### 🔍 핵심 요약 및 기억할 포인트

| 잘못된 접근 방법               | 올바른 접근 방법                       |
| ----------------------- | ------------------------------- |
| 객체는 데이터 저장용이다           | 객체는 행동과 협력을 위한 존재이다             |
| 클래스 간 관계가 설계의 핵심이다      | 객체 간 협력과 책임을 정하는 것이 설계의 핵심이다    |
| 데이터부터 생각하고 행동을 나중에 정의한다 | 행동(책임)을 먼저 결정하고 데이터는 그 이후에 결정한다 |

***

### ✏️ **정리**

* 객체지향 설계의 핵심은 객체 간 **협력과 책임**을 명확히 정의하는 데 있다.
* 클래스는 객체를 만드는 수단에 불과하며, 중요한 것은 객체가 어떤 행동을 통해 협력하느냐다.
* 데이터를 우선시하는 관점을 벗어나, 행동(책임)을 우선으로 객체를 설계하라.

이러한 접근을 지키면 더 유연하고 유지보수하기 쉬운 객체지향 설계가 가능해진다.
