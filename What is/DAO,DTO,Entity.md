# DAO, DTO, Entity
```
개발블로그를 읽다보면 DAO, DTO 그리고 Entity를 볼 수 있다.
나는 프로젝트에서 DAO를 사용했고 다른 두개는 둘다 DB에 접근한다 정도만 알고 넘어갔었다
시간이 흘러 지금이라도 제대로 알아보고 싶어졌다.
```

# 개념
**DAO**(Data Access Object) :
* 제로 DB에 접근하는 객체이다.
  - Persistence Layer(DB에 data를 CRUD하는 계층)이다.
* Service와 DB를 연결하는 고리의 역할을 한다.
* SQL를 사용(개발자가 직접 코딩)하여 DB에 접근한 후 적절한 CRUD API를 제공한다.
  - JPA 대부분의 기본적인 CRUD method를 제공하고 있다.

**DTO**(Data Transfer Object) :
* 계층간 데이터 교환을 위한 객체(Java Beans)이다.
  - DB에서 데이터를 얻어 Service나 Controller등으로 보낼때 사용하는 객체
  - 즉, DB에서 데이터가 Presentation Logic Tier로 넘어오게 될 때는 DTO의 모습으로 바뀐다.
  - 로직을 가지고 있지 않은 순수한 데이터 객체, getter/ setter메소드만 가지고있다.
  - 하지만 DB에서 꺼낸 값을 임의로 변경할 필요가 없어 DTO클래스에는 setter가 없다.
* Request와 Response용 DTO는 View를 위한 클래스
  - 자주 변경이 필요한 클래스
  - Presentation Model
  - toEntity() 메소드를 통해서 DTO에서 필요한 부분을 이용하여 Entity로 만든다.
  - Controller Layer에서 Response DTO 형태로 Client에 전달한다.
  
 **VO vs DTO**
  - VO는 DTO와 동일한 개념이지만 read only속성
  - VO는 특정한 비지니스 값을 담는 객체, DTO는 Layer간 통신의 용도로 오가는 객체

**Entity**
* 실제 DB의 테이블과 *1:1*로 매칭될 클래스
  - Entity클래스 또는 Core한 클래스라고 부르며 @Entity, @Column, @Id를 이용
* 최대한 외부에서 Entity클래스의 getter메소드를 사용하지 않도록 클래스 안에서 필요한 메소드를 구현
  - 단, Domain Logic만 가지고, Presentation Logic을 가지고 있으면 안된다.
  - 구현한 메소드는 Service Layer에서 사용한다.
* 상속 x , 인터페이스 구현체 x
* Entity와 DTO를 분리하는 이유는 View Layer와 DB(Persistence) Layer를 분리하기 위해서

# 전체 구조
![image](https://user-images.githubusercontent.com/97998574/186835421-95de4651-f48c-496b-8c58-09fa703dfe2a.png)

```
유저가 browser에서 form으로 서버로 DTO를 보낸다.
DTO는 Controller > Service > Repository를 거치고
Repository에서 DB로 Entity클래스로 오간다.
forRest에서는 User라는 Domain객체만을 사용해서 browser부터 db까지 오갔는데 이렇게 했어야하는구나.. 
```
