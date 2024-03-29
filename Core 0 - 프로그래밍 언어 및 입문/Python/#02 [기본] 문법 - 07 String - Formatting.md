# 문자열 포매팅

문자열 포매팅(Formatting)이란 문자열 안에 어떤 값을 삽입하는 방법이다.





## 1. 서식 지정자 ( format specifier )

* **문자열 포맷 코드 ( %d, %s )**

[% 연산자를 사용하는 옛날 방식](https://docs.python.org/3/library/stdtypes.html#old-string-formatting)

문자열 포매팅 예제에서는 대입해 넣는 자료형으로 정수와 문자열을 사용했으나 이 외에도 다양한 것을 대입할 수 있다. 문자열 포맷 코드로는 다음과 같은 것이 있다.

| 자료형 | 설명                                                         |
| ------ | ------------------------------------------------------------ |
| %s     | 문자열 (String)                                              |
| %c     | 문자 1개 (character)                                         |
| %b     | 2진수                                                        |
| %d     | 10진 정수(Integer)                                           |
| %o     | 8진 정수, 예) '%o' % 8은 '10'                                |
| %x     | 16진 정수, 0~9, a~f, 예) '%x' % 254는 'fe'                   |
| %X     | 16진 정수, 0~9, A~F, 예) '%X' % 254는 'FE'                   |
| %e     | 실수 지수 표기법, 예) '%e' % 2.3은 '2.300000e+00'            |
| %E     | 실수 지수 표기법, 예) '%E' % 2.3은 '2.300000E+00'            |
| %f     | 실수 소수점 표기, 부동소수(floating-point)                   |
| %F     | 실수 소수점 표기, f와 같음, nan은 NAN, inf는 INF로 표시(nan은 숫자가 아니라는 뜻, inf는 무한대) |
| %g     | 실수 일반 형식, 예) '%g' % 2.3e-10은 '2.3e-10'               |
| %G     | 실수 일반 형식, 예) '%G' % 2.3e-10은 '2.3E-10'               |
| %%     | ( % 문자 ) 표시                                              |









### 1.1. 정수 integer

**1) 숫자나 변수 바로 대입**

---

* 숫자

```python
print("I eat %d apples." % 5)
```

```
'I eat 5 apples.'
```

---

* 변수 

```python
number = 3
print("I eat %d apples." % number)
```

```
'I eat 3 apples.'
```

---



**2) 길이와 정렬**

% 뒤에 숫자를 붙이면 문자열을 지정된 길이로 만든 뒤 오른쪽으로 정렬하고 남는 공간을 공백으로 채웁니다.

---

* %길이d : 오른쪽 정렬 

```python
print("%10d" % 13)
```

```
'        13'
```

----

- %-길이d : 왼쪽 정렬 ( 문자열 길이에 -를 붙여주면 됩니다. )

```python
print('%-10d' % 13)
```

```
'13        '
```

 '%-10d는 문자열의 길이를 10으로 만든 뒤 지정된 문자열을 넣고 왼쪽으로 정렬합니다.
따라서 문자열 '13'은 길이가 2이므로 오른쪽 공간을 공백 8칸으로 채웁니다.

---

* '%0길이d' % 숫자 : 길이 만큼 정렬하며 빈칸은 0으로 채워진다.

```python
print('%03d' % 1)
```

```
'001'
```

---





### 1.2. 실수 floating-point

**1) 숫자나 변수 바로 대입**

---

- **'%f' %** **숫자**

```python
print('%f' % 2.3)
```

```
'2.300000'
```

실수를 넣을 때는 %f를 사용하며 고정 소수점 **f**ixed point의 f입니다. %f는 기본적으로 소수점 이하 6자리까지 표시하므로 2.3은 2.300000으로 표시됩니다.

---

* **'%f' % 변수**

```python
print('%f' % number)
```

```
'2.300000'
```

---



**2) 자릿수와 정렬**

---

- **'%길이.자릿수f' % 숫자**

특정 소수점 까지 반올림해서 표시한다.
% 뒤에 숫자를 붙이면 문자열을 지정된 길이로 만든 뒤 오른쪽으로 정렬하고 남는 공간을 공백으로 채웁니다.

```python
print("%0.4f" % 3.42134234)
print("%10.4f" % 3.42134234)
```

```
'3.4213'
'    3.4213'
```

