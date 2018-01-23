![image](https://media-exp2.licdn.com/mpr/mpr/AAIA_wDGAAAAAQAAAAAAAArRAAAAJDQ4ODhlMjA5LTY4ODctNGQyMS04MGM3LTM0Yjk0MDc1ZTFlNQ.png)

# 2. 설치 및 기초

## 설치
[설치링크](https://kotlinlang.org/docs/reference/basic-syntax.html)  
  
단축키  
1. cmd + shift + A : 안스내 옵션 확인

## 기초

### 1. 함수
<pre><code>// 0. 기존 java
int sum(int a, int b, int total){
	return total+a+b;
}

// 1_1. return 방식
fun sum(a:Int, b:Int, total:Int): Int{
   return a+b+total
}

// 1_2. return 없음
fun sum(a:Int, b:Int, total:Int) = a + b + total;

// 2. '?' 사용 가능
fun sum(str: String): Int? {
	// 정수가 아닌 경우 NULL 을 리턴 (?를 적는다)
}

// 3. 자동으로 타입이 변환됨
fun sum(obj? : Any): Int? {
	if (obj is String){
		// obj가 자동으로 변환됨
		return obj.length
	}
	
	return null;
} 
</code></pre>

### 2. 변수

#### 2.1 변수 선언 방식
   - 1. val : 읽기전용 변수, 1회만 선언 가능 (final과 유사)  
     <pre><code>// 선언 방법
     val a : Int = 3			// 선언 후 할당
     val b = 2			// Int 추론 후 할당
     val c : Int? = parseInt(a)	// parseInt(a) 가 정수가 아닌 경우 Null 할당
     val d : Int			// compile error (초기화 필요)
     a = 4				// compile error (읽기 전용)
     </code></pre>
     
   - 2. var : mutable 변수
     <pre><code>// 선언 방법
     var a = 5
     a++</code></pre>
     
     
     
#### 2.2 자료형 종류 
   - 코틀린에서 모든 타입은 객체  
     -> 멤버 함수나 프로퍼티를 호출 가능
     
   - boxing
     <pre><code>// boxing example
     var a: Int = 10000		// int
     var b: Int = 10000		// int	
     println(“a === b : ${a === b}”)	// true
     println(“a == b : ${a == b}”)	// true
     
     var a: Int = 10000		// int
     var b: Int? = 10000		// Integer
     println(“a === b : ${a === b}”)	// false
     println(“a == b : ${a == b}”)	// true</code></pre>
     
   - 1. Numbers  
     말 그대로 숫자  
     문자를 숫자로 처리할 수 없음  
     UnderScore 활용 가능 (ex> 1_000_000)
     작은 타입에서 큰 타입으로 대입 불가능 (Explicit Conversation)
     <pre><code>// example
     val a : Int = 3
     
     val b : Long = a		// O
     val b : Long = a.toLong()	// O
     </code></pre>
     
   - 2. String   
     ※ String Interpolation (문자열 보간법)  
       스트링빌더(StringBuilder) or + 기호 없이 아래처럼 활용 가능
     <pre><code>// String 선언 방식, 활용 예제
     // 1. java에서 흔히 사용하는 string 방식
     val strDefine1 = "\n이것은 코틀린의\nescaped String\n입니다.\n"
     // 2. 개행문자, 특수문자 다 들어갈 수 있는 string 방식
     val strDefine2 = """
     이것은 코틀린의
     raw String
     입니다.
     """
     
     val str1 = "a is $a"
     
     val str2 = "${str1.replace("is", "was)}, but now is $a"
     
     var str3 : String = "Kotlin"
     println(str3.get(0))
     println(str3[0])
     println(str3.length)
     </code></pre>
     
   - 3. 자료구조
     <pre><code>// 자료구조
     val listItems = listOf("A", "B", "C")
     val setItems = setOf("A", "B", "C")
     var arrayItems1 : arrayOf("a", "b")
     var arrayItems2 : Array<String> = Array(2, {item -> arrayItems1[item]})
     // item은 index를 의미
     
     println(arrayItems1.get(0))
     println(arrayItems1[0])
     println(arrayItems1.size)

     listItems	// 람다 활용 가능
     	.filter{ item.startsWith("a") }
     	.sortedBy{ item }
     	.map { item.toUpperCase() }
     	.forEach { println(it) }
     </code></pre>


