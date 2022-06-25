# DI and AOP란?

> 코드를 통해 스프링 DI가 무엇인지 이해해보겠습니다!

## 변경에 유리한 코드 
```java

SprotsCar car = new SportsCar()  // car를 생성하는 객체 A 가 있을떄 을 Truck으로 바꿀떄 변경할곳은 2곳
Truck car = new Truck(); 


classs car{}
class SportsCar extends car{}
class Truck extends Car{} 로 구성되어 있습니다 
만약, Car car = new SportsCar(); // 이렇게 존재하는데, 하단으로 바꾼다면 변경사항은 1개입니다.
      Car car = new Truck(); 
> 즉 부모타입의 참조변수로 바꾸면 변경사항이 하나로 줄어듭니다. 상단에 있는 코드보다 변경에 더욱 유리한코드입니다.

더욱 간단하게 하자면, 즉 별도의 메소드를 통해 객체를 반환하게 바꾼다면 
// getCar를 호출하는 수많은 메서드는 내용이 바뀌어도 안바꾸어도된다 
Car car = getCar();

//기능제공
static Car getCar(){
  return new SportsCar();  // Sportscar() > Truck(); 이렇게 하나만 바꾸면된다
}



부모타입의 참조변수를 활용한 장점
- 변경사항이 발생했을떄 더 적으노력을 코드를 바꿀 수 있음
- 변경포인트가 많으면 실수가 생길 확률이 높아지니 변경포인트를 줄여 실수가능성을 낮춤

  
