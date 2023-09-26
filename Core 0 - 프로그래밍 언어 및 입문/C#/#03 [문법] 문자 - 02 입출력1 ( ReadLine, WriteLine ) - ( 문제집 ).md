# 01-05 입출력1 ( ReadLine, WriteLine )



* **Console.ReadLine()은 어떤 함수인가?**
  * Console은 명령 프롬프트를 말한다.
  * 문자열을 입력하는 함수이다. 
  * 반환 값은 String이다. ( 개행 포함 - \n )



* **'문자열'은 형 변환을 어떻게 할까?**
  * 문자열은 '묵시적', '명시적' 형 변환이 불가능 하다.
    * 컴파일 error - 발생
  * 특정 함수를 사용해줘야 한다. 
    * <T>.Parse()라는 함수를 사용해야 한다.



* **Parse()는 어떤 함수인가?**

  * 공백을 제외한 데이터를 해석해서 변환시켜준다.

  * 다른 프로그래밍 언어에도 이런 유사한 함수들이 존재한다.

  * 문자열이 숫자 외의 값을 인자로 가질 경우 예외 ( exception ) 발생

    ```c#
    int result = int.Parse("a");
    ```

    ---

    **코드**

    ```c#
    int num1 = int.Parse(Console.ReadLine());
    long num2 = long.Parse(Console.ReadLine());
    Console.WriteLine(num1);
    Console.WriteLine(num2);
    ```

    **실행**

    ```c#
         25     // int.Parse(Console.ReadLine())
      9999999   // long.Parse(Console.ReadLine())
    ```

    ```c#
    25			// num1 = 25
    9999999		// num2 = 9999999
    ```






* **Console.WriteLine()은 어떤 함수인가?**
  * Console은 명령 프롬프트를 말한다.
  * 문자열을 출력하는 함수이다. 
  * 개행 한다.



* **Escape character은 무엇이낙?**

  * 그 의미에 맞게 문법에서 탈출시키거나 특별한 방식으로 출력하는 문자다.
  * 역슬래스 ( \ )롤 시작하는 특수 문자
    * 한국 키보드의 경우 원화기호 ( ￦ ) 

  

* **16진수 아스키값으로 출력하시오.**

  ```C#
  Console.WriteLine("\x48\x65\x6C\x6C\x6F\x20\x57\x6F\x72\x6C\x64\x21");
  ```

  ```
  Hello World!
  ```

  * \x{숫자} : 16진수 출력
    (ex) \x48 : 'H'



* **double형 변수 d를 선언 하자마자 값을 입력받아 초기화 하시오.**

  ```cs
  double d = double.Parse(input.ReadLine());
  ```

  
