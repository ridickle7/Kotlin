![image](https://media-exp2.licdn.com/mpr/mpr/AAIA_wDGAAAAAQAAAAAAAArRAAAAJDQ4ODhlMjA5LTY4ODctNGQyMS04MGM3LTM0Yjk0MDc1ZTFlNQ.png)

# 1. 코틀린

2011년에 처음 나옴  
구글에서 공식적으로 지원 (2017.05)  
안드로이드 뿐만 아니라 다른 플랫폼에도 사용 가능  

두드러지는 장점  
1. 간결함  
   - java의 경우, getter / setter / toString() / 재정의 등 사전 작업들이 많다.  
   - kotlin의 경우, **간단하게 처리** 가능  
   - object를 통해 singleton 도 지원 가능

2. 안전한 처리  
   <pre><code>// java의 경우
   String str = null;
   null.length;                    // NullPointerException!!!
   
   // kotlin의 경우
   var str : String
   output = null                   // compile error
   
   // kotlin의 경우 (만약 null 사용하고 싶을 경우)
   var str : String?
   output = null
   println(output.length())	// compile error  
   
  
   fun calculateTotal(obj : Any) {
      if(obj is Invoice){          // 자동 캐스팅 됨
         obj.calculateTotal()
      }
   }
   </code></pre>
   
3. 상호 운용 가능 (java와의 상호운용 가능) 
   - java 코드를 kotlin 에 복붙하면, java 코드 kotlin 화

4. 툴과 친밀하다
   - 친~ 밀 합니다!
