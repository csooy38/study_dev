# SPRING

## 1. 스프링 개요
- 선수학습 : `java`, `jsp(servlet)`, 스크립트 언어(`html`, `javascript`, `css`, `jquery`)
- 개념 : 자바 언어를 기반으로 한 애플리케이션을 제작할 때 효율적으로 빠르게 개발할 수 있도록 하는 애플리케이션 프레임워크(프로그래밍 틀).
	
### 1.1. 스프링 프레임워크란?
- 스프링은 엔터프라이즈(기업용) 애플리케이션에서 필요로 하는 여러가지 기능들을 제공하는 프레임 워크.
- Java EE가 제공하는 기능들을 스프링에서도 지원하고 있기 때문에 국내에서는 가장 인기있는 프레임워크로 자리를 잡았다.
- 스프링은 Java EE에서 제공하는 기능 외에 DI나 AOP와 같은 기능을 추가적으로 제공한다.
- Java EE에서 MVC-2 모델 방식도 새로운 애플리케이션을 개발할 때마다 일일이 처음부터 다시 개발해야 하는 단점이 있다. 모든 애플리케이션에서 공통적인 기능등을 처음부터 다시 개발해야 한다는 것은 상당히 비효율적이다.
- 이보다 더 좋은 방법이 바로 스프링이다. 애플리케이션 개발 시에 일반적인 웹 애플리케이션에서 많이 사용하는 기능들은 미리 만들어서 제공하고, 그 외에 필요한 부분만 추가 및 수정하는 방식을 이용하면 된다. 이렇게 하면 훨씬 효율적일 뿐만 아니라 일정한 형식에 따라서 개발을 진행하므로 표준화가 이루어져 생산성도 높일 수 있다.
- 애플리케이션은 규모가 커질수록 각각의 기능들을 개발자가 따로 개발하는 것보다는 표준화된 방법으로 개발하는 것이 상당히 유리하다. 
- 그렇다면 <b>프레임워크(framework)</b>란?
	* 프레임워크(framework)의 사전적 의미는 `"어떤 것을 구성하는 구조 또는 뼈대"`이다.
	* 소프트웨적 의미로는 "기능을 미리 클래스나 인터페이스 등으로 만들어 제공하는 반제품" 정도로 해석할 수 있다. 
	* 즉, 어느 정도는 완성된 상태로 제공하는 기능이다.
	
	
### 1.2. 스프링 프레임워크의 특징
- 스프링은 경량의 프레임워크이다.
	* 자바의 객체를 담고 있는 컨테이너(IoC 컨테이너).
	* 객체의 생성, 관리, 소멸과 같은 생명주기를 관리한다.
	
	
### 1.3. DI(Dependecy Injection : 의존성 주입)
- DI는 스프링 핵심 개념 중 하나.
- 기존에는 어떤 한 클래스가 다른 클래스의 기능(메서드)을 사용하려면 당연히 개발자가 코드에서 직접적으로 사용할 클래스의 생성자를 호출하여 사용하였다(new 키워드 이용). 따라서 사용할 클래스와 사용될 클래스의 관계는 개발자에 의해 직접 코드에서 부여가 되었다.(높은 의존도 - 강한 결합)
- 스프링에서는 객체 사이의 의존 관계를 객체 자신이 아닌 외부(스프링 컨테이너)에서 수행하는 개념이다.
	* 즉, 이런 연관 관계를 개발자가 직접 코딩을 통해서 부여하는 것이 아니라 스프링 컨테이너가 연관 관계를 직접 규정하는 것을 말한다. 그러면 코드에서 직접적인 연관 관계가 발생하지 않으므로 각각의 클래스들의 변경이 자유로워진다.(약한 결합) 따라서 스프링 프레임워크에서는 각 클래스들의 연관 관계를 클래스들 간의 사이에서 맺어지는 것이 아니라, 스프링 프레임워크에서 설정을 통해 맺어줌으로써 클래스들끼리 연관 관계를 맺지 않도록 구현을 해 놓았다.
- 스프링 프레임워크에서의 의존 관계는 설정 파일(bean.xml)이나 애노테이션을 이용하여 설정한다.
- 스프링에서 클래스(빈 : `bean`)를 담는 그릇을 스프링 컨테이너라고 한다.
	* 스프링 기반 애플리케이션에서는 스프링 컨테이너에서 객체가 태어나고, 자라고 소멸한다.
	* 스프링 컨테이너는 객체를 생성하고, 서로 엮어 주고, 이들의 전체 생명주기를 관리한다.
	* 스프링 컨테이너는 스프링 프레임워크 핵심부에 위치한다. 스프링 컨테이너는 종속 객체 주입을 이용해서 애플리케이션을 구성하는 컴포넌트를 관리하며, 협력 컴포넌트 간 연관 관계의 형상도 스프링 컨테이너에서 이루어진다.
		
		
### 1.4. 스프링 컨테이너의 종류
- `BeanFactory` : 단순히 스프링 컨테이너에서 객체를 생성하고 DI만 처리해 주는 기능만을 제공하는 객체.
	* 하지만 스프링을 사용하는 이유는 단순히 DI만 사용하기 위해서가 아니다. 
	* 스프링을 사용하는 이유는 다양한 부가 기능(트랜잭션 처리, 자바 코드 기반의 스프링 설정, 애노테이션을 이용한 빈 설정,  스프링을 이용한 웹 개발 등) 때문인데 이러한 부가적인 기능을 사용하기 위해서는 `ApplicationContext` 객체를 주로 이용한다.
