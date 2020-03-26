# 타임리프
## 1. Thymeleaf
	> Template Engene. th:xx 형식으로 속성을 html태그에 추가하여 값이나 처리 등을 페이지에 심을 수 있다.   
	jsp, 그루비 등 다른 템플릿도 스프링 부트에서 사용 가능하지만 타임리프로 넘어가는 추세..?

## 2. 변수식 : ${ }

```java
@Controller
@RequestMapping("/thymeleaf")
public class ThymeleafController {

	@RequestMapping("/ex02")
	public String Thymeleaf() {
		return "thymeleaf/ex02";
	}
}
```

```html
<body>
	<h1>Hello World!</h1>
	
	<!-- Original -->
	<p th:text="${new java.util.Date().toString()}"></p>
	
	<!-- utility object -->
	<p th:text="${#dates.format(new java.util.Date(), 'yyyy-MM-dd HH:mm')}"></p>
	<p th:text="${#numbers.formatInteger(123,5)}"></p>
	<p th:text="${#strings.toUpperCase('Welcome to Spring Boot')}"></p>
	
	<!-- parameter -->
	<p th:text="'id0=' + ${param.id[0]} + ', id1=' +${param.id[1]}"></p>
</body>
```

> 주소값에 id값 두가지를 넣어주어야 한다. `http://localhost:8080/thymeleaf/ex02?id=hello&id=world`

## 3. 메세지식 : #{ }

src/main/resource 경로에 messages.properties 파일 생성
```
content.id=strongstar
content.name=kdseol
```

```html
<body>
	<h1 th:text="#{content.id}">hello world</h1>
	<p th:text="#{content.name}"></p>
</body>
```

## 4. 링크식 : @{ }
> href와 경로 사이의 공백 주의!
```html
<body>
	<h1 th:text="#{content.id}">hello world</h1>
	<a th:href= "@{'/home/' + ${param.id[0]}}">link</a>
</body>
```

## 5. 객체의 변수식 : *{ }
```java
@RequestMapping("/ex05")
	public String Thymeleaf05(Model model) {
		model.addAttribute("msg", "data..");
		DataObject data = new DataObject(123,"star");
		model.addAttribute("object", data);
		return "thymeleaf/ex05";
	}
	
	class DataObject {
		public int id;
		public String name;
		
		public DataObject(int id, String name) {
			super();
			this.id=id;
			this.name=name;
		}
```

```html
<body>
	<h1 th:text="#{content.id}">hello world</h1>
	<p th:text="${msg}">message.</p>
	<div th:object="${object}">
		<p th:text="*{id}"></p>
		<p th:text="*{name}"></p>
	</div>
</body>
```

## 6. 리터럴 치환 : ||
> ### 상수와 리터럴
>상수는 변하지 않는 변수를 의미하며(메모리 위치) 메모리 값을 변경할 수 없다.  
>리터럴은 변수의 값이 변하지 않는 데이터(메모리 위치안의 값)를 의미한다.  
>보통은 기본형의 데이터를 의미하지만, 특정 객체(Immutable class , VO class)에 한에서는 리터럴이 될 수 있다.  
출처: https://mommoo.tistory.com/14 [개발자로 홀로 서기]

```html
<body>
	<h1 th:text="#{content.id}">hello world</h1>
	<div th:object="${object}">
		<p th:text="|id: *{id}, name : *{name}|">message.</p>
	</div>
</body>
```

## 7. HTML출력
```java
	@RequestMapping("/ex07")
	public String Thymeleaf07(Model model) {
		model.addAttribute("msg", "<h1>END</h1><br /><h2>END</h2>");
		return "thymeleaf/ex07";
	}
```

```html
<body>
	<h1 th:text="#{content.id}">hello world</h1>
	<p th:utext="${msg}">message.</p>
</body>
```

>타임리프는 html태그를 모두 escape 처리하기 때문에 'th:utext'로 써야 한다.

## 8. 조건문, 분기문, 반복문
```java
	@RequestMapping("/{num}")
	public ModelAndView index(@PathVariable int num, ModelAndView mav) {
		mav.setViewName("thymeleaf/index");
		
		mav.addObject("num", num);
		mav.addObject("check", num % 2 == 0);
		mav.addObject("trueVal", "Even number.");
		mav.addObject("falseVal", "Odd number.");

		ArrayList<String[]> list = new ArrayList<String[]>();
		list.add(new String[] {"kim", "kim@a.com"});
		list.add(new String[] {"lee", "lee@b.com"});
		mav.addObject("list", list);
		return mav;
	}
```

```html
<body>
	<!-- "${변수식} ? ${값1} : ${값2}" -->
	<p th:text="${num} + ' : ' + (${check} ? ${trueVal} : ${falseVal})"></p>
	
	<!-- if -->
	<p th:if="${check}" th:text="${num} + ' : ' + ${trueVal}">true</p>
	<p th:unless="${check}" th:text="${num} + ' : ' + ${falseVal}">false</p>
	
	<!-- switch -->
	<div th:switch="${num}">
		<p th:case="1" th:text="one">1</p>
		<p th:case="2" th:text="one">2</p>
		<p th:case="3" th:text="one">3</p>
		<p th:case="*">?</p>
	</div>
	
	<!-- each -->
	<table border="1">
		<tr>
			<td>NAME</td>
			<td>E-MAIL</td>
		</tr>
		<tr th:each="obj:${list}">
			<td th:text="${obj[0]}"></td>
			<td th:text="${obj[1]}"></td>
		</tr>
	</table>
</body>
```

