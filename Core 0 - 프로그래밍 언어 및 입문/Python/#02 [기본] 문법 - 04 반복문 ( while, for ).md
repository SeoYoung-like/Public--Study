# 03 반복문 ( while, for )

반복을 의미하는 영어 단어로는 repeat과 iterate가 있다. 

* repeat : 단순하게 그대로 반복만 하는 것
* iterate : 프로그래밍에서 약간씩 변화를 주며 반복하는 것 

한 바퀴 돌아와서 다시 시작한다는 의미로 루프(loop)를 만든다고 표현하기도 합니다.

---

* ```for```문과 ```while```문은 이론상으로는 서로 호환이 가능하지만 실제로는 용도가 약간 다릅니다.





## 1. while문

### 1.1. continue 문

```python
a = 0
while a < 10:
  a = a + 1
  if a % 2 == 0:
    continue
  print(a)
```

```python
# 실행결과
1
3
5
7
9
```





### 1.2. break 문

반복문을 벗어날 때 사용하는 키워드다.

```python
# 변수를 선언합니다.
i = 0

# 무한 반복합니다.
while True:
    # 몇 번째 반복인지 출력합니다.
    print("{}번째 반복문입니다.".format(i))
    i = i + 1
    # 반복을 종료합니다.
    input_text = input("> 종료하시겠습니까?(y): ")
    if input_text in ["y", "Y"]:
        print("반복을 종료합니다.")
        break
```

```python
# 실행결과
0번째 반복문입니다.
> 종료하시겠습니까?(y): n
1번째 반복문입니다.
> 종료하시겠습니까?(y): n
2번째 반복문입니다.
> 종료하시겠습니까?(y): n
3번째 반복문입니다.
> 종료하시겠습니까?(y): y
반복을 종료합니다.
```





### 1.3. 다양한 반복 방식

#### 1) 상태 기반 - 반복하기 ( in )

해당하는 값을 모두 제거한다.

```python
# 변수를 선언합니다.
list_test = [1, 2, 1, 2]
value = 2

# list_test 내부에 value가 있다면 반복
while value in list_test:
    list_test.remove(value)

# 출력합니다.
print(list_test)
```





#### 2) else 사용

```python
while 조건:
    조건이 True일 때 실행될 명령문들
else:
    반복이 (break없이) 끝났을 때 실행될 명령문들
```

반복 루프가 ```break```로 종료될 경우에는 ```else:```가 무시됩니다. ( for문도 동일 하다. )









## 2. for문

### **2.1. 기본 구조와 이터러블 객체**

```python
for 변수 in 이터러블-객체:
    수행할 문장1
    수행할 문장2
    ...
```



#### 1) 이터러블 객체

여기서 ```in```과 ```:``` 사이에는 반복에 사용할 수 있는(**iterable, 이터러블**) 객체가 들어갈 수 있습니다. 
예를 들어서 int나 float같은 숫자 자료형들의 객체는 들어갈 수 없고 <u>list나 tuple같은 컨테이너형의 객체</u>들은 들어갈 수 있습니다. 정수 범위에 대해 반복을 할 때는 범위(<u>range</u>)형의 객체를 만들어서 사용할 수 있습니다. ```변수```에는 이터러블이 제공해주는 아이템들이 차례대로 대입됩니다.

교재에 따라서 이 변수를 <u>루프 제어 변수(loop control variable)</u>라고 부르기도 하고 아이템이 대입되는 대상이라는 의미에서 <u>대상(target)</u>이라고 부르기도 합니다.

[참고] 이터러블 객체를 제외한 객체를 대입할 경우 TypeError가 발생한다. 

```python
# 어떤 객체가 iterable 한지 확인하는 방법

from collections.abc import Iterable

print(isinstance(1, Iterable))
print(isinstance([1, 2, 3], Iterable))
print(isinstance(range(3), Iterable))
```

```
False
True
True
```



매 루프마다 루프 제어 변수에 이터러블(iterable)의 아이템들이 하나씩 대입됩니다. 
다른 변수들과 동일한 방법으로 사용할 수 있으며 이름도 변수명 규칙에 따라 마음대로 지을 수 있습니다.

```python
# for 예시
for i in [8, 3, 5]:  # i에는 8, 3, 5이 순서대로 대입됩니다.
    j = i * 10
    print(j)
```