위 예는 숫자 3.42134234를 소수점 네 번째 자리까지만 표시하고 전체 길이가 10개인 문자열 공간에서 오른쪽으로 정렬하는 예를 보여 준다.

---

* **'%0길이.자릿수f' % 숫자**

```python
print('%08.2f' % 3.6)
```

```
'00003.60'
```

'%08.2f' % 3.6을 출력했을 때 '00003.60'이 나온다. 

---

**[참고] 실수의 문자 개수**

* 정수 부분, 소수점, 소수점 이하 자릿수가 모두 포함됩니다. 
  * 정수 : '00003'  -  5개
  * 소수점 : '.'  -  1개
  * 자릿수 : '60'  -  2개 
  * 총 : 8개

---







### 1.3. 문자열 string

문자열 안에 꼭 숫자만 넣으라는 법은 없다. 이번에는 숫자 대신 문자열을 넣어 보자.



**1) 숫자나 변수 바로 대입**

* **%s**

```python
print("I eat %s apples." % "five")
```

```
'I eat five apples.'
```

여기에서 재미있는 것은 %s 포맷 코드인데, 이 코드는 어떤 형태의 값이든 변환해 넣을 수 있다. ( 정수, 실수 포함 )
 %s는 자동으로 '% 뒤에 있는 값'을 문자열로 바꿔준다.

```python
print("I have %s apples" % 3)
print("rate is %s" % 3.234)
```

```
'I have 3 apples'
'rate is 3.234'
```





**2) 길이와 정렬**

- **%길이s**

```python
print('%10s' % 'python')
```

```
'    python'
```

%10s는 문자열의 길이를 10으로 만든 뒤 지정된 문자열을 넣고 오른쪽으로 정렬합니다. 
따라서 문자열 'python'은 길이가 6이므로 왼쪽 공간을 공백 4칸으로 채웁니다.



- **%-길이s**

```python
print('%-10s' % 'python')
```

```
'python    '
```

%-10s는 문자열의 길이를 10으로 만든 뒤 지정된 문자열을 넣고 왼쪽으로 정렬합니다. 
따라서 문자열 'python'은 길이가 6이므로 오른쪽 공간을 공백 4칸으로 채웁니다.

```python
# 왼쪽 정렬 (응용)

print("%-10sjane." % 'hi')
```

```
'hi        jane.'
```









### **1.4. 복합 및 기타**

**[ 2개 이상의 값 넣기 ]**

```python
number = 10
day = "three"
print("I ate %d apples. so I was sick for %s days." % (number, day))
```

```
'I ate 10 apples. so I was sick for three days.'
```

만약 서식 지정자를 서로 붙이면 결과도 붙어서 나오므로 주의해야 합니다. 

```python
print('Today is %d%s.' % (3, 'April'))
```

```
'Today is 3April.'
```

다음과 같이 3과 'April'이 붙어서 3April로 나옵니다.



**[ %% ]**

```python
print("Error is %d%%." % 98)
```

```
'Error is 98%.'
```









## 2. format 메써드 포매팅 ( format() )

문자열의 format 을 사용하면 좀 더 발전된 스타일로 문자열 포맷을 지정할 수 있다. 
인덱스와 슬라이스를 활용한다.

( 문자열이 가지고 있는 함수이다. )



### 2.1. 기본 사용

정수, 실수, 변수, 문자열, 리터럴 모두 사용 가능하다.



**format만 사용하기**

```python
# 3.1415 값 소수 첫 번째 자리까지만 출력
digit = 3.1415
print(format(digit, ".1f"))
```

```
3.1
```





**인덱스 없이 사용하기**

인덱스와 이름을 생략하고, 순서에 맞게 넣는 방식이다.

```python
print("나는 {}를 좋아합니다.".format("피자"))
```

```
나느 피자를 좋아합니다.
```

---

```python
# format() 함수로 숫자를 문자열로 변환하기
format_a = "{}만 원".format(5000)
format_b = "파이썬 열공하여 첫 연봉 {}만 원 만들기".format(5000)
format_c = "{} {} {}".format(3000, 4000, 5000)
format_d = "{} {} {}".format(1, "문자열", True)

# 출력하기
print(format_a)
print(format_b)
print(format_c)
print(format_d)
```

```
5000만 원
파이썬 열공하여 첫 연봉 5000만 원 만들기
3000 4000 5000
1 문자열 True
```





