# MVC란 무엇일까 ?

model, view , controll 
- view : 눈에 보이는 것 
- model : 결과 저장소 
- controller : 처리 

여기서 저장소인 model은 key , value 값으로 저장할 수 있습니다

Spring은 입력받을 값들을 매개변수로 선언하고 Model model , model.addAttribute("key",value)로 선언해서 작업을 처리합니다.
model은 작업결과를 저장후, 결과를 보여 줄 view를 반환해줍니다 .
반환시에는 return "view 이름" 으로 반환하면 됩니다.

'서블릿'은 자동으로 model에 저장되어 있는것을 view로 전달합니다
