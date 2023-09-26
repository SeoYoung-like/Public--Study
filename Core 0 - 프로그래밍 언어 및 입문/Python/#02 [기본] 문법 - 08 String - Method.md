# 문자열 메서드

문자열 자료형은 자체적으로 함수를 가지고 있다. 
이들 함수를 다른 말로 문자열 내장 함수라 한다. 

이 내장 함수를 사용하려면 문자열 변수 이름 뒤에 ‘.’를 붙인 다음에 함수 이름을 써주면 된다. 







### 1. 문자 개수 및 위치값 ( index )

#### 문자 개수 세기 ( count )

문자열 중 문자 b의 개수를 리턴한다.

**[주의!]** 소문자 대문자를 가린다.

```python
>>> a = "hobby"
>>> a.count('b')
2
```

```python
>>> 'apple pineapple'.count('pl')
2
```





#### 위치 알려주기1 ( find ) ★

* find() : **왼쪽**부터 찾아서 **처음 등장**하는 **위치**를 찾습니다.
* rfind() : **오른쪽**부터 찾아서 **처음 등장**하는 **위치**를 찾습니다.

문자열 중 문자 b가 처음으로 나온 위치를 반환한다. 
만약 찾는 문자나 문자열이 존재하지 않는다면 -1을 반환한다.

```python
>>> a = "Python is the best choice"
>>> a.find('b')
14
>>> a.find('k')
-1
```

---

```
>>> output_a = "안녕안녕하세요".find("안녕")
>>> print(output_a)
0
>>> output_b = "안녕안녕하세요".rfind("안녕")
>>> print(output_b)
2
>>> 'apple pineapple'.find('pl')
2
>>> 'apple pineapple'.find('xy')
-1
>>> 'apple pineapple'.rfind('pl')
12
>>> 'apple pineapple'.rfind('xy')
-1
```

---

**-1**





#### 위치 알려주기2 ( index )

* **index('찾을문자열')** : 왼쪽에서부터 특정 문자열을 찾아서 인덱스를 반환합니다. 단, 문자열이 없으면 에러를 발생시킵니다. 문자열이 여러 개일 경우 처음 찾은 문자열의 인덱스를 반환합니다.
* **rindex('찾을문자열')** : 오른쪽에서부터 특정 문자열을 찾아서 인덱스를 반환합니다. 단, 문자열이 없으면 에러를 발생시킵니다. 문자열이 여러 개일 경우 처음 찾은 문자열의 인덱스를 반환합니다.

<u>앞의 find 함수와 다른 점은 문자열 안에 존재하지 않는 문자를 찾으면 **오류**가 발생</u>한다는 점이다.

```python
>>> a = "Life is too short"
>>> a.index('t')
8
>>> a.index('k')
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
ValueError: substring not found
```

문자열 중 문자 t가 맨 처음으로 나온 위치를 반환한다. 만약 찾는 문자나 문자열이 존재하지 않는다면 오류를 발생시킨다. 

```python
>>> 'apple pineapple'.index('pl')
2
>>> 'apple pineapple'.rindex('pl')
12
```













### 2. 공백 지우기 

#### 왼쪽 공백 지우기 ( lstrip ) ★

문자열 중 가장 왼쪽에 있는 한 칸 이상의 연속된 공백들을 모두 지운다. 
lstrip에서 l은 left를 의미한다.

```python
>>> a = " hi "
>>> a.lstrip()
'hi '
```



#### 오른쪽 공백 지우기 ( rstrip ) ★

문자열 중 가장 오른쪽에 있는 한 칸 이상의 연속된 공백을 모두 지운다. 
rstrip에서 r는 right를 의미한다.

```python
>>> a= " hi "
>>> a.rstrip()
' hi'
```



#### 양쪽 공백 지우기 ( strip ) ★

문자열 양쪽에 있는 한 칸 이상의 연속된 공백을 모두 지운다.

```python
>>> a = " hi "
>>> a.strip()
'hi'
```





##### (응용) 특정 문자 삭제하기

lstrip, rstrip, strip을 이용해서 문자열에서 특정 문자를 삭제해보겠습니다.

**lstrip('삭제할문자들'), rstrip('삭제할문자들'), strip('삭제할문자들')**

```python
>>> ', python.'.strip(',.')
' python'
```





##### **(보충)** **구두점을 간단하게 삭제하기**

string 모듈의 punctuation에는 모든 구두점이 들어있습니다. 다음과 같이 strip 메서드에 string.punctuation을 넣으면 문자열 양쪽의 모든 구두점을 간단하게 삭제할 수 있습니다.