## 9. 전처리
>변수식 앞에 밑줄(_)2개를 사용한다.  
`__${값}__`  
> |expression : ${check}| -> 있는 그대로의 출력  
> `__${check}}__` -> ${check}의 값이 평가되고 난 결과값이 들어감.
```java
	@RequestMapping("/a{num}")
	public ModelAndView index1(@PathVariable int num, ModelAndView mav) {
		mav.setViewName("thymeleaf/index1");
		
		mav.addObject("num", num);
		if(num >= 0) {
			mav.addObject("check", "num >= list.size() ? 0 : num");	
		} else {
			mav.addObject("check", "num*-1 >= list.size() ? 0 : num*-1");
		}

		ArrayList<Person> list = new ArrayList<Person>();
		list.add(new Person("kim", "kim@a.com"));
		list.add(new Person("lee", "lee@b.com"));
		list.add(new Person("park", "park@c.com"));
		mav.addObject("list", list);
		return mav;
	}
	
	class Person {
		public String name;
		public String email;
		
		public Person(String name, String email) {
			this.name = name;
			this.email = email;
		}
	}
```

```html
<body>
	<!-- 리터럴 치환 -->
	<p th:text="|expression : ${check}|"></p>
	
	<!-- 전처리 -->
	<table th:object="${list.get(__${check}__)}" border="1">
		<tr>
			<td>NAME</td>
			<td>E-MAIL</td>
		</tr>
		<tr>
			<td th:text="*{name}"></td>
			<td th:text="*{email}"></td>
		</tr>
	</table>
</body>
```

## 10. 인라인처리
> th:inline="text" 로 작성된 태그 내부에서만 처리 가능  
[[${값}]] 의 형식으로 사용
```java
	@RequestMapping("/b{num}")
	public ModelAndView index2(@PathVariable int num, ModelAndView mav) {
		mav.setViewName("thymeleaf/index2");

		ArrayList<Person> list = new ArrayList<Person>();
		list.add(new Person("kim", "kim@a.com"));
		list.add(new Person("lee", "lee@b.com"));
		list.add(new Person("park", "park@c.com"));
		mav.addObject("list", list);
		return mav;
	}

    class Person {
		public String name;
		public String email;
		
		public Person(String name, String email) {
			this.name = name;
			this.email = email;
		}
	}
```

```html
<body>
    <!-- 인라인 처리 -->
	<table th:inline="text" border="1">
		<tr>
			<td>NAME</td>
			<td>E-MAIL</td>
		</tr>
		<tr th:each="person:${list}">
			<td>[[${person.name}]]</td>
			<td>[[${person.email}]]</td>
		</tr>
	</table>
</body>
```

## 11. 인라인처리 in 자바스크립트
> `<script th:inline="javascript"></script>` 내에서 적용  
`/*[[${값}]]*/` 의 형식으로 사용
```java
	@RequestMapping("/c{num}")
	public ModelAndView index3(@PathVariable int num, ModelAndView mav) {
		mav.setViewName("thymeleaf/index3");
		mav.addObject("num", num);
		return mav;
	}
```

```html
<body>
	input value : <input type="number" id="val" /> <br />
	result : <input type="number" id="result" readonly="readonly" /> <br />
	
	<button onclick="plus()">Click</button>
	
	<script	src="https://code.jquery.com/jquery-3.2.1.slim.min.js"
	integrity="sha256-k2WSCIexGzOj3Euiig+TlR8gA0EmPjuc79OEeY5L45g="
	crossorigin="anonymous"></script>
	<script th:inline="javascript">
		function plus() {
			var val = $("#val").val();
			var num = /*[[${num}]]*/;
			$("#result").val(val*1 + num*1);
		}
	</script>
</body>
```

## 12. 템플릿 프래그먼트
> `<tag th:fragment="fragmentName">`  
`<tag th:include="templateName::fragmentName">`
> > ex.  
common.html에 `<nav th:fragment="header">...</nav>` 작성.  
index.html 에서 `<nav th:include="common::header"></nav>` 로 사용.  

> include의 경로는 같은 폴더가 아닐 경우 해당 경로로 지정해 주어야 한다.
```java
@RequestMapping("/index4")
	public ModelAndView index4(ModelAndView mav) {
		mav.setViewName("thymeleaf/index4");
		return mav;
	}
```
- index.html
```html
<body>
	<h1>index4.html</h1>
	
	<div th:include="thymeleaf/part::frgDiv">
		<h2>index</h2>
		<p>index message..</p>
	</div>
</body>
```
- part.html
```html
<body>
	<h1>Fragment Sample</h1>
	
	<div th:fragment="frgDiv">
		<h2>frg</h2>
		<p class="frg">frg message..</p>
	</div>
</body>
```