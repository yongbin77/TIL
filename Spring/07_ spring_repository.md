### repository class란?

```java
//메세지 저장하는 Repository
public interface MessageRepository extends CrudRepository<Message, Long> {
}

```
#### repository class:
> 데이터 액세스 계층에서 데이터베이스와의 연동을 담당하는 Repository인 Repository 인터페이스
> 특이한 것은 CrudRepository라는 인터페이스를 상속하고 있고, 이 CrudRepository의 제너릭 타입이 <Message, Long>으로 선언

CrudRepository<Message, Long> 와 같이 제너릭 타입을 지정해줌으로써 

 " Message 엔티티 클래스 객체에 담긴 데이터를 데이터베이스 테이블에 
생성 또는 수정하거나 데이터베이스에서 조회한 데이터를 Message 엔티티 클래스로 변환" 
<Message, Long>에서 

Long은 Message 엔티티 클래스의 멤버 변수 중에 식별자를 의미하는 @Id 라는 애너테이션이 붙어있는 멤버 변수의 데이터 타입

즉 @Id를 나타내는 key의 변수 데이터타입을 선언한 것 

#### repository로 무엇을 하나?

>Repository 인터페이스를 서비스 계층에서 DI를 통해 주입받은 후, 데이터베이스 작업을 위해 사용
>즉, 서비스계층에서 사용됨! 


```java

@Service
public class MessageService {
		// repository의 데이터 사용을 위해 DI를 통해 주입받음 
    
    private MessageRepository messageRepository;

    public MessageService(MessageRepository messageRepository) {
        this.messageRepository = messageRepository;
    }
    
    // 비즈니스 메서드 
    public Message createMessage(Message message) {
        return messageRepository.save(message); 
    }
    //crudrepository 인터페이스를 상속받아 save바로 사용가능 
}

// > 즉  개발자가 데이터의 생성, 조회, 수정, 삭제 작업을 위한 별도의 코드를 구현하지 않아도 CrudRepository가 이 작업을 대신해주는 역할을 해줌
```
