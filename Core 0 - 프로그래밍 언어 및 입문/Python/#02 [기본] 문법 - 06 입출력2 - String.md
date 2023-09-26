# 07 입출력2 - String과 문자열 포맷팅

* '다차원 배열'과 관련된 부분은 'Nested - Containers'에서 다룰 예정



## 1. 문자열 자료형 ( string )

* [Strings](https://docs.python.org/3/tutorial/introduction.html#strings)

문자열(string)은 순서대로 나열되어 있는 문자들을 다루는 자료형입니다.  

글자를 여러 개 담을 수 있다는 점에서 넓은 의미로 **컨테이너(container)** 자료형 중의 하나로 분류가 됩니다.  
컨테이너 자료형들 중에서도 <u>원소(element)들이 순서대로 나열되어 있다는 점</u>에서 **시퀀스(sequence)** 로 다시 분류가 됩니다.  

시퀀스로 분류되는 자료형에는 문자열(string) 외에도 리스트(list)와 튜플(tuple)이 더 있습니다.  
시퀀스에서는 **인덱싱(indexing)** 과 **슬라이싱(slicing)** 을 사용할 수 있습니다.





### 1.1. 리터럴

한 글자 또는 여러 글자의 시작과 끝을 작은따옴표(') 또는 큰따옴표(")로 둘러싸서 만듭니다.  
[참고] 영어에서는 single quote(홑따옴표), double quote(겹따옴표)라고 부릅니다.  

```
"Hello, World" # 큰따옴표 사용
'Hello, World' # 작은따옴표 사용
```

**[참고]** 문자열 리터럴에 큰따옴표(")만을 사용하는 프로그래밍 언어들이 많습니다. 

특히 C, C++, 자바에서는 작은따옴표는 글자 하나에, 큰따옴표는 여러 글자에 사용하기 때문에 아예 용도가 다릅니다. 입력하기에는 작은따옴표가 편하지만 다른 프로그래밍 언어도 공부하실 계획이라면 큰따옴표로 습관들이시는 것을 추천합니다.





#### 1) 문자열 출력하기

```python
print("안녕")
```





#### 2) 작은따옴표, 큰따옴표 

* 작은따옴표 사용은 큰따옴표로 묶기
* 큰따옴표 사용은 작은따옴표로 묶기
* 여러 줄 문자열로 묶기 - `""" """`, `''' '''`
  * 작은 따옴표, 큰 따옴표를 여러 개 출력해야 할 때 사용한다.

* 이스케이프 문자 사용



**큰 따옴표로 묶어서 작은 따옴표 사용하기**

```py
>>> s = "Python isn't difficult"
>>> s
"Python isn't difficult"
```



**작은 따옴표로 묶어서 큰 따옴표 사용하기**

```python
>>> s = 'He said "Python is easy"'
>>> s
'He said "Python is easy"'
```

[주의!] 작은따옴표 안에 작은따옴표를 넣거나 큰따옴표 안에 큰따옴표를 넣을 수는 없습니다.

실행을 해보면 구문 에러(SyntaxError)가 발생합니다.

```python
>>> s = 'Python isn't difficult'
SyntaxError: invalid syntax
>>> s = "He said "Python is easy""
SyntaxError: invalid syntax
```



**여러 줄 문자열로 묶기 - `""" """`, `''' '''`**

여러 줄로 된 문자열은 작은따옴표 안에 작은따옴표와 큰따옴표를 둘 다 넣을 수 있습니다.
 또한, 큰따옴표 안에도 작은따옴표와 큰따옴표를 넣을 수 있습니다. 이번에는 스크립트 파일로 만들고 실행해봅니다.

```py
single_quote = '''"안녕하세요."
'파이썬'입니다.'''
 
double_quote1 = """"Hello"
'Python'"""
 
double_quote2 = """Hello, 'Python'"""    # 한 줄로 작성
 
print(single_quote)
print(double_quote1)
print(double_quote2)
```

```
"안녕하세요."
'파이썬'입니다.
"Hello"
'Python'
Hello, 'Python'
```

이외에도 이스케이프 코드(`\'`, `\"`) 를 사용하는 방법이 있다.





#### 3) Raw 문자열

문자열 앞에 r 또는 R을 붙이면 raw 문자열이 됩니다. 
앞에 r을 붙이며 백슬래쉬를 일반적인 문자로 처리합니다.

이 raw 문자열은 이스케이프 시퀀스를 그대로 저장할 때 사용합니다.

```python
# Raw strings: 

print(R"C:\some\name") 		# print("C:\\some\\name") 보다 편합니다.
print(r'C:\Users\dojang\AppData\Local\Programs\Python\Python36-32\python.exe')
```

```python
C:\some\name
C:\Users\dojang\AppData\Local\Programs\Python\Python36-32\python.exe
```

* raw 문자열에 제어 문자를 입력해보면 제어 문자가 동작하지 않는 것을 볼 수 있습니다.

```python
>>> print(r'1\n2\n3\n')
1\n2\n3\n
```







### 1.2. 문자열의 불변성

파이썬의 문자열(str)은 불변(immutable) 자료형입니다. 
일부를 수정할 수 없고 대신에 수정된 객체를 새로 만들어야 합니다.

```python
a = "ABCDEF"
a[-1:0:-1] # FEDCB
a[-1::-1]  # FEDCBA

print(a)   # 슬라이싱을 해도 원래 객체는 변하지 않는다.
-------------------------------------------------	   
[ 실행결과 ]
ABCDEF
```

```python
# 슬라이싱으로 새로운 객체 생성
b = a[1:]
print(id(a))
print(id(b))
-------------------------------------------------	   
[ 실행결과 ]
1699357016176
1699377727856
```

```python
b = a[0:1000]

# 주소가 동일
print(id(a))
print(id(b))
-------------------------------------------------	   
[ 실행결과 ]
1699357016176
1699357016176
```



**객체의 일부 변경 불가**

```python
# 불변 객체의 일부를 바꿀 수 없습니다.
# ABCDEF
# 012345
a = "ABCDEF"
a[2] = "X"
```

```
TypeError: 'str' object does not support item assignment
```

TypeError가 발생한다.

```python
# 특정 위치의 한 글자만 바꾸고 싶다면?
# ABCDEF
# 012345
a = "ABCDEF"
a = a[:2] + "X" + a[3:]
a
```











### 1.3. 연산하기

#### 1) 사칙 연산

**코드**

```python
# 더하기 연산자 +
print("일이삼" + str(456))

# 곱하기 연산자 *
print("일이삼" * 3)
```

**실행 결과**

```
일이삼456
일이삼일이삼일이삼
```





#### 2) 문자열 길이 함수 - len() 

문자열의 길이는 다음과 같이 len 함수를 사용하면 구할 수 있다. len 함수는 print 함수처럼 파이썬의 기본 내장 함수로 별다른 설정 없이 바로 사용할 수 있다.

```python
>>> a = "Life is too short"
>>> len(a)
17
```









## 2. 인덱싱과 슬라이싱

### 2.1. 인덱싱

**인덱싱(Indexing)**이란 특정 위치를 **"가리킨다"(참조)**는 의미이다.

* 인덱싱 - [] 기호

```python
# 문자열 인덱싱

print("안녕하세요"[0])
print("안녕하세요"[1])
print("안녕하세요"[-3])
print("안녕하세요"[-2])
print("안녕하세요"[-1])
```

```python
# 문자열 인덱싱

>>> a = "Life is too short, You need Python"
>>> a[0]
'L'
>>> a[12]
's'
>>> a[-1]
'n'
```





#### - IndexError ( index out of rage ) 예외

가장 많이 만나는 예외 중 하나이다. 

```python
a = "ABCDEF"
# 시작에 len(a) 이상의 인덱스 사용시

a[1000]
```

리스트/문자열의 수를 넘는 요소/글자를 선택할 때 발생한다.

[참고] 슬라이싱은 Index Error가 발생하지 않는다. ( 주의하기 )







### 2.2. 슬라이싱

**슬라이싱(Slicing)**은 특정 부분을 **"잘라낸다"(추출)**는 의미이다. 

* 슬라이싱 - [:] 기호

```python
# 문자열 슬라이싱

print("안녕하세요"[0])
print("안녕하세요"[1])
print("안녕하세요"[0:2])
print("안녕하세요"[-3])
print("안녕하세요"[-2])
print("안녕하세요"[-1])
print("안녕하세요"[-3:])
```

```python
# 문자열 슬라이싱

>>> a = "Life is too short, You need Python"
>>> a[0:4]
'Life'
```

* 슬라이싱 기법으로 a[시작 번호:끝 번호]를 지정할 때 **<u>끝 번호에 해당하는 것은 포함하지 않기 때문</u>**이다. 
  a[0:3]을 수식으로 나타내면 다음과 같다. ( 0 <= a < 3 )





a[시작 번호:끝 번호]에서 끝 번호 부분을 생략하면 시작 번호부터 그 문자열의 끝까지 뽑아낸다.

```python
>>> a[19:]
'You need Python'
```

a[시작 번호:끝 번호]에서 시작 번호를 생략하면 문자열의 처음부터 끝 번호까지 뽑아낸다.

```python
>>> a[:17]
'Life is too short'
```

a[시작 번호:끝 번호]에서 시작 번호와 끝 번호를 생략하면 문자열의 처음부터 끝까지를 뽑아낸다.

```python
>>> a[:]
'Life is too short, You need Python'
```

슬라이싱에서도 인덱싱과 마찬가지로 마이너스(-) 기호를 사용할 수 있다.

```python
>>> a[19:-7]
'You need'
```

위 소스 코드에서 a[19:-7]이 뜻하는 것은 a[19]에서부터 a[-8]까지를 말한다. 이 역시 a[-7]은 포함하지 않는다.



```python
a = "ABCDEF"

# 시작에 len(a) 이상의 인덱스 사용시
a[1000:]
```

너무 큰 숫자를 넣으면 ''빈 문자열이 출력된다.





#### 1) **슬라이싱으로 문자열 나누기**

```python
>>> a = "20010331Rainy"
>>> year = a[:4]
>>> day = a[4:8]
>>> weather = a[8:]
>>> year
'2001'
>>> day
'0331'
>>> weather
'Rainy'
```





#### **2) 문자열 [ 숫자 : 숫자 : 스텝 ] ★**

```bash
>>> print("0123456789"[::3])
0369
>>> print("0123456789"[::-1]) # 확장 슬라이싱 이라고 불리기도 한다. extended Slices
9876543210
```

스텝(step)에 음수를 사용하면 역순으로 가져옵니다.

```python
a = "ABCDEF"

# 음의 스텝을 사용할 때는 시작과 종료도 순서가 역순이어야 합니다.
# ABCDEF
# 012345
a[-1:0:-1]
```

```python
a = "ABCDEF"

# 종료를 생략하면 마지막까지 포함
a[-1::-1]
```





**[ "Pithon"이라는 문자열을 "Python"으로 바꾸려면? ]**

Pithon 문자열을 Python으로 바꾸려면 어떻게 해야 할까? 제일 먼저 떠오르는 생각은 다음과 같을 것이다.

```python
>>> a = "Pithon"
>>> a[1]
'i'
>>> a[1] = 'y'
```

즉 a 변수에 "Pithon" 문자열을 대입하고 a[1]의 값이 i니까 a[1]을 y로 바꾸어 준다는 생각이다. 

하지만 결과는 오류가 발생한다. 왜냐하면 문자열의 요솟값은 바꿀 수 있는 값이 아니기 때문이다.
(문자열 자료형은 그 요솟값을 변경할 수 없다. 그래서 immutable한 자료형이라고도 부른다).

하지만 앞에서 살펴본 슬라이싱 기법을 사용하면 Pithon 문자열을 사용해 Python 문자열을 만들 수 있다.

```python
>>> a = "Pithon"
>>> a[:1]
'P'
>>> a[2:]
'thon'
>>> a[:1] + 'y' + a[2:]
'Python'
```





#### 3) 슬라이싱과 함수

두 번째 원소부터 끝 원소까지의 합을 구할 때 slicing, sum을 함께 사용하면 한번에 계산이 가능합니다.

**python3 코드**

```python
n = int(input())
arr = list(map(int, input().split()))

sum_val = sum(arr[1:])

print(sum_val)
```

**출력결과**

```
>> 5
>> 1 2 3 4 5

14
```