### 3. 문법

#### 3.1 조건문
   - java, C 사용방식과 동일  
   - 삼항 연산자가 없음
   - 경우에 따라 해당 조건문을 변수로 바로 대입 가능
   <pre><code>// 변수 대입 example
   val max = if (a > b) a else b; 
   </code></pre>

#### 3.2 반복문
   - while, for 은 사용방법 거의 동일
     <pre><code>// 새로운 example
     for(i in 1..100) {
       print("");
     }
     </code></pre>
   - iterator을 제공하는 모든 것을 반복할 수 있음  
     ※ for 문을 지원하는 iterator 의 조건
       1. 멤버변수 혹은 확장함수 중에서 iterator()를 반환하는 것이 있는 경우
       2. next() 를 가지는 경우
       3. hasNext() : Boolean 을 가지는 경우
     <pre><code>// iterator 만들기 example
     val myData = MyData()
     for(item in myData){
       print(item)
     }
     
     class MyData{
       operator fun iterator() : MyIterator{
         return MyIterator()
       }
     }
     
     class MyIterator{
       val data = listOf(1,2,3,4,5)
       val idx = 0
       operator fun hasNext() : Boolean{
         return data.size > idx
       }
       
       operator fun next() : Int{
         return data[idx++]
       }
     }</code></pre>
   - range
     <pre><code>// range를 이용한 for loop
     for(x in listOf(1,2,3)){
       print(x)
     }
     </code></pre>
   - index를 활용하고 싶을 시 
     1. indices 를 활용하기
     2. withIndex() 를 이용
     <pre><code>// index 활용 example
     // 1. indices 활용 example
     for(i in array.indices){
       print("$i = ${array[i]}")
     }
     
     // 2. withIndex() 활용 example
     for((index, value) in array.withIndex()){
       println("$index : ${value})
     }</code></pre>

#### 3.3 when 문
   - switch와 비슷한 문법
   - branches의 조건문이 만족할때까지 위에서 순차적으로 인자를 비교
     <pre><code>// When 문법 활용 예제1
     fun describe(obj : Any) : String {
     	when (obj){
     		1		-> "One"		// 숫자 1인 경우, One 스트링 리턴
				"Hello"		-> "Greeting"		// Hello 스트링인 경우, Greeting 스트링 리턴
				is Long	  	-> "Long"		//
				!is String	-> "Not a String"	//
				else		-> {		// 중괄호처리도 가능
					println("Unknown")
					"Unknown"
				}
			}
	  }
	  val items = setOf("A","B","C")
	  
	  when{
	     "D" in items	-> println("juicy")
	     "A" in items	-> println("apple is fine too")
     }
     </code></pre>


### 4. 기타

#### 4.1 package
   패키지 별도 선언 안할 경우, 기본 패키지에 자동 포함  
   ※ 기본 패키지 : 별도 임포트 없이 활용할 수 있는 패키지
   
#### 4.2 label
   코틀린은 기본 3개의 점프 표현식 제공  
   - return : nearest enclosing 함수에서 값을 반환한다  
   - break : 현재 루프를 빠져 나감  
   - continue : 현재 루프의 다음 스텝 진행  
   - label은 for, while 등의 표현식에 붙일 수 있다.  
	  > loop@ -> 레이블 선언  
	  > @loop -> 레이블 적용  
   <pre><code> // label 사용 example
   array.forEach label@ {	// label 활용 안할 시, for문이 아닌 가장 가까운 바깥 함수가 종료됨
     if(it == 1) return @label
     print(it)
   }
   print("end")
   </code></pre>
