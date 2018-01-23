![image](https://media-exp2.licdn.com/mpr/mpr/AAIA_wDGAAAAAQAAAAAAAArRAAAAJDQ4ODhlMjA5LTY4ODctNGQyMS04MGM3LTM0Yjk0MDc1ZTFlNQ.png)

# 3. 객체 지향

## 3.1 class

## 3.1.1 정의
 - class라는 이름으로 선언함
 - header, body 생략 가능
   <pre><code>// class 사용 example
   class invoice(number : Int){}
   class Empty
   </code></pre>
   
## 3.1.2 정의
 - 클래스별로 1개만 기본 생성자를 가질 수 있음
   <pre><code>// constructor example
   class Person constructor(firstName : String) {}
   class Person(firstName : String) {}
   </code></pre>   
 - 기본 생성자는 코드를 가질 수 없으므로 초기화는 init 블록에서 진행
   <pre><code>// constructor example
   class Customer(name : String){
     init{
       // 프로퍼티 설정
       // println("Customer value $name")
     }
   }</code></pre>
   
   > ※ 프로퍼티 설정 방법
   ><pre><code>// constructor example
   >// 1
   >class Customer(){
   >  var fullName : String = ""
   >  get() {return field}
   >  set(value) {field = value}  
   >}
   >class Person(firstName : String) {}
   >
   >// 2
   >class Customer(var fullname : String){
   >  get() {return field}
   >  set(value) {field = value}
   >}
   >
   >// 3
   >class Customer public @Inject constructor(name: String) {
   >  get() {return field}
   >  set(value) {field = value}
   >}
   ></code></pre>
 - 생성자를 여러개 가질 수도 있음 (보조 생성자)
   <pre><code>// multiple constructor example
   class Person {
		constructor (parent : Person) {	// 보조 생성자
			parent.children.add(this)
		}
	}
   </code></pre>
 - 클래스가 기본 생성자를 가지고 있다면, 각각의 보조 생성자들은 기본 생성자들을 직 / 간접적으로 위임해야 함
 - this 키워드 활용
		직접 : 기본 생성자에 위임
		간접 : 다른 보조생성자에 위임
	<pre><code>// 기본 생성자와 보조 생성자와의 관계
	class Person(val name : String){
	  constructor(name : String, parent : Parent) : this(name){
	    
	  }
	  
	  constructor() : this("홍길동", Person()){
	  
	  }
	
	}
	</code></pre>
 - 생성된 기본 생성자  
   default 생성자  
   매개변수 X, 가시성 public  
   (가시성을 없애려면, 빈 기본생성자를 선언해야 함)  
   ex> class DontCreateMe private constructor() {}  
## 3.1.3 인스턴스 
 - 코틀린은 new 키워드가 없음
   <pre><code>// instance 생성 example
   val invoice = Invoice()
	val customer = Customer(“Joe Smith”)
   </code></pre>
 - 클래스는 아래의 것들을 포함할 수 있음
   > constructor / init {}  
   > function  
   > properties  
   > nested and inner classes  
   > object declaration	 
