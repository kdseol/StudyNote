# 자바 명명 규칙

## 주로 쓰는 반의어


값 | 의미 
---|:---:
`get / set` | 받다/ 받다
`add / remove` | 추가/제거
`create / destroy` | 창조/파괴하다
`start / stop` | 시동/정지
`insert delete` | 삽입/삭제
`increment / decrement` | 증가/감소
`old / new` | 구/신
`begin / end` | 시작/끝
`girst / last` | 긴/마지막
`up / down` | 위/아래
`min / max` | 최소/최대
`next / previous` | 다음/이전
`open /close` | 열다/ 닫다
`show /hide` | 보이다/ 숨기다
`suspend /resume` | 일시 정지/재개하다
`parent / child` | 부모/아이

## 공통
>대소문자가 구분되며 길이에 제한이 없다.  
예약어를 사용해서는 안 된다.  
숫자로 시작해서는 안 된다.  
특수문자는 '_' 와 '$'만을 허용한다.  
파스칼 표기법 (PascalCase)과 카멜 표기법(camelCase)를 사용한다.  
`PascalCase` : 모든 단어에서 첫 번째 문자는 대문자이며 나머지는 소문자이다.  
`camelCase` : 최초에 사용된 단어를 제외한 첫 번째 문자가 대문자이며 나머지는 소문자이다.  
반의어는 반드시 대응하는 개념으로 사용해야 한다.

## 1. 패키지(Package)
>패키지명은 표준 패턴을 따라야 한다.  
Ex) `[com].[Company].[Project].[TopPackage].[LowerPackage]`  
패키지명은 가급적 한 단어의 명사를 사용한다.  
Ex) 좋은 예 : `com.nexon.sudden.member.object`  
Ex)  나쁜 예 : `sudden.memberObject`

## 2. 클래스(Class)
>파스칼 사용  
`Ex) public class HelloWorld {}`
인터페이스에는 특별한 접두사나 접미사를 사용하지 않고 파스칼을 사용한다.  
`Ex) public interface Animal {}`  
인터페이스를 구현한 클래스에는 특별한 접두사나 접미사를 사용하지 않고 파스칼을 사용한다.  
`Ex) public class Tiger implements animal{}`  
추상 클래스에는 특별한 접두사 접미사를 사용하지 않고 파스칼을 사용한다.  
`Ex) public abstract class Animal {}`  

## 3. 메소드(Method) 명명 규칙

> 메소드명에는 파스칼 표기법을 사용한다.  
`Ex) public void SendMessage(String message) {}`  
속성에 접근하는 메소드명의 접두사는 'get','set'을 사용한다.  
`Ex) public void setDisplayName`  
`Ex) public void getDisplayName`  
데이터를 조회하는 메소드명의 접두사는 find를 사용한다.  
`Ex) public void findData(String data){}`  
데이터를 입력하는 메소드명의 접두사는 input을 사용한다.  
`Ex) public void inputData(HashMap data){}`  
데이터를 변경하는 메소드명의 접두사는 modify를 사용한다.  
`Ex) public void modifyData(HashMap data){}`  
데이터를 삭제하는 메소드명의 접두사는 delete를 사용한다.  
`Ex) public void deleteData(String data){}`  
데이터를 초기화 하는 메소드명의 접두사는 initialize을 사용한다.  
`Ex) public void initData(String data){}`  
반환값의 타입이 boolean인 메소드는 접두사로 is를 사용한다.  
`Ex) public void isData(String Data){}`  
데이터를 불러오는 메소드명의 접두사는 load를 사용한다.  
`Ex) public void loadData(){}`  
데이터가 있는지 확인하는 메소드명의 접두사는 has를 사용한다.  
`Ex) public void hasData(){}`  
보다 지능적인 set이 요구될때 사용하는 메소드명의 접두사는 register를 사용한다.  
`Ex) public void registerAccount(){}`  
새로운 객체를 만든뒤 해당 객체를 리턴해주는 메소드명의 접두사는 create를 사용한다.  
`Ex) public void createAccount(){}`  
해당 객체를 다른 형태의 객체로 변환해주는 메소드명의 접두사는 to를 사용한다.  
`Ex) public void toString(){}`  
해당 객체가 복수인지 단일인지 구분하는 메서드명의 접미사는 s를 사용한다.  
`Ex) public void getMembers(){}`  
B를 기준으로 A를 하겠다는 메소드명의 전치사는 By를 사용한다.  
`Ex) public void getUserByName(String name){}`  
반환값의 타입이 boolean인 메소드는 접두사로 is를 사용한다.  
`Ex) public void isData(String Data){}`  
데이터를 불러오는 메소드명의 접두사는 load를 사용한다.  
`Ex) public void loadData(){}`  
데이터가 있는지 확인하는 메소드명의 접두사는 has를 사용한다.  
`Ex) public void hasData(){}`  
보다 지능적인 set이 요구될때 사용하는 메소드명의 접두사는 register를 사용한다.  
`Ex) public void registerAccount(){}`  
새로운 객체를 만든뒤 해당 객체를 리턴해주는 메소드명의 접두사는 create를 사용한다.  
`Ex) public void createAccount(){}`  
해당 객체를 다른 형태의 객체로 변환해주는 메소드명의 접두사는 to를 사용한다.  
`Ex) public void toString(){}`  
해당 객체가 복수인지 단일인지 구분하는 메서드명의 접미사는 s를 사용한다.  
`Ex) public void getMembers(){}`  
B를 기준으로 A를 하겠다는 메소드명의 전치사는 By를 사용한다.  
`Ex) public void getUserByName(String name){}`

## 4. 변수(Variable) 명명 규칙

> 변수와 메소드의 파라미터에는 카멜표기법을 사용한다.  
변수에 약어를 사용하지 않고 모든 의미를 충분히 담는다.  
한 글자로 된 이름을 사용하지 않는다.  
선언된 지점에서 초기화하며, 가능한 사용범위를 최소화 한다. 숫자 0 레퍼런스 null  
반복문에서 인덱스로 사용할 변수는 i,j,k 등으로 사용한다.  
`Ex) for(int i = 0; i < 10; i++){}`  
지역변수와 멤버변수(전역변수)는 변수명 앞에 밑줄(_)을 사용하여 구별한다.  
boolean타입의 변수는 접두사로 is를 사용한다 Ex) isCheck  

출처: https://m.blog.naver.com/reona7140/221306141987