### 2.2. 인덱스 

**인덱스 - 사용하기 ( 1개 )**

여러 개를 삽입할때는 인덱스를 사용할 수 있습니다.

```python
print("I eat {0} apples".format(3))			# 숫자
print("I eat {0} apples".format("five"))	# 문자열
print("I eat {0} apples".format(number))	# 변수(숫자)
```

```
'I eat 3 apples'
'I eat five apples'
'I eat 3 apples'
```





**인덱스 - 사용하기 ( 2개 이상 )**

2개 이상의 값을 넣을 경우 문자열의 {0}, {1}과 같은 인덱스 항목이 format 함수의 입력값으로 순서에 맞게 바뀐다. 

```python
# 여러 개를 삽입할때는 인덱스를 사용할 수 있습니다.
print("{} {} {}".format("Apple", "Banana", "Cherry"))
print("{2} {1} {0}".format("Apple", "Banana", "Cherry"))
```

```python
>>> number = 10
>>> day = "three"
>>> "I ate {0} apples. so I was sick for {1} days.".format(number, day)
'I ate 10 apples. so I was sick for three days.'
```

{0}, {1}과 같은 인덱스 항목 대신 더 편리한 {name} 형태를 사용하는 방법도 있다. {name} 형태를 사용할 경우 format 함수에는 반드시 name=value 와 같은 형태의 입력값이 있어야만 한다. 





**인덱스와 이름을 혼용해서 넣기**

```python
>>> "I ate {0} apples. so I was sick for {day} days.".format(10, day=3)
'I ate 10 apples. so I was sick for 3 days.'
```

위와 같이 인덱스 항목과 name=value 형태를 혼용하는 것도 가능하다.

```python
a, b = 5, "apple"

print("A is {0}".format(a))
print("A is {new_a}".format(new_a=a))

print("B is {0}".format(b))
print("B is {new_b}".format(new_b=b))

print("A is {0} and B is {1}".format(a, b))
print("A is {new_a} and B is {new_b}".format(new_a=a, new_b=b))
print("B is {1} and A is {0}".format(a, b))
print("B is {new_b} and A is {new_a}".format(new_a=a, new_b=b))
```

```bash
# 실행결과
A is 5
A is 5
B is apple
B is apple
A is 5 and B is apple
A is 5 and B is apple
B is apple and A is 5
B is apple and A is 5
```

---

```python
print("나는 {age}살이며, {color}색을 좋아해요!".format(age=25, color="파랑"))
```





**주의! IndexError 예외**

{} 기호의 개수가 format() 함수의 매개변수 개수보다 많으면 IndexError 예외가 발생합니다. 









### 2.3. 슬라이스 ( 공백 및 정렬 )

#### 1) 숫자

**- 정수를 특정 칸에 출력하기**

{:d} int 자료형의 정수를 출력하겠다고 직접적으로 지정하는 것이다. 
{:5d}라고 입력하면 5칸을 잡고 뒤에서 부터 52라는 숫자를 채웁니다. 
{:05d}라고 입력하면 5칸을 잡고 뒤에서 부터 52라는 숫자를 채우면서 빈칸은 0으로 채워주게 된다.

```python
# 정수
output_a = "{:d}".format(52)

# 특정 칸에 출력하기
output_b = "{:5d}".format(52) 	# 5칸
output_c = "{:10d}".format(52)	# 10칸

# 빈칸을 0으로 채우기
output_d = "{:05d}".format(52) 	# 양수
output_e = "{:05d}".format(-52) # 음수

print("# 기본")
print(output_a)

print("# 특정 칸에 출력하기")
print(output_b)
print(output_c)

print("# 빈칸을 0으로 채우기")
print(output_d)
print(output_e)
```

```bash
[ 실행결과 ]

# 기본
52
# 특정 칸에 출력하기
   52
        52
# 빈칸을 0으로 채우기
00052
-0052
```



**부호 붙여 출력하기**

+기호를 추가하면 양수의 경우에는 + 기호를 붙여 줍니다. ( 음수의 경우 - 기호가 붙어 나옵니다. )
{: d} 처럼 앞에 공백을 두면 양수의 경우에 기호 위치를 공백으로 비워줍니다. 

