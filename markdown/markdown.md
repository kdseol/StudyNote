# Markdown


## 1. 문단 구분
<pre>
한 개 이상의 빈 줄을 문단에 삽입하거나
줄의 마지막에 스페이스바를 두번 이상 띄어쓰기
</pre>

## 2. 헤더(Header)
<pre>
# This is a H1
## This is a H2
### This is a H3
#### This is a H4
##### This is a H5
###### This is a H6
</pre>

## 3. 블럭인용문자(BlockQuote)
<pre>
> This is a first blockqute.
>	> This is a second blockqute.
>	>	> This is a third blockqute.
</pre>

## 4. 목록
### 4.1. 순서있는 목록(ol)
<pre>
1. 첫번째
2. 두번째
3. 세번째
    1. 세번째의 첫번째
    2. 세번째의 두번째
</pre>
>현재까지는 어떤 번호를 입력해도 순서는 내림차순으로 정의된다.

### 4.2. 순서없는 목록(ul)
<pre>
* 빨강
  * 녹색
    * 파랑

+ 빨강
  + 녹색
    + 파랑

- 빨강
  - 녹색
    - 파랑
</pre>
>혼합해서 사용하는 것도 가능하다.
<pre>
* 빨강
  + 녹색
    - 파랑
</pre>

## 5. 코드
4개의 공백 또는 하나의 탭으로 들여쓰기를 만나면 변환되기 시작하여 들여쓰지 않은 행을 만날때까지 변환이 계속된다.

### 5.1. 들여쓰기
<pre>
    문장을 탭으로 들여쓰면 된다.
</pre>
### 5.2. 코드블럭
* `<pre><code>{code}</code></pre>` 이용방식

```
<pre>
<code>
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("Hello, Honeymon");
  }

}
</code>
</pre>
```

* 코드블럭코드("\```") 을 이용하는 방법

<pre>
<code>
```
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("Hello, Honeymon");
  }
}
```
</code>
</pre>

## 6. 수평선 `<hr/>`
다음 문법은 모두 수평선을 만든다.

    * * *

    ***

    *****

    - - -

    ---------------------------------------

## 7. 링크
* 참조링크

```
[link keyword][id]

[id]: URL "Optional Title here"

// code
Link: [Google][googlelink]

[googlelink]: https://google.com "Go google"
```

Link: [Google][googlelink]

[googlelink]: https://google.com "Go google"

* 외부링크
```
사용문법: [Title](link)
적용예: [Google](https://google.com, "google link")
```
Link: [Google](https://google.com, "google link")

* 자동연결
```
일반적인 URL 혹은 이메일주소인 경우 적절한 형식으로 링크를 형성한다.

* 외부링크: <http://example.com/>
* 이메일링크: <address@example.com>
```

* 외부링크: <http://example.com/>
* 이메일링크: <address@example.com>

## 8. 강조
```
*이텔릭*
_이텔릭_
**두껍게**
__두껍게__
~~취소선~~
<u>밑줄</u>
```

* *이텔릭*
* _이텔릭_
* **두껍게**
* __두껍게__
* ~~취소선~~
* <u>밑줄</u>

```문장 중간에 사용할 경우에는 **띄어쓰기** 를 사용하는 것이 좋다.```   
문장 중간에 사용할 경우에는 **띄어쓰기**를 사용하는 것이 좋다.

## 9. 이미지
```
![Alt text](/path/to/img.jpg)
![Alt text](/path/to/img.jpg "Optional title")
```
![석촌호수 러버덕](https://camo.githubusercontent.com/202c9ae1d457d6109be6c4cf13db9cac5fd708a6/687474703a2f2f6366696c65362e75662e746973746f72792e636f6d2f696d6167652f32343236453634363534334339423435333243374230)
![석촌호수 러버덕](https://camo.githubusercontent.com/202c9ae1d457d6109be6c4cf13db9cac5fd708a6/687474703a2f2f6366696c65362e75662e746973746f72792e636f6d2f696d6167652f32343236453634363534334339423435333243374230 "RubberDuck")

사이즈 조절 기능은 없기 때문에 ```<img width="" height=""></img>```를 이용한다.

예
```
<img src="/path/to/img.jpg" width="450px" height="300px" title="px(픽셀) 크기 설정" alt="RubberDuck"></img><br/>
<img src="/path/to/img.jpg" width="40%" height="30%" title="px(픽셀) 크기 설정" alt="RubberDuck"></img>
```

<img src="https://camo.githubusercontent.com/202c9ae1d457d6109be6c4cf13db9cac5fd708a6/687474703a2f2f6366696c65362e75662e746973746f72792e636f6d2f696d6167652f32343236453634363534334339423435333243374230" width="450px" height="300px" title="px(픽셀) 크기 설정" alt="RubberDuck"></img><br/>
<img src="https://camo.githubusercontent.com/202c9ae1d457d6109be6c4cf13db9cac5fd708a6/687474703a2f2f6366696c65362e75662e746973746f72792e636f6d2f696d6167652f32343236453634363534334339423435333243374230" width="40%" height="30%" title="%(비율) 크기 설정" alt="RubberDuck"></img>

## 10. 코드
<pre><code>
```대신에 ~~~도 사용 가능하다.

```html
&lt;a href="https://www.google.co.kr/" target="_blank"&gt;GOOGLE&lt;/a&gt;
```

```css
.list > li {
  position: absolute;
  top: 40px;
}
```

```javascript
function func() {
  var a = 'AAA';
  return a;
}
```

```bash
$ vim ./~zshrc
```

```python
s = "Python syntax highlighting"
print s
```
</code></pre>

```html
<a href="https://www.google.co.kr/" target="_blank">GOOGLE</a>
```

```css
.list > li {
  position: absolute;
  top: 40px;
}
```

```javascript
function func() {
  var a = 'AAA';
  return a;
}
```

~~~bash
$ vim ./~zshrc
~~~

```python
s = "Python syntax highlighting"
print s
```

```yaml
No language indicated, so no syntax highlighting. 
But let's throw in a tag.
```
## 11. 표(Table)

> &lt;table&gt; 태그로 변환됩니다.
헤더 셀을 구분할 때 3개 이상의 -(hyphen/dash) 기호가 필요합니다.
헤더 셀을 구분하면서 :(Colons) 기호로 셀(열/칸) 안에 내용을 정렬할 수 있습니다.
가장 좌측과 가장 우측에 있는 |(vertical bar) 기호는 생략 가능합니다.
```
| 값 | 의미 | 기본값 |
|---|:---:|---:|
| `static` | 유형(기준) 없음 / 배치 불가능 | `static` |
| `relative` | 요소 자신을 기준으로 배치 |  |
| `absolute` | 위치 상 부모(조상)요소를 기준으로 배치 |  |
| `fixed` | 브라우저 창을 기준으로 배치 |  |
```
값 | 의미 | 기본값
---|:---:|---:
`static` | 유형(기준) 없음 / 배치 불가능 | `static`
`relative` | 요소 **자신**을 기준으로 배치 |
`absolute` | 위치 상 **_부모_(조상)요소**를 기준으로 배치 |
`fixed` | **브라우저 창**을 기준으로 배치 |