# '커피 주문할 수 있는 애플리케이션' 만들기를 통해 Spring mvc 학습 및 설명

애플리케이션을 만들기 전 REST API기반으로 제공할 기능을 리소스(자원)을 분류합니다.
저는 MEMBER(커피숍 사장, 고객) , COFFEE (커피(제품)) ,주문 이렇게 3영역으로 분류하였습니다. 
이렇게 만들어진 영역은 Package로 묶어 코드를 진행


```java
회원관리를 위해 MemberController 클래스를 만듦 
@RestController 
@RequestMapping 을 클래스 위에 붙여줍니다. 

- 현재 Controller클래스 안에 있는 구현된 요청을 처리하는 메서드를 '핸들러 메서드'라 말합니다.

//우선 memebercontroller에 필요한 회원 정보인 이메일 , 이름 ,전화번호를 명시 ( 클라이언트 요청 및 응답에 필요한 정보)

Requestmapping에 produces를 붙입니다. 붙인 이유는 produces 속성은 응답데이터를 어떤 미디어 타입으로 클라이언트에게 전송할지를 설정해줍니다.
가장 많이 활용되는 JSON형식으로 붙이기위해 Mediatype.APPlication_JSON_Value; 를 붙입니다.
이값을 설정하지 않으면 JSON형식의 데이터를 응답으로 전송하지 않고 문자열 자체를 전송합니다 .
```
MemberController클래스의 내부 메소드 설명
1.Postmemeber()메서드 : 회원정보를 등록해주는 '핸들러메서드'
2.Getmember()메서드: 특정회원의 정보를 클라이언트 쪽에 제공하는 메서드 


1.postMember() 메서드 위 @ postmapping 애너테이션을 붙입니다. 이것을 붙이는 이유는 : 클라이언트의 요청데이터를 서버에 생성하기 위해서입니다.
postMember() 메서드의 리턴타입은 String , 단 클라이언트 쪽에서 JSON형식의 데이터를 전송 받아야 함으로 응답문자열을 JSON형식으로 해야합니다.
관례: 일반적으로는 POSTMethod를 처리하는 핸들러메서드는 데이터를 생성한 후 생성데이터를 리턴해주는게 관례입니다

2.@getmapping 을 getmember메서드 위에 작성합니다, 괄호안에는 몇가지의 속성을 사용할 수 있지만 현재 저는 HTTP URI를 지정하였습니다.

> 즉 클라이언트 쪾에서 Getmemeber() 핸들러메서드에 요청을 보낼 경우 최종 URI는 "v1/members/"/{member-id}"

RequestMapping + Getmapping 이 두가지가 합쳐져있습니다.

# 작성한 코드 
```java
import org.springframework.http.MediaType;
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping(value = "/v1/members", produces = {MediaType.APPLICATION_JSON_VALUE})
public class MemberController {
    @PostMapping
    public String postMember(@RequestParam("email") String email,
                             @RequestParam("name") String name,
                             @RequestParam("phone") String phone) {
        System.out.println("# email: " + email);
        System.out.println("# name: " + name);
        System.out.println("# phone: " + phone);
        
        String response =
                "{\"" + 
                   "email\":\""+email+"\"," + 
                   "\"name\":\""+name+"\",\"" + 
                   "phone\":\"" + phone+ 
                "\"}";
        return response;
    }

    @GetMapping("/{member-id}")
    public String getMember(@PathVariable("member-id")long memberId) {
        System.out.println("# memberId: " + memberId);

        // not implementation
        return null;
    }

    @GetMapping
    public String getMembers() {
        System.out.println("# get Members");

        // not implementation
        return null;
    }
}
```

회원고객이 주문한 커피주문 정보를 서버에 등록해주는 postorder() 메서드
- 고객이 주문한 커피에 필요한 정보: 어떤 고객이 어떤 커피를 주문했는지 ( 회원식별자 : memberId) 

getorder() : 특정 주문정보를 클라이언트 쪽에 제공하는 핸들러 메서드

위에 직접작성한 코드의 문제점이 있습니다. 문제점으로는 
1. JSON형식의 문자열을 수작업 하였습니다. 
이러한 수작업은 프로그래밍에 오랜시간을 걸리게하고 비효율적입니다.

이러한 문제를 해결하기 위해 
(1) 클래스 레벨의 @Requestmapping 옆 produces삭제하고 
(2) Json문자열이 map객체로 대체하여 key,value값을 넣어 요청을 받는것 입니다.
- Map<Stirng,Stirng>의 겨웅 key,value 값이 모두 String이어야합니다, if key가 String이고 value 값이 다른타입의 데이터면 Object로 지정합니다
Map객체를 리턴하게 되면 내부적으로 ' 이 데이터는 JSON형식의 응답데이터로 변환해야 되구나'라고 이해하며 json형식으로 자동으로 변환해줍니다.
(3) 리턴값으로 JSON문자열을 리턴하는 부분을 ResponseEntity 객체로 바꾸는 것입니다.
```java
return new ResponseEntity<>(map,HTTPStatus.CREATED);

// 위 프로그래밍의 의미는, ResponseEntity 객체를 생성하면서 생성자 파라미터로 Map과 HTTP응답상태를 함께 전달하는 것입니다. 즉 요청자에게 보여주는것
//HTTP응답상태를 넣어주어 클라이언트 요청을 서버가 어떻게 처리했는지 알려줄 수 있어 원활한 소통을 가능케합니다.

```

