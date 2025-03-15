# 정적 모델

* 객체지향 애플리케이션을 설계하고 구현하기 위해서는 <mark style="color:yellow;">**객체 관점의 동적 모델**</mark>과 <mark style="color:yellow;">**객체를 추상화한 타입 관점의 정적 모델**</mark>을 <mark style="color:yellow;">**적절히 혼용**</mark>해야한다.
---

## 타입의 목적
```
"타입을 사용하면 동적으로 변하는 객체의 상태를 정적인 관점에서 표현할 수 있다."
```
  - <mark style="color:yellow;">**타입을 사용하는 이유**</mark>는 인간의 인지 능력으로는 시간에 따라 동적으로 변하는 <mark style="color:yellow;">**객체의 복잡성을 극복하기가 너무 어렵기 때문이다.**</mark>
  - <mark style="color:yellow;">**타입은**</mark> 시간에 따라 동적으로 변하는 <mark style="color:yellow;">**객체의 상태를**</mark> 시간과 무관한 <mark style="color:yellow;">**정적인 모습으로 다룰 수 있게 해준다.**</mark>
  - 결국 타입은 <mark style="color:yellow;">**객체의 상태에 복잡성을 부과하는 시간이라는 요소를 제거**</mark>함으로써 시간에 <mark style="color:yellow;">**독립적인 정적인 모습으로 객체를 생각**</mark>할 수 있게 해준다.
```
"앨리스, 너가 어떤 모습이라도 너가 앨리스라는 사실은 변하지 않아."
```
 - 앨리스라는 객체의 상태가 계속 해서 변하더라도 앨리스를 다른 객체와 구별할 수 있는 <mark style="color:yellow;">**식별성은 동일하게 유지**</mark>된다.
 - 앨리스 객체가 가질 수 있는 모든 경우의 키(height) 값을 나열하는 대신 앨리스의 키(height)가 <mark style="color:yellow;">**임의의 값을 가질 수 있다는 사실만을 생각함으로써 상황을 단순하게 만들 수 있다.**</mark>

---

## 그래서 결국 타입은 추상화다
```
"타입을 이용하면 객체의 동적인 특성을 추상화할 수 있다" 
```
  - 어떤 시점에서 객체에 관해 생각할 때 <mark style="color:yellow;">**불필요한 시간이라는 요소와 상태 변화라는 요소를 제거**</mark>하고 철저하게 <mark style="color:yellow;">**정적인 관점에서 객체의 모습을 묘사하는 것을 가능**</mark>하게 해준다.
  - 결국 <mark style="color:yellow;">**타입은**</mark> 시간에 따른 객체의 상태 변경이라는 <mark style="color:yellow;">**복잡성을 단순화할 수 있는 효과적인 방법**</mark>인 것이다.
 
## 동적 모델과 정적 모델
```
"두 가지 모델을 동시에 고려해야한다."
"하나는 객체가 특정 시점에 구체적으로 어떤 상태를 가지느냐다."
"다른 하나는 객체가 가질 수 있는 모든 상태와 모든 행동을 시간에 독립적으로 표현하는 것이다."
```
  - <mark style="color:yellow;">**동적 모델(dynamic model)**</mark>은 실제로 객체가 살아 움직이는 동안 <mark style="color:yellow;">**상태가 어떻게 변하고 어떻게 행동하는지를 포착하는 것**</mark>이다.
  - <mark style="color:yellow;">**정적 모델(static model)**</mark>은 동적으로 변하는 객체의 상태가 아니라 <mark style="color:yellow;">**객체가 속한 타입의 정적인 모습을 표현**</mark>한다.
  - 클래스를 작성하는 시점에는 시스템을 정적인 관점에서 접근하는 것이다.
  - 그러나 실제로 애플리케이션을 실행해 객체의 상태 변경을 추적하고 디버깅하는 동안에는 객체의 동적인 모델을 탐험하고 있는 것이다.