```
80
30
50
```

---

```python
# for-else 예시
for i in [8, 3, 5]:
    j = i * 10
    print(j)
else:
    print("끝났어요")
```





#### 2) range

```range()``` 함수를 이용해서 range 타입의 객체를 만들 수 있다. ( 정수 범위(range)를 만들어낼 수 있습니다. ) 
보통 ```for```문과 함께 사용됩니다.

```python
type(range(5))
```

괄호 안에 3가지의 인수(argument)를 넣어서 범위를 조절할 수 있습니다.

```range(시작, 종료, 스텝)```

시작, 종료, 스텝의 의미는 슬라이싱과 비슷하지만 함수 괄호 안에서는 컴마(```,```)로 구분합니다..









### 2.2. 다양한 for문  

#### 1) 리스트, 튜플

자주 사용하는 전형적인 for문이다.

```python
>>> test_list = ['one', 'two', 'three'] 
>>> for i in test_list: 
...     print(i)
... 
one 
two 
three
```

---

```python
my_list = [{1, 2, 3}, (4, 5, 6)]

for i in my_list:
    print(type(i))
```

```
<class 'set'>
<class 'tuple'>
```



##### - 리스트와 튜플 결합 형태

리스트와 튜플이 결합한 형태를 사용하는 방식이다.

```python
>>> a = [(1,2), (3,4), (5,6)]
>>> for (first, last) in a:
...     print(first + last)
...
3
7
11
```

 a 리스트의 요솟값이 튜플이기 때문에 각각의 요소가 자동으로 (first, last) 변수에 대입된다.







#### 2) **range**

for문은 숫자 리스트를 자동으로 만들어 주는 range 와 함께 사용하는 경우가 많다. 
다음은 range 함수의 간단한 사용법이다.

* **range(시작, 종료, 스텝)**

  [주의!] 만약 종료 값에 도달 할 수 없다면 무한 루프가 발생한다. (ex) range(10, 11, -1)

```python
# range(10) : 0부터 10 미만의 숫자 ( value )

>>> a = range(10)
>>> a
range(0, 10)
```

range(10)은 0부터 10 미만의 숫자를 포함하는 **range 객체**를 만들어 준다.
시작 숫자와 끝 숫자를 지정하려면 range(시작 숫자, 끝 숫자) 형태를 사용하는데, 이때 끝 숫자는 포함되지 않는다.

**[주의!]** range는 value 값의 나열을 나타내는 것이지 index값이 아니다 혼동하지 말자.

---

**| 참고 |** **버전별 range의 차이점**

파이썬 2.7과 파이썬 3에서 range는 결과가 조금 다릅니다. 파이썬 2.7에서는 range를 사용하면 실제로 연속된 숫자가 들어있는 리스트를 만들어내지만 파이썬 3에서는 range 객체(반복 가능한 객체)를 만들어냅니다.

```python
# 파이썬 2.7

>>> range(10)
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

```python
# 파이썬 3

>>> range(10)
range(0, 10)
>>> list(range(10))    # range 객체를 리스트로 만듦
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

파이썬 2.7의 range는 리스트를 만들어내므로 아주 큰 숫자를 지정하면 메모리를 많이 사용합니다. 그래서 보통 파이썬 2.7에서 리스트 대신 객체를 생성할 때는 xrange를 사용합니다. 그래서 파이썬 3에서는 range가 객체를 생성하는 방식으로 바뀌었습니다.



---







##### (1) 반복 - range(0, 10)