- `AbstractApplicationContext` : 컨테이너 종료(`close()`)와 같은 기능을 제공하는 객체.
- `GenericXmlApplicationContext` : `AbstractApplicationContext` 객체를 상속받아 만들어진 클래스로, xml 파일에서 스프링 빈 설정 정보를 읽어 오는 역할을 한다.
- `GenericXmlApplicationContext` 객체를 생성할 때 파라미터 값으로 "classpath:getsum.xml" 을 전달했는데 이는 클래스 패스에 위치한 xml 파일을 설정 파일로 사용한다는 의미이다.
- `GenericXmlApplicationContext` 객체는 전달 받은 xml 파일에서 설정 정보를 읽어 와서 스프링 빈 객체를 생성하고 프로퍼티 값을 설정한다.
	* 이렇게 생성된 스프링 빈 객체는 `getBean()` 이라는 메서드를 사용해서 구현할 수 있다. `getBean()` 메서드의 첫번째 파라미터는 구현하고자 하는 스프링 빈 객체의 고유한 id 이름이며, 두번째 파라미터는 그 객체의 클래스 타입을 의미한다.
	
	
#### [예]

- 스프링은 객체를 생성하고 각각의 객체를 연결해 주는 조립기 역할을 한다.
- 여기에 있는 GenericXmlApplicationContext 객체가 조립기 기능을 구현한 클래스이다.
- 조립기에서 생성할 객체가 무엇이고, 각 객체를 어떻게 연결하는지에 대한 정보는 xml 파일에 설정이 되어 있다.
- GenericXmlApplicationContext 클래스는 이 xml 파일에 정의된 설정 정보를 읽어와서 객체를 생성하고, 각각의 객체를 연결한 뒤에 내부적으로 보관한다.
- xml을 이용한 스프링 설정을 하다 보면 컨테이너가 생성할 객체를 지정하기 위해 <bean> 태그를 사용하는 것을 볼 수 있다.
- 스프링 컨테이너가 생성해서 보관하는 객체를 스프링 빈(spring bean) 객체라고 부르며, 일반적으로 자바 객체와 동일하다.
- 스프링 컨테이너는 생성한 빈 객체를 <이름, 빈 객체> 이렇게 쌍을 보관한다.
- 스프링 컨테이너가 보관하고 있는 객체를 사용하고 싶은 경우 빈 객체와 연결되어 있는 이름을 이용해서 객체를 참조하게 된다.
		  
```java
public class GetSum {
	
	private int num1;
	private int num2;
	
	public int getNum1() {
		return num1;
	}
	public void setNum1(int num1) {
		this.num1 = num1;
	}
	public int getNum2() {
		return num2;
	}
	public void setNum2(int num2) {
		this.num2 = num2;
	}
	
	// 핵심기능(비지니스 로직)
	public void hap(int num1, int num2) {
		System.out.println("더하기 >> " + (num1 + num2));
	}
}
```

```java
public class MyGetSum {
	
	private int su1;
	private int su2;
	private GetSum getSum;
	
	public int getSu1() {
		return su1;
	}
	public void setSu1(int su1) {
		this.su1 = su1;
	}
	public int getSu2() {
		return su2;
	}
	public void setSu2(int su2) {
		this.su2 = su2;
	}
	public GetSum getGetSum() {
		return getSum;
	}
	public void setGetSum(GetSum getSum) {
		this.getSum = getSum;
	}
	
	// 핵심 기능
	public void sum() {
		this.getSum.hap(su1, su2);
	}
}
```

* src/main/resources/getsum.xml
	- DI 즉, 주입을 어떻게 할 것인지는 xml 문서에 기입이 되어 있다.
	- 스프링 컨테이너인 `ctx`가 "classpath:getsum.xml" 파일을 보고 DI를 진행한다.
	- getsum.xml 파일은 `resource` 폴더에 들어가 있어야 한다.
	- `AbstractApplicationContext` 객체가 DI 작업을 하는 스프링 컨테이너.
	- 스프링 컨테이너 객체를 생성한다.
	- xml 파일을 이용하여 메모리로 스프링 컨테이너 객체가 생성된다.(메모리로 로딩)

```xml
<!-- GetSum getsum = new GetSum(); 와 동일 -->
<bean id="getsum" class="com.sist.di01.GetSum"/>
	
<bean id="mySum" class="com.sist.di01.MyGetSum">
	<!-- MyGetSum mySum = new MyGetSum();
	mySum.setSu1(200);
	mySum.setSu2(100);
 -->

<property name="su1" value="200"/>
	<property name="su2" value="100"/>
	<property name="getSum">
		<ref bean="getsum"/>
	</property>
</bean>
```


* Main.java

```java
AbstractApplicationContext ctx = new GenericXmlApplicationContext("classpath:getsum.xml");

// 실제적으로 이 코드에서 주입과정이 일어나게 된다.
// new 키워드를 사용하지 않고 직접 스프링 컨테이너에서 꺼내서 사용한다.

// my1 = my2  동일. (방식의 차이)
MyGetSum my1 = (MyGetSum)ctx.getBean("mySum");
MyGetSum my2 = ctx.getBean("mySum", MyGetSum.class);	
		
my1.sum();
my2.sum();
		
// 사용한 자원은 반납해야 한다.
ctx.close();
```
	