### 예시) 도서 관리 시스템에서의 객체와 타입 모델

#### 1. 객체(동적 모델) 관점  
- `책1` (도서ID: 001, 제목: **"객체지향의 사실과 오해"**, 저자: **"조영호"**)  
- `책2` (도서ID: 002, 제목: **"클린 코드"**, 저자: **"로버트 C. 마틴"**)  

이처럼 개별 객체는 각각의 상태를 가지며 <mark style="color:yellow;">**동적으로 관리됨**.</mark>


#### 2. 타입(정적 모델) 관점  
- **`Book` 클래스** (공통 속성: `제목`, `저자`, `출판사`, `ISBN` 등)  
- **`Ebook` 클래스** (추가 속성: `파일 형식`, `다운로드 링크`)  
- **`PaperBook` 클래스** (추가 속성: `재고 수량`, `도서관 위치`)  

`Book`이라는 <mark style="color:yellow;">**추상적인 개념(타입)**</mark> 을 정적 모델로 정의해 두면, 전반적인 시스템 설계를 <mark style="color:yellow;">**체계적으로 관리**</mark>할 수 있음.

### 왜 혼용해야 할까?

#### 1. 유연성과 유지보수성 확보
- <mark style="color:yellow;">**정적 모델만**</mark> 사용하면 <mark style="color:yellow;">**상속 구조가 너무 깊어지고**</mark>, 변경이 어려움.  
- <mark style="color:yellow;">**동적 모델만**</mark> 사용하면 <mark style="color:yellow;">**공통된 구조 없이 객체가 난잡하게 생성**</mark>될 수 있음.  
- <mark style="color:yellow;">**정적 모델을 기반으로 하고, 동적 모델을 활용하여 개별 객체를 유연하게 관리**</mark>해야 함.  

#### 2. 시스템 확장 용이
- 예를 들어, `Book` 클래스를 정적 모델로 만들면, 새로운 `AudioBook` 타입을 추가할 때 기존 `Book` 타입을 확장하는 방식으로 쉽게 적용 가능.  
- 반면, 개별 객체(`책1`, `책2`)는 동적으로 다루면서 변경 사항을 적용할 수 있음.  

#### 3. 복잡성 완화 & 설계 명확성
- 모든 개별 객체를 직접 다루면 <mark style="color:yellow;">**관리가 어려워지고**</mark> 코드가 <mark style="color:yellow;">**난잡해질 수 있음**.</mark>  
- 타입을 활용해 <mark style="color:yellow;">**공통된 구조를 정의**</mark>하면 시스템이 더 체계적으로 유지됨.  

#### 결론  
- <mark style="color:yellow;">**정적 모델**</mark>은 시스템의 <mark style="color:yellow;">**기본 틀**</mark>을 제공  
- <mark style="color:yellow;">**동적 모델**</mark>은 개별 객체의 <mark style="color:yellow;">**상태 변화와 관계를 유연하게 조정**</mark>
- 이 둘을 균형 있게 혼용하면 <mark style="color:yellow;">**확장성, 유지보수성, 가독성을 모두 잡을 수 있는 객체지향 설계가 가능해집니다.**</mark>

---

## 클래스
```
"클래스와 타입은 동일한 것이 아니다."
```
  - 클래스는 타입의 구현 외에도 코드를 재사용하는 용도로도 사용되기 때문에 클래스와 타입을 동일시하는 것은 수많은 오해와 혼란을 불어일으킨다.
  - 객체지향에서 <mark style="color:yellow;">**중요한 것**</mark>은 <mark style="color:yellow;">**동적으로 변하는 객체의 '상태'**</mark>와 <mark style="color:yellow;">**상태를 변경하는 '행위'**</mark>다.
  - 클래스는 <mark style="color:yellow;">**타입을 구현하기 위해 프로그래밍 언어에서 제공하는 구현 매커니즘**</mark>이라는 사실을 기억하라.
