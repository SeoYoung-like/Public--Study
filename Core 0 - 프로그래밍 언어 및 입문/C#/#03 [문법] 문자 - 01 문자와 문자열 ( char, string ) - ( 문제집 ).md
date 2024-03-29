# 01-04. 문자와 문자열

**[핵심] 컴퓨터에서 모든 것은 숫자로 이루어져 있다.**



## 1. 문자

### 1.1. 데이터 타입

* **컴퓨터에서 문자는 무엇인가?**
  * 모든 문자는 사실 숫자다.



* **문자로 쓰는 데이터 타입은?**
  * 문자코드 특징 때문에 대부분 unsigned를 기본형으로 한다.

  * 각 언어마다 문자를 주로 쓰는 데이터 타입은 다르다.
  
  * ' '(작은따옴표)를 사용한다. 



* C#에서 주로 문자코드를 사용하는 형은 무엇이고, 몇 바이트 인가?
  * char 
  * 2바이트
  * 유니코드



### 1.2. 문자 코드

* **문자열 셋 / 문자열 세트 ( Character Set )은 무엇인가?** 
  * 사용자가 입력한 문자나 기호들을 컴퓨터가 이용할 수 있는 숫자로 만드는 것
  * 숫자에 대응되는 할당 문자들의 집합



* **문자열 인코딩 ( Encoding )이란?**
  * ( 문자 => 숫자 ) 변환
  * 문자열 셋을 통해 사람이 입력한 문자를 그에 해당하는 숫자로 변환 하는 것



* **ASCII 코드는 무엇인가?** 

  * 표준 코드체계 이다.
  * 미국 ANSI에서 표준화한 정보 교환용 7비트 부호체계이다.  

  ---

  * 최초의 아스키 총 128개의 문자
  * 7 bit
    0000 0000  ~  0111 1111
           0	   ~         127
  * 1 bit - 남은 비트 1개
    사용을 안 하거나, 오류 검증용으로 사용

  ---



* **Extended ASCII ( 확장 아스키 ) 란 무엇인가?**
  * ASCII가 1비트가 남다 보니 각 나라마다 이 1비트를 가지고 다양한 언어가 추가하게 된다.
  * 하지만 이런 인코딩 방식이 중구난방으로 만들어지다 보니 호환이 안되 서로 다른 문자 인코딩을 사용하여 글자가 깨지는 일이 빈번히 발생하게 되었다.



* **Unicode 란 무엇인가?** 
  * Extended ASCII 의 호환성 문제를 해결하게 된 방식이다.
  * 전 세계의 모든 문자를 다루도록 설계된 표준 문자 전산 처리 방식으로 그 개수는 고어까지 포함되면서 비트 수의 범위가 늘어나고 있다.
  * 문자열 셋을 통일 하게 되면서 호환성 문제에서 벗어나 다양한 문자로 온라인에 소통할 수 있게 되었다.
    * 호환성을 이유로 **<u>UTF-8</u>** 형식이 가장 많이 사용되고 있다.  ( UTF 16, UTF 32 등 형식이 다양하다. )
  * **2바이트 ( 16비트 )**



* **Unicoe와 ASCII 코드의 동일성을 말하시오.**
  * 유니코드의 첫 부분은 ASCII 하고 동일하다.
    ( 유니코드의 첫 128 바이트는 아스키와 완전히 동일하다. )







## 2. 문자열 ( String )

* **문자열은 어떤 데이터 타입인가?**
  * 문자열은 자체는 하드웨어가 이해하는 기본 자료형은 아니다.
    ( 하드웨어 - 컴퓨터가 1:1 이해할 수 있는 데이터가 아니다. )
    
  * 여러 개의 문자가 모인 집합체 
    ( 문자가 줄줄이 연결 된 거라 생각하면 된다. )
    
    * 문자열은 큰 따옴표("")로 감싼다.
    * 문자열은 문자형(char)의 배열
    * **문자열 : 모든 것을 읽어 올 수 있는 형태인 포괄적인 형태의 상위 개념**
    
    



* **문자열에서 사용할 수 있는 연산자는 무엇이 있는가?**
  * [주의!] 프로그래밍 언어마다 문자열에 사용 가능한 연산자가 다르다. 
    * 이는 컴퓨터 프로그래밍 언어마다 문자열 동작 방식이 다르며 '기본 자료형'이 아니기 때문이다. 
  * 아래의 연산자들은 그 중에서도 주로 사용 가능한 연산자를 서술한 것이다. ( 항상은 아니다. )
  * `+`연산자를 활용해서 두 문자열을 합칠 수 있다.
  * `==` 두 문자열이 같은지 확인한다.