```python
>>> list(range(0, 10))
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

> **[TIP]** 포함을 강조하고 싶을 때
>
> 10을 반드시 포함해야 한다는 것을 강조하고 싶을 때 다음과 같이 작성한다.
>
> ```python
> >>> list(range(0, 10 + 1)) 		#10 포함 강조
> [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
> ```
>



**for 문**

```python
list_a = list(range(0, 10))

for i in range(0,10):
	print(list_a[i], end=" ")
```

```bash
#실행결과
0 1 2 3 4 5 6 7 8 9 
```





##### (2) 특정 크기 반복 - range(0, 10, 2) 

```python
>>> list(range(1, 10, 2))
[0, 2, 4, 6, 8]
```





##### (3) 반대로 반복 - range(10, 0 - 1, -1)

```python
>>> list(range(10, 0 - 1, -1))
[10, 9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
```







**for문 - 1**

```python
for i in range(10, 0 - 1, -1):
	print("현재 반복 변수: {0}".format(i))	# 0생략가능
```

```python
#실행결과
현재 반복 변수: 10
현재 반복 변수: 9
현재 반복 변수: 8
현재 반복 변수: 7
현재 반복 변수: 6
현재 반복 변수: 5
현재 반복 변수: 4
현재 반복 변수: 3
현재 반복 변수: 2
현재 반복 변수: 1
현재 반복 변수: 0
```



**for문 - 2**

```python
for i in reversed(range(10)):
	print("현재 반복 변수: {0}".format(i))		# 0생략가능
```

```python
#실행결과
현재 반복 변수: 9
현재 반복 변수: 8
현재 반복 변수: 7
현재 반복 변수: 6
현재 반복 변수: 5
현재 반복 변수: 4
현재 반복 변수: 3
현재 반복 변수: 2
현재 반복 변수: 1
현재 반복 변수: 0
```







**(X) 실전 예문 **

```python
marks = [90, 25, 67, 45, 80]
for number in range(len(marks)):
    if marks[number] < 60: 
        continue
    print("%d번 학생 축하합니다. 합격입니다." % (number+1))
```

<u>len 함수는 리스트 안의 요소 개수를 돌려주는 함수이다.</u> 

따라서 `len(marks)`는 5가 될 것이고 `range(len(marks))`는 `range(5)`가 될 것이다. 
number 변수에는 차례로 0부터 4까지의 숫자가 대입될 것이고, `marks[number]`는 차례대로 90, 25, 67, 45, 80 값을 갖게 된다. 

```python
# 구구단 예문

>>> for i in range(2,10):        # 1번 for문
...     for j in range(1, 10):   # 2번 for문
...         print(i*j, end=" ") 
...     print('') 
... 
2 4 6 8 10 12 14 16 18 
3 6 9 12 15 18 21 24 27 
4 8 12 16 20 24 28 32 36
5 10 15 20 25 30 35 40 45
6 12 18 24 30 36 42 48 54 
7 14 21 28 35 42 49 56 63 
8 16 24 32 40 48 56 64 72 
9 18 27 36 45 54 63 72 81
```







#### 3) else 사용

else를 필수로 사용하는 사용 할 필요는 없다.

```python
while 조건:
    조건이 True일 때 실행될 명령문들
else:
    반복이 (break없이) 끝났을 때 실행될 명령문들
```

반복 루프가 ```break```로 종료될 경우에는 ```else:```가 무시됩니다. ( for문도 동일 하다. )
예를 들어서 리스트 안에서 3을 만나면 종료되는 프로그램을 생각해보겠습니다.

```python
my_list = [0, 5, 2, 8, 9, 3, 11, 5, 2]

for i in my_list:
    print(i, end=" ")
    if i == 3:
        print("!3을 찾았습니다!")
        break
else:
    print("3을 찾지 못했습니다.")
```











#### 4) 중첩

```py
# i과 j가 어떻게 변하는지 디버거로 추적해봅시다.
for j in range(3):  # outer loop

    print(f"Line {j}: ", end="")

    for i in range(5):  # inner loop
        print(i, end="")

    print()  # 줄바꿈
```

```
Line 0: 01234
Line 1: 01234
Line 2: 01234
```



```python
# isinstance 아이템이 리스트인지 확인하며 합을 구한다.

my_list = [[1, 2, 3], [4, 5], [6], 7]

my_sum = 0

for my_item in my_list:
    if isinstance(my_item, list):
        for i in my_item:
            my_sum += i
    else:
        my_sum += my_item
        
my_sum
```

```
28
```







### 2.3. ( _  )생략 사용

for문에서 i가 쓰이지 않는 경우라면 i를 사용하지 않겠다는 뜻으로 대신 `_`를 이용하기도 합니다. 이는 가독성 측면에서 좋은 코드를 작성하기 위해 꼭 필요합니다. 

* [숙제] 과거에 사용하던 방식이라는 이야기도 있으니 개념을 직접 찾아서 검증해 보자. 

**python3 코드**

```python
n = int(input())
for _ in range(n):
    print("A", end="")
```

**출력결과**

```
>> 3

AAA
```
