# 책임
---
```
"객체지향 개발에서 가장 중요한 능력은, 책임을 능숙하게 소프트웨어 객체에 할당하는 것."
```
---
## 책임
- 객체가 ___알아야 하는 정보___ 와, 객체가 ___수행할 수 있는 행위___ 에 대해 개략적으로 서술한 문장.
1. **하는 것(doing)**
   - 객체를 생성하거나 계산을 하는 등의 스스로 하는 것
   - 다른 객체의 행동을 시작시키는 것
   - 다른 객체의 활동을 제어하고 조절하는 것

2. **아는 것(knowing)**
   - 개인적인 정보에 관해 아는 것
   - 관련된 객체에 관해 아는 것
   - 자신이 유도하거나 계산할 수 있는 것에 관해 아는 것

- 책임은 ___객체지향 설계의 품질___ 을 결정하는 가장 중요한 요소다.

- 책임은 객체의 ___공용 인터페이스(public interface)___ 를 구성한다. → **캡슐화**
---

## 메시지
- 두 객체간의 협력은 ___메시지___ 를 통해 이뤄진다.
- 객체가 다른 객체에게 주어진 책임을 수행하도록 요청을 보내는 것을 ___메시지 전송___ 이라고 한다.
  - 송신자: 메시지를 전송함으로써 협력을 요청하는 객체
  - 수신자: 메시지를 받아 요청을 처리하는 객체

- 메시지는 협력에 참여하는 두 객체 사이의 ___관계___ 를 강조한 것이다.
- 일반적으로 하나의 책임이 여러 메시지로 분할된다.