```python
>>> import string
>>> ', python.'.strip(string.punctuation)
' python'
>>> string.punctuation
'!"#$%&\'()*+,-./:;<=>?@[\\]^_`{|}~'
```

만약 공백까지 삭제하고 싶다면 string.punctuation에 공백 ' '을 연결해서 넣어주면 되겠죠?

```python
>>> ', python.'.strip(string.punctuation + ' ')
'python'
```

물론 메서드 체이닝을 활용해도 됩니다.

```python
>>> ', python.'.strip(string.punctuation).strip()
'python'
```







---





### 3. 대소문자 바꾸기

#### 소문자를 대문자로 바꾸기 ( upper ) ★

```python
>>> a = "hi"
>>> a.upper()
'HI'
```

upper 함수는 소문자를 대문자로 바꾸어 준다. 만약 문자열이 이미 대문자라면 아무 변화도 일어나지 않을 것이다.



#### 대문자를 소문자로 바꾸기 ( lower ) ★

```python
>>> a = "HI"
>>> a.lower()
'hi'
```

lower 함수는 대문자를 소문자로 바꾸어 준다.





#### 첫 글자를 대문자로 바꾸기 ( capitalize )

```python
>>> "abc def".capitalize() # 첫 글자를 대문자로
'Abc def'
```



#### 각 단어의 첫 글자를 대문자로 바꾸기 ( title )

```python
>>> "abc def".title() # 각 단어의 첫 글자를 대문자로
'Abc Def'
```















### 4. 문자열 결합 및 바꾸기

#### 문자열 결합 ( join )

구분자 문자열과 이터러블의 요소를 연결하여 새로운 문자열로 만듭니다. 

* **'구분자 문자열'.join(이터러블)**

```python
>>> ",".join('abcd')
'a,b,c,d'
```

abcd 문자열의 각각의 문자 사이에 ','를 삽입한다.
보통 리스트와 튜플에 사용한다.

join 함수의 입력으로 리스트를 사용하는 예는 다음과 같다.

```python
>>> ",".join(['a', 'b', 'c', 'd'])
'a,b,c,d'
```



#### 문자열 바꾸기 ( replace ) - 전체

문자열 안의 문자열을 다른 문자열로 바꿉니다(문자열 자체는 변경하지 않으며 바뀐 결과를 반환합니다).

* **replace('바꿀 문자열', '새 문자열')**

```python
>>> a = "Life is too short"
>>> a.replace("Life", "Your leg")
'Your leg is too short'
>>> a
"Life is too short"
```



#### 문자열 바꾸기 ( **translate** ) - 대응 ( 테이블 )

translate는 문자열 안의 문자를 다른 문자로 바꿉니다. 먼저 **str.maketrans('바꿀문자', '새문자')**로 변환 테이블을 만듭니다. 그다음에 **translate(테이블)**을 사용하면 문자를 바꾼 뒤 결과를 반환합니다. 다음은 문자열 'apple'에서 a를 1, e를 2, i를 3, o를 4, u를 5로 바꿉니다.

* **translate(테이블)**

```python
>>> table = str.maketrans('aeiou', '12345')
>>> 'apple'.translate(table)
'1ppl2'
```







### 5. 문자열 구성 파악하기

#### 마지막 문자열이 어떻게 끝나는지 확인  ( endswith )

```python
filename = "blakpink.png"
filename.endswith("png") # filename의 마지막이 "png"로 끝나는지 확인합니다.
```





#### 문자열의 구성 파악하기 ( isOO ) ★

문자열이 특정 값으로 구성, 인식, 사용 할 수 있는 확인하는 함수 모음이다.

* isalnum() : **알파벳 또는 숫자**로만 **구성** 되어 있는지 **확인**
* isalpha() : **알파벳으로만** **구성**되어 있는지 **확인**
* isidentifier() : **식별자**로 사**용할 수 있는 것**인지 **확인**
* isdecimal() : **정수 형태**인지 **확인**
* isdigit() : **숫자**로 **구분 되는 범위**인지 **확인** ★
* isnumeric() : **숫자**로 **구분 되는 범위**인지 **확인** ( isnumeric이 좀 더 폭넓은 의미로 수를 취급한다. ) ★
* isspace() : **공백**으로 **구성**되어 있는지 **확인**
* islower() : **소문자**로만 **구성**되어 있는지 **확인**
* isupper() : **대문자**로만 **구성**되어 있는지 **확인**

```python
>>> print("TrainA10".isalnum())
True
>>> print("10".isdigit())
True
```

```python
>>> txt = "1234"
>>> txt.isdigit() # 모든 글자가 숫자인지를 확인합니다. input()과 함께 많이 사용됩니다.
True
```

>  위에서 소개한 문자열 관련 함수는 문자열 처리에서 사용 빈도가 매우 높고 유용하다. 
>
>  이 외에도 몇 가지가 더 있지만 자주 사용되지는 않는다.







### 6. 문자열 채우기

#### 문자열 정렬과 글자 채우기  ( rjust, ljust, center )

문자열을 정렬할 때 사용하는 String에 속한 메소드

[참고] 한글에서는 이 방식이 제대로 작동하지 않습니다.

```python
# .ljust() 메써드는 모자르는 글자수 만큼 빈칸을 넣어줍니다.

