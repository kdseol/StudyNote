# 재귀 알고리즘

## 1. 재귀(Recursion) 함수란?
> 특정 함수 내에서 자기 자신을 다시 호출하여 문제를 해결해나가는 함수.  
문제를 해결하기 위해 원래 범위의 문제에서 더 작은 범위의 하위 문제를 먼저 해결함으로써 원래 문제를 해결해 나가는 방식.  
일반 반복문을 통해 구현가능한 기능은 재귀함수를 통해 구현이 가능하며, 반대로 재귀함수를 통해 구현한 기능은 반복문으로 구현이 가능하다.

* 재귀 함수는 함수 내에서 자기 자신을 계속 호출하는 방식이기 때문에 함수 안에 반드시 종료 구간이 되는 BaseCase를 생각하며 코드를 구현해야 한다.

```java
Public class Recursion_Test {
    public static void main(String[] args) {
        Function();
    }
 
    public static void Function() {
        System.out.println("반갑습니다");
         Function();
    }
}
```
* Function이라는 Method는 '반갑습니다'를 출력하고 자기자신을 호출하지만 종료되는 구간이 없기 때문에 무한루프가 된다.

```java
public class Recursion_Test3 {
    public static void main(String[] args) {
        Function(5);
    }
 
    public static void Function(int num) {
        if(num == 0){
            return;
        } else {
            System.out.println("반갑습니다");
             Function(num - 1);
        }
    }
}
```

* 매개변수 num을 받고 if구문에 의해 분기를 시킨다. 매개변수 값이 0이면 리턴을 하고 0이 아닐경우 '반갑습니다'를 출력하고, num-1을 전달한다.

<img src="./recursion1.png" style="width:80%">

* 결과적으로 출력은 총 5번 된다.


## 2. 1부터 n까지 합 구하기
```java
public class Recursion_Test2 {
    public static void main(String[] args) {
        System.out.println("1부터 5까지의 합은 : " + Function(5));
    }
 
    public static int Function(int num) {
        if(num == 1) {
            return 1;
        } else {
            return num + Function(num -1);
        }
    }
}
```

<img src="./recursion1.png" style="width:80%">

출처 : https://lktprogrammer.tistory.com/106

## 3. 재귀함수와 for 문 (반복문) 의 차이
1. 메모리 
 > 재귀함수는 함수를 반복적으로 호출하기 때문에 스택 메모리를 사용한다.  
(스택 오버플로우가 발생할 수 있다. )  
반면 반복문은 메모리 힙을 사용한다.

 

2. 코드길이
 > 재귀함수를 사용하면 반복문에 비해 코드수를 줄일 수 있다. 

 



출처: https://noahlogs.tistory.com/32?category=827412