```python
# 기호와 함께 출력하기
output_f = "{:+d}".format(52)  # 양수
output_g = "{:+d}".format(-52) # 음수
output_h = "{: d}".format(52)  # 양수: 기호 부분 공백
output_i = "{: d}".format(-52) # 음수: 기호 부분 공백

print("# 기호와 함께 출력하기")
print(output_f)
print(output_g)
print(output_h)
print(output_i)
```

```bash
[ 실행결과 ]

# 기호와 함께 출력하기
+52
-52
 52
-52
```





**부호 조합하기**

=기호를 붙이면 양수,음수 기호를 빈칸 앞에 다 붙일지, 숫자 앞에 붙일지 지정할 수 있게 된다.
( = 는 기호를 빈칸 앞으로 붙이게 만든다. )

```python
# 조합하기
output_h = "{:+5d}".format(52) 		# 기호를 뒤로 밀기: 양수
output_i = "{:+5d}".format(-52) 	# 기호를 뒤로 밀기: 음수
output_j = "{:=+5d}".format(52) 	# 기호를 앞으로 밀기: 양수
output_k = "{:=+5d}".format(-52)	# 기호를 앞으로 밀기: 음수
output_l = "{:+05d}".format(52) 	# 0으로 채우기: 양수
output_m = "{:+05d}".format(-52)	# 0으로 채우기: 음수
output_n = "{:=+05d}".format(52)	# 0으로 채우고, 기호를 앞으로 밀기: 양수
output_o = "{:=+05d}".format(-52)	# 0으로 채우고, 기호를 앞으로 밀기: 음수

print("# 조합하기")
print(output_h)
print(output_i)
print(output_j)
print(output_k)
print(output_l)
print(output_m)
print(output_n)
print(output_o)
```

```bash
[ 실행결과 ]

# 조합하기
  +52
  -52
+  52
-  52
+0052
-0052
+0052
-0052
```

> **참고** 
>
> 조합 순서가 달라지면 출력이 이상하게 된다. 예를 들어 {:=+05d}를 {:=0+5d}처럼 입력하면 전혀 다른 형태가 나오므로 주의하기 바란다. 후자의 경우 ValueError가 발생한다.





**실수**

기존 포맷이 `{0}`이었다면 그 뒤에 `:`를 붙여 포맷을 지정해 주면 됩니다.

```python
a = 33.567268
print("{0:.4f}".format(a))
-----------------------------
[ 실행결과 ]
33.5673
-----------------------------
```

```python
# float precision
# 총 10글자가 되도록 빈칸 추가, 소수점 아래 자리가 4개가 되도록 절삭
print("The result is:{0:10.4f}".format(123.456789))
-----------------------------
[ 실행결과 ]
The result is:  123.4568
-----------------------------
```



**소수점 표현하기**

float 자료형 출력을 강제로 지정할 때 {:f}를 사용한다.

```python
>>> y = 3.42134234
>>> "{0:0.4f}".format(y)
'3.4213'
```

```python
>>> "{0:10.4f}".format(y)
'    3.4213'
```

[참고] {0:.4f}라고 적어도 잘 작동한다.

위와 같이 자릿수를 10으로 맞출 수도 있다. 
역시 앞에서 살펴본 10.4f, +, 0의 표현식을 그대로 사용한 것을 알 수 있다.

```python
>>> "{0:+10.4f}".format(y)
'   +3.4213'
```

```python
>>> "{0:+010.4f}".format(y)
'+0003.4213'
```



**소수점 의미 없는 소수 제거하기**

.0 처럼 의미없는 소수를 제거하고 출력하고 싶을 때 {:g}를 사용한다.

```python
output_a = 52.0
output_b = "{:g}".format(output_a)
print(output_a)
print(output_b)
```

```bash
[ 실행결과 ]
52.0
52
```













#### 2) 문자열

**출력할 문자열 길이 조절**

출력하고 남는 길이는 빈칸으로 채워진다.

```python
print("{0:8} | {1:5}".format("Name", "Count"))
print("{0:8} | {1:5}".format("Mango", 5))
print("{0:8} | {1:5}".format("Banana", 7))
```

```python
Name     | Count
Mango    |     5
Banana   |     7
```





**왼쪽 정렬**

* **'{인덱스:<길이}'.format(값)**

```python
>>> "{0:<10}".format("hi")
'hi        '
```

`:<10` 표현식을 사용하면 치환되는 문자열을 왼쪽으로 정렬하고 문자열의 총 자릿수를 10으로 맞출 수 있다.

