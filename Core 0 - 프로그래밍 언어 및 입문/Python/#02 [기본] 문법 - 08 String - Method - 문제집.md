# 문자열 메서드

* **공백이나 특정 문자를 지우는 메서드를 나열하시오.** 123

  |

  * strip
  * rstrip
  * lstrip



* **대소문자를 바꾸는 메서드를 나열하시오.** 123
  * upper
  * lower
  * capitalize
  * title



* **문자열의 문자(문자열) 개수 및 위치 값을 찾는 메서드를 나열하시오.** 123
  * index
  * find
  * count



* **이터러벌을 '구분자'로 구분하여 '새로운 문자열'로 저장하는 메서드는 무엇인가?** 123
  |
  * join



* **문자열을 바꾸는 메서드를 나열하시오.** 123

  |

  * replace
  * translate



---



* **index는 어떤 메서드인가?** 123
  * 특정 문자나 문자열의 위치를 반환하는 메서드이다.
  * index와 rindex가 있다.



* **find는 어떤 메서드인가?** 123
  * 특정 문자나 문자열의 위치를 반환하는 메서드이다.
  * find와 rfinde가 있다. 



* **index와 find의 차이점은 무엇인가?** 123
  * find : 문자열이 존재하지 않으면 -1을 반환한다.
  * index: 문자열이 존재하지 않으면 '에러'를 발생시킨다.



* **count는 어떤 메서드인가?** 123
  * 특정 문자나 문자열의 개수를 반환하는 메서드이다.



* **strip은 어떤 메서드인가?** 123
  * 문자열 양쪽에 있는 한 칸 이상의 연속된 특정 문자들을 모두 지운다.
  * 기본값 : 공백



* **lstrip과 rstrip은 어떤 메서드인가?** 123
  * lstrip : 문자열 중 가장 왼쪽에 있는 한 칸 이상의 연속된 공백을 모두 지운다. 
  * rstrip : 문자열 중 가장 오른쪽에 있는 한 칸 이상의 연속된 공백을 모두 지운다. 
    * [응용] 특정 문자를 입력할 경우 그 문자들을 삭제한다.



* **strip 메서드 시리즈 사용시 주의사항은?** 123

  * 양끝쪽 부터 확인하기 때문에 제시한 특정 문자가 없을 경우 거기서 종료된다.

  * ```python
    ", python.".strip(',.')
    ```

    ```
    ' python'
    ```

  * ```python
    ", python.  ".strip(',.')
    ```

    ```
    ' python.  '
    ```




* **[보충] 구두점 모두 삭제하기** ㅇㅇㅇ

  * string.punctuation

    * string 모듈의 punctuation에는 모든 구두점이 들어있습니다. 

    * ```python
      string.punctuation
      ```

      ```
      '!"#$%&\'()*+,-./:;<=>?@[\\]^_`{|}~'
      ```

  * ```python
    ', python.'.strip(string.punctuation + ' ')
    ```

    ```
    'python'
    ```



* **upper, lower은 어떤 메서드인가?** 123
  * 문자열을 모두 대문자로 바꾸는 메서드이다.
  * 문자열을 모두 소문자로 바꾸는 메서드이다.



* **capitalize는 어떤 메서드인가?** 123
  * 첫 글자를 대문자로 바꾸는 메서드이다.



* **title은 어떤 메서드인가?** 123
  * 각 단어의 첫 글자를 대문자로 바꾸는 메서드이다.



* **join은 어떤 메서드인가?** 123
  * 구분자 문자열과 이터러블의 요소를 연결하여 새로운 문자열로 만듭니다. 



* **join 사용시 주의 할 사항은 무엇인가?** 1
  * 문자나 문자열만 사용한다. ( 정수 사용시 작동하지 않을 수 있다. )



* **replace는 어떤 메서드인가?** 123
  
  * 문자열 안의 문자열을 다른 문자열로 바꿉니다. ( 전체 )
  
  

* **replace 메서드의 주의 사항은 무엇인가?** 1
  
  * 문자열 자체는 변경하지 않으며 바뀐 결과를 반환합니다. ( 비파괴적 )



* **translate는 어떤 메서드인가?** 123
  * 변환 테이블을 통해 문자를 바꾸는 메서드이다.















* **index는 어떤 메서드인가?**
  * 반환하는 메서드이다.









* **index는 어떤 메서드인가?**
  * 반환하는 메서드이다.









* **index는 어떤 메서드인가?**
  * 반환하는 메서드이다.









* **index는 어떤 메서드인가?**
  * 반환하는 메서드이다.









* **index는 어떤 메서드인가?**
  * 반환하는 메서드이다.









* **index는 어떤 메서드인가?**
  * 반환하는 메서드이다.









* **index는 어떤 메서드인가?**
  * 반환하는 메서드이다.









* **index는 어떤 메서드인가?**
  * 반환하는 메서드이다.









* **index는 어떤 메서드인가?**
  * 반환하는 메서드이다.









* **index는 어떤 메서드인가?**
  * 반환하는 메서드이다.









* **index는 어떤 메서드인가?**
  * 반환하는 메서드이다.









* **index는 어떤 메서드인가?**
  * 반환하는 메서드이다.









* **index는 어떤 메서드인가?**
  * 반환하는 메서드이다.





* 
