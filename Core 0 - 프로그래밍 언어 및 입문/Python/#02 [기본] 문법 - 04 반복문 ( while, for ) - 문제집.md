## 1. while 문

* **다음 코드의 결과 값은 어떻게 되는가?** 123

  * ```py
    # 변수를 선언합니다.
    list_test = [1, 2, 1, 2]
    value = 2
    
    # list_test 내부에 value가 있다면 반복
    while value in list_test:
        list_test.remove(value)
    
    # 출력합니다.
    print(list_test)
    ```

    |

    * ```
      [1, 1]
      ```





## 2. for 문

* **for문과 in 연산자 중 in뒤에 들어가는 데이터라고 뭐라고 하는가?** 123
  * 이터러블 객체 (or 루프 제어 변수)라고 부른다.
    * 주로 범위형 객체들(컨테이너 객체)이 이에 해당한다.
  * [참고] 아이템이 대입되는 대상이라는 의미에서 <u>대상(target)</u>이라고 부르기도 합니다.



* **[참고] for문에서 사용하는 in 독특한 방식으로 사용된다.** ㅇㅇㅇ

  * 매 루프마다 루프 제어 변수에 이터러블(iterable)의 아이템들이 하나씩 대입됩니다. 

  * 다른 변수들과 동일한 방법으로 사용할 수 있으며 이름도 변수명 규칙에 따라 마음대로 지을 수 있습니다.

  * ```py
    # for-else 예시
    for i in [8, 3, 5]:
        j = i * 10
        print(j)
    else:
        print("끝났어요")
    ```

  * ```
    80
    30      
    50      
    끝났어요
    ```

    

* **range 함수는 무엇인가?**  123
  
  *  range 타입의 객체를 만들 수 있는 함수이다. 
    * 정수 범위(range)를 만들어낼 수 있습니다. 
  * 보통 ```for```문과 함께 사용됩니다.



* **range 함수의 기본 구조를 말하시오. **123
  * ```range(시작, 종료, 스텝)```
  * 시작, 종료, 스텝의 의미는 슬라이싱과 비슷하지만 함수 괄호 안에서는 컴마(```,```)로 구분합니다..



* **range(0, 5)는 어떤 숫자가 포함되어 있나?** 123
  * 0이상 5미만의 숫자를 포함한 객체 : 0, 1, 2, 3, 4
  * [주의!] 마지막 끝 숫자는 포함되지 않는다.



* **[참고] range 무한 루프** ㅇㅇㅇ
  * 만약 종료 값에 도달 할 수 없다면 무한 루프가 발생한다. (ex) range(10, 11, -1)



* **[참고] 버전별 range 차이점** ㅇㅇㅇ

  * 파이썬 2.7과 파이썬 3에서 range는 결과가 조금 다릅니다. 파이썬 2.7에서는 range를 사용하면 실제로 연속된 숫자가 들어있는 리스트를 만들어 내지만 파이썬 3에서는 range 객체(반복 가능한 객체)를 만들어냅니다.

  * 파이썬 2.7의 range는 리스트를 만들어내므로 아주 큰 숫자를 지정하면 메모리를 많이 사용합니다. 그래서 보통 파이썬 2.7에서 리스트 대신 객체를 생성할 때는 xrange를 사용합니다. 그래서 파이썬 3에서는 range가 객체를 생성하는 방식으로 바뀌었습니다.
  
  * ```py
    # 파이썬 2.7
    
    >>> range(10)
    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    ```
  
  * ```python
    # 파이썬 3
    
    >>> range(10)
    range(0, 10)
    >>> list(range(10))    # range 객체를 리스트로 만듦
    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    ```



* **python 반복문(for, while)에서 특이한 사용법은 무엇인가? ( 1가지 )** 123
  * for문 while문 모두 else문을 사용할 수 있다.
  * [주의!] 반복 루프가 ```break```로 종료될 경우에는 ```else:```가 무시됩니다. 



* **[참고] for문,  while문 - else사용** ㅇㅇㅇ

  * ```python
    while 조건:
        조건이 True일 때 실행될 명령문들
    else:
        반복이 (break없이) 끝났을 때 실행될 명령문들
    ```

  * ```py
    my_list = [0, 5, 2, 8, 9, 3, 11, 5, 2]
    
    for i in my_list:
        print(i, end=" ")
        if i == 3:
            print("!3을 찾았습니다!")
            break
    else:
        print("3을 찾지 못했습니다.")
    ```



* **[참고] 실전 예문** ㅇㅇㅇ

  * ```python
    marks = [90, 25, 67, 45, 80]
    for number in range(len(marks)):
        if marks[number] < 60: 
            continue
        print("%d번 학생 축하합니다. 합격입니다." % (number+1))
    ```



* **[참고]  for문 - ( _  )생략 **ㅇㅇㅇ

  * for문에서 i가 쓰이지 않는 경우라면 i를 사용하지 않겠다는 뜻으로 대신 `_`를 이용하기도 합니다. 

  * 이는 가독성 측면에서 좋은 코드를 작성하기 위해 꼭 필요합니다. 

    * [숙제] 과거에 사용하던 방식이라는 이야기도 있으니 개념을 직접 찾아서 검증해 보자. 

  * ```py
    n = int(input())
    for _ in range(n):
        print("A", end="")
    ```

    ```
    >> 3
    
    AAA
    ```

    