```python
>>> "{:<10}".format("hi")
'hi        '
```



**오른쪽 정렬**

* **'{인덱스:>길이}'.format(값)**

```python
>>> "{0:>10}".format("hi")
'        hi'
```

오른쪽 정렬은 `:<` 대신 `:>`을 사용하면 된다. 



**가운데 정렬**

```python
>>> "{0:^10}".format("hi")
'    hi    '
```

`:^` 기호를 사용하면 가운데 정렬도 가능하다.



**공백 채우기**

```python
>>> "{0:=^10}".format("hi")
'====hi===='
>>> "{0:!<10}".format("hi")
'hi!!!!!!!!'
```

정렬할 때 공백 문자 대신에 지정한 문자 값으로 채워 넣는 것도 가능하다. 

채워 넣을 문자 값은 정렬 문자 `<, >, ^` 바로 앞에 넣어야 한다. 위 예에서 첫 번째 예제는 가운데(`^`)로 정렬하고 빈 공간을 `=` 문자로 채웠고, 두 번째 예제는 왼쪽(`<`)으로 정렬하고 빈 공간을 `!` 문자로 채웠다.







#### 3) **종합**

```python
'{인덱스:[[채우기]정렬][길이][.자릿수][자료형]}'
 
'{0:0<10}'.format(15)       # '1500000000': 길이 10, 왼쪽으로 정렬하고 남는 공간은 0으로 채움
'{0:0>10.2f}'.format(15)    # '0000015.00': 길이 10, 오른쪽으로 정렬하고 소수점 이하 자릿수는 2자리
 
'{0: >10}'.format(15)    # '        15': 남는 공간을 공백으로 채움
'{0:>10}'.format(15)     # '        15': 채우기 부분을 생략하면 공백이 들어감
'{0:x>10}'.format(15)    # 'xxxxxxxx15': 남는 공간을 문자 x로 채움
```

---

```python
# 빈 자리는 빈공간으로 두고, 오른쪽 정렬을 하되, 총 10자리 공간을 확보
print("{0: >10}".format(500))
print("{0: >10}".format(-500))
'       500'
'      -500'

# 양수일 땐 +로 표시, 음수일 땐 -로 표시 
print("{0: >+10}".format(500))
print("{0: >+10}".format(-500))
'      +500'
'      -500'

# 왼쪽 정렬하고, 빈칸으로 _로 채움
print("{0:_>10}".format(500))
'+500______'

# 3자리 마다 콤마를 찍어주기
print("{0:,}".format(100000000000))
'100,000,000,000'

# 3자리 마다 콤마를 찍어주기, +- 부호도 붙이기
print("{0:+,}".format(100000000000))
print("{0:+,}".format(-100000000000))
'+100,000,000,000'
'-100,000,000,000'

# 3자리 마다 콤마를 찍어주기, 부호도 붙이고, 자릿수 확보하기
# 돈이 많으면 행복하니까 빈자리는 ^ 로 채워주기
print("{0:^<+30,}".format(100000000000))
'+100,000,000,000^^^^^^^^^^^^^^'
```





### 2.4. 기타



**금액에서 천단위로 콤마 넣기**

숫자 중에서 금액은 천단위로 ,(콤마)를 넣죠? 파이썬에서는 간단하게 천단위로 콤마를 넣을 수 있습니다.

먼저 format 내장 함수를 사용하는 방법입니다. 다음과 같이 format 함수에 숫자와 ','를 넣어줍니다.

**format(숫자, ',')**

```python
>>> format(1493500, ',')
'1,493,500'
```

format 함수는 서식 지정자와 함께 사용할 수 있습니다. 다음은 콤마를 넣은 숫자를 오른쪽 정렬합니다.

```python
>>> '%20s' % format(1493500, ',')    # 길이 20, 오른쪽으로 정렬
'           1,493,500'
```

포매팅에서 콤마를 넣으려면 다음과 같이 :(콜론)뒤에 ,(콤마)를 지정하면 됩니다.

```python
>>> '{0:,}'.format(1493500)
'1,493,500'
```

만약 정렬을 하고 싶다면 정렬 방향과 길이 뒤에 콤마를 지정해줍니다.