"ABCDEFG".ljust(10) 	# 길이를 10으로 만든 뒤 오른쪽으로 정렬하고 남는 공간을 공백으로 채웁니다.
----------------------
[ 실행결과 ]
'ABCDEFG   '
```

- rjust( n , c=' ') : 문자열을 오른쪽으로 n만큼 정렬함. 빈칸은 c로 채워 넣는다.

- ljust( n , c=' ') : 문자열을 왼쪽으로 n만큼 정렬함. 빈칸은 c로 채워 넣는다.

```python
a="abc"
print(a.rjust(10))
print(a.rjust(10,'#'))

b="def"
print(a.ljust(15))
print(a.ljust(15,'k'))
```

```
       abc
#######abc
abc            
abckkkkkkkkkkkk
```



* center( n , c='') : 문자열을 지정된 길이로 만든 뒤 가운데로 정렬하며 남는 공간을 공백으로 채웁니다. 

```python
>>> 'python'.center(10)
'  python  '
```

만약 가운데로 정렬했을 때 전체 길이와 남는 공간이 모두 홀수가 된다면 왼쪽에 공백이 한 칸 더 들어갑니다. 예를 들어 길이가 6인 'python'을 11로 가운데 정렬하면 5가 남아서 왼쪽에 공백 3칸, 오른쪽에 공백 2칸이 들어갑니다.

```python
>>> 'python'.center(11)
'   python  '
```

```python
>>> 'python'.center(11, "#")
'###python##'
```



##### (보충) 매써드 체이닝

문자열 메서드는 처리한 결과를 반환하도록 만들어져 있습니다. 따라서 메서드를 계속 연결해서 호출하는 메서드 체이닝이 가능합니다. 메서드 체이닝은 메서드를 줄줄이 연결한다고 해서 메서드 체이닝(method chaining)이라 부릅니다.

다음은 문자열을 오른쪽으로 정렬한 뒤 대문자로 바꿉니다.

```python
>>> 'python'.rjust(10).upper()
'    PYTHON'
```

사실 문자열을 입력받을 때 자주 사용했던 input().split()도 input()이 반환한 문자열에 split을 호출하는 메서드 체이닝입니다.





#### 문자열 앞에 0으로 채우기 ( zfill )

**zfill(길이)**는 지정된 길이에 맞춰서 문자열의 왼쪽에 0을 채웁니다( **z**ero **fill**을 의미). 
단, 문자열의 길이보다 지정된 길이가 작다면 아무것도 채우지 않습니다. 

보통 zfill은 숫자를 일정 자릿수로 맞추고 앞자리는 0으로 채울 때 사용합니다.

```python
print( "3".zfill(3) )
# 실행결과 : 003
```

```python
print( "s".zfill(4) )
# 실행결과 : 000s
```

```python
for x in range(3):
    print( str(x).zfill(4) )
""" 
실행결과
0000
0001
0002
"""
```

```python
>>> '35'.zfill(4)        # 숫자 앞에 0을 채움
'0035'
>>> '3.5'.zfill(6)       # 숫자 앞에 0을 채움
'0003.5'
>>> 'hello'.zfill(10)    # 문자열 앞에 0을 채울 수도 있음
'00000hello'
```





#### 아스키코드 함수 ( ord / chr )

*  python에서 ord('A') 코드를 실행하게 되면 65라는 값을 받게 됩니다.
*  python에서 chr(65) 코드를 실행하게 되면 'A'를 받게 됩니다.

```python
>> print(ord('A'))
65

>> print(chr(65))
'A'
```