```python
>>> '{0:>20,}'.format(1493500)     # 길이 20, 오른쪽으로 정렬
'           1,493,500'
>>> '{0:0>20,}'.format(1493500)    # 길이 20, 오른쪽으로 정렬하고 남는 공간은 0으로 채움
'000000000001,493,500'
```



**`{` 또는 `}` 문자 표현하기**

```python
>>> "{{ and }}".format()
'{ and }'
```

format 함수를 사용해 문자열 포매팅을 할 경우 `{ }`와 같은 중괄호(brace) 문자를 포매팅 문자가 아닌 문자 그대로 사용하고 싶은 경우에는 위 예의 `{{ }}`처럼 2개를 연속해서 사용하면 된다.









## 3. F-String ( f'문자열{}' )

[주의!] 파이썬 3.6 버전부터는 f 문자열 포매팅 기능을 사용할 수 있다. 파이썬 3.6 미만 버전에서는 사용할 수 없는 기능이므로 주의해야 한다.



**[참고] 치환필드**

f-string에서 ```{name}```과 같이 나중에 다른 데이터로 치환(교체) 될 부분을 ```{}```로 표시해놓은 것을 [치환 필드(replacement field)](https://docs.python.org/ko/3/reference/lexical_analysis.html#formatted-string-literals)라고 부릅니다.

```{num:{width}.{precision}}```와 같이 치환 필드 안에 다시 치환 필드가 들어있는 것을 [중첩된 필드(nested field)](https://docs.python.org/ko/3/reference/lexical_analysis.html#formatted-string-literals)라고 부릅니다. 

'필드(field)'는 단순하게 설명하면 데이터의 일부를 의미하는 용어인데 보통 '데이터베이스(database)'에서 자세히 배웁니다. 

유사한 기능을 하는 ```{}``` 문법을 [format()의 공식 문서](https://docs.python.org/ko/3/tutorial/inputoutput.html#the-string-format-method)에서는 '포맷 필드(format field)'라고 부르고 있습니다.  
파이썬은 발전 속도가 빨라서 공식문서도 아직 애매한 부분들이 있기 때문에 용어 자체에 너무 신경쓰지 마시고 개념만 이해해두시면 됩니다.





### 3.1. 기본 사용

**기본 사용**

```python
name = '홍길동'
age = 30
print(f'나의 이름은 {name}입니다. 나이는 {age}입니다.')
```

```
'나의 이름은 홍길동입니다. 나이는 30입니다.'
```



**표현식 / 리터럴 연산 지원**

표현식이란 문자열 안에서 변수와 +, -와 같은 수식을 함께 사용하는 것을 말한다.

```python
# 리터럴 연산
print(f"Added: {1+2}")
```

```
3
```

---

```python
# 표현식 
age = 30
print(f'나는 내년이면 {age+1}살이 된다.')
```

```
'나는 내년이면 31살이 된다.'
```



**딕셔너리 사용**

딕셔너리는 Key와 Value라는 것을 한 쌍으로 갖는 자료형이다. 02-5에서 자세히 알아본다.
리스트나 배열도 사용 가능하다.

```python
>>> d = {'name':'홍길동', 'age':30}
>>> f'나의 이름은 {d["name"]}입니다. 나이는 {d["age"]}입니다.'
'나의 이름은 홍길동입니다. 나이는 30입니다.'
```





### 3.2. 소수점

**소수점**

```python
# float 정밀도 조절에서 .format()과 f-string의 사용법이 약간 달라요

num = 123.56789
print(str(num))
print("계산 결과:{0:10.4f}".format(num))  # 4는소수점 이하
print(f"계산 결과:{num:{10}.{6}}")  # 10은 빈칸 포함 총 글자수, 6은 출력되는 숫자수
# f-string에서는 {width}.{precision} 형식으로 float 출력을 조절할 수 있습니다.
------------------------
[ 실행결과 ]
123.56789
계산 결과:  123.5679
계산 결과:   123.568
------------------------
```

```python
num = 1.23456789
print(str(num))
print("계산 결과:{0:10.4f}".format(num))  # 4는소수점 이하
print(f"계산 결과:{num:{10}.{6}}")  # 6은 출력되는 총 숫자
------------------------
[ 실행결과 ]
1.23456789
계산 결과:    1.2346
계산 결과:   1.23457
------------------------
```

```python
num = 1.23
print(str(num))
print("계산 결과:{0:10.4f}".format(num))  # 4는소수점 이하, 0으로 패딩을 해줌
print(f"계산 결과:{num:{10}.{6}}")  # 6은 출력되는 총 숫자, 0으로 패딩을 해주지 않음
print(f"계산 결과:{num:10.4f}")  # 패딩 가능
------------------------
[ 실행결과 ]
1.23
계산 결과:    1.2300
계산 결과:      1.23
계산 결과:    1.2300
------------------------
```

---

```python
# f-string에서는 width와 precision에도 변수를 사용할 수 있습니다.
# 사용하기에 따라서는 큰 장점이 될 수도 있습니다.
num = 1.23
width = 10
precision = 6
print(f"계산 결과:{num:{width}.{precision}}") 
------------------------
[ 실행결과 ]
계산 결과:      1.23
------------------------
```



**[참고] float 출력 정밀도 조절**

> format() : 10.4f와 같은 **형식 지정자(format specifier)만 사용 가능**. 10이나 4 자리에 **변수 사용 불가**  
> f-string : 10.4f 같은 **형식 지정자**와 **{10}.{6} 방식** **둘 다 사용 가능**. <u>물결 괄호 안에 **변수 사용 가능**</u>









### 3.3. 공백 및 정렬

**정렬**

```python
>>> f'{"hi":<10}'  # 왼쪽 정렬
'hi        '
>>> f'{"hi":>10}'  # 오른쪽 정렬
'        hi'
>>> f'{"hi":^10}'  # 가운데 정렬
'    hi    '
```

---

```python
num_lines = 5

for i in range(num_lines):
    print(f"{'*' * (i+1):>{num_lines}}")
```

```
    *
   **
  ***
 ****
*****
```



**공백 채우기**

```python
>>> f'{"hi":=^10}'  # 가운데 정렬하고 '=' 문자로 공백 채우기
'====hi===='
>>> f'{"hi":!<10}'  # 왼쪽 정렬하고 '!' 문자로 공백 채우기
'hi!!!!!!!!'
```



**[참고] 한글 줄맞춤**

영어는 글자 하나당 1칸씩 차지 하지만 한글은 1개당 2칸을 차지한다.

```python
print("{0:12} | {1:12}".format("첫 번째 단어", "두 번째 단어"))
print("{0:12} | {1:12}".format("셋째", "넷째"))
-------------------
[ 실행결과 ]
첫 번째 단어      | 두 번째 단어     
셋째           | 넷째  
-------------------
```

**해결 방법**

```python
# 앞에 느낌표를 붙여서 주피터 노트북에서도 패키지 설치를 할 수 있습니다.
# 알파벳 외의 글자들이 적절한 크기를 가질 수 있게 조절하는 함수를 사용한다.
#!pip install wcwidth

from wcwidth import wcswidth

print(wcswidth("안녕AB"), len("안녕AB"))

def wcpadding(s, l):
    return s + " "*(l-wcswidth(s))

print(wcswidth("첫 번째 단어"))

# 스크립트 모드의 터미널 출력에서는 정확하게 줄맞춤 가능
print("{0}|{1}".format(wcpadding("첫 번째 단어", 12), wcpadding("두 번째 단어", 12)))
print("{0}|{1}".format(wcpadding("셋째", 12), wcpadding("넷째", 12)))

# 정확하게 줄맞춤이 가능하지만 불필요한 공백이 삽입 
# 주피터 노트북에서도 정상 작동을 할 수 있게, tab을 넣어준다.
print("{0}\t|{1}".format(wcpadding("첫 번째 단어", 12), wcpadding("두 번째 단어", 12)))
print("{0}\t|{1}".format(wcpadding("셋째", 12), wcpadding("넷째", 12)))
```

```
[ 실행결과 ]
6 4
12
첫 번째 단어|두 번째 단어    
셋째        |넷째            
첫 번째 단어    |두 번째 단어
셋째            |넷째    
```























### 3.4. 기타

**`{ }` 문자를 표시**

다음과 같이 두 개를 동시에 사용해야 한다.

```python
>>> f'{{ and }}'
'{ and }'
```

```python
print(f"나는 {{{name}}}이다.")
```



**이스케이프 코드**

```python
# 백슬래쉬를 직접 사용할 수 없음
f"Newline is {\n}"

# 간접적으로는 사용 가능
newline = "\n"
f"Newline is {newline}"
```













