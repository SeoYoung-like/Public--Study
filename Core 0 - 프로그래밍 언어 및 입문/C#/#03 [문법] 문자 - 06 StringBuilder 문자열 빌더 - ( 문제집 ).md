# 19 문자열 빌더와 컬렉션



## 1. 문자열과 가비지 수집기

* **문자열 빌더는 무엇인가?**
  * 문자열 처리를 성능상 최적화 시키기 위해 나온 기능이다.



* **문자열 +연산자의 한계는 무엇인가?**
  * 임시로 만들고 버려지는 임시 문자열이 많아진다.



* **String.Join()의 한계는 무엇인가?**
  * `+연산자`와 `for문`을 활용한 방식이기 때문에 임시 문자열이 많아진다.



* **String.Join() 함수를 이용하여 코드를 완성하시오.**

  ```csharp
  string[] value = {"apple", "orange", "grape", "pear"}; 
  string separator = ", ";
  string result = ?
  
  // apple, orange, grape, pear
  Console.WriteLine(result);
  ```

  |

  ```cs
  string[] value = {"apple", "orange", "grape", "pear"}; 
  string separator = ", ";
  string result = String.Join(separator, value); 
  
  // apple, orange, grape, pear
  Console.WriteLine(result);
  ```

  

* **가비지 수집기란 무엇이며, 성능 저하를 줄 수 있는 요인으로 무엇이 있는가?**

  * C#에서 새로 만들어 진 문자열(임시)들은 자동으로 지워주는 기능을 한다.
  * 쓰레기 문자열이 넘쳐나면 GC의 성능 저하가 올 수 있다.

  

* **임시 문자열 사용을 줄이기 위해 할 수 있는 방법이 무엇이 있는가?**
  
  *  StringBuilder를 사용해 주면 된다.



* **StringBuilder와 `+연산자`는 임시문자열을 얼마나 사용하는가?**
  * `+연산자` : N개
  * **StringBuilder** : 1개  ( 일반적 )





## 2. Stringbuiler 클래스

* **StringBuilder는 무엇인가?**
  * 문자열을 효율적으로 만들어 주는 클래스다. 



* **String Builder의 동작 방법은 무엇인가?**
  * 긴 문자열을 담을 수 있는 충분한 공간을 미리 확보한다. 
  
  * 추가 된 문자열들로 그 공간을 차례대로 채워 나간다.
  * 모든 것이 준비되면 최종적으로 문자열을 만들어서 반환한다.



* **StringBuilder 개체를 생성하시오.**

  ```csharp
  // 파일 제일 위에서 라이브러리 추가
  using ?
  
  // 개체 생성
  ? builder = ?
  ```

  |

  ```csharp
  // 파일 제일 위에서 라이브러리 추가
  using System.Text;
  
  // 함수 안에서
  StringBuilder builder = new StringBuilder(4096);
  ```



* **StringBuilder의 개체로 <u>문자열을 추가</u>하시오.**

  ```csharp
  StringBuilder builder = new StringBuilder(4096);
  
  
  
  ?			// Hello Pope!
  ?			// Give me\n
  ```

  |

  ```csharp
  StringBuilder builder = new StringBuilder(4096);
  
  builder.AppendLine("Hello Pope!");
  builder.Append("Give me");
  ```

  

  

* **문자열 Appen와 AppenLine의 어떤 형을 지원하는가?**

  * 숫자, 문자 등 다양한 데이터 형을 지원한다.
    ( 함수 오버로드 )



* **StringBuilder의 개체로 <u>총 용량</u>과 <u>길이</u>을 구하시오.**

  ---

  |

  ```csharp
  builder.Capacity;		// 총용량
  builder.Length;			// 길이
  ```

  

* **총용량과 길이는 무엇인가?**
  
  * 총용량 : 개체를 생성할 때 처음에 미리 할당한 공간이다.
  * 길이 : 내부 배열이 현재 사용 중인 길이 ( 현재 할당 된 문자 양 )



* **StringBuilder의 개체로 <u>추가 공간을 확보</u>하시오.**

  ```csharp
  StringBuilder builder = new StringBuilder(25);
  builder.AppendLine("Hello Pope!");
  builder.Append("Give me");
  
  ?
  ```

  |

  ```csharp
  StringBuilder builder = new StringBuilder(25);
  builder.AppendLine("Hello Pope!");
  builder.Append("Give me");
  
  builder.EnsureCapacity(1024);
  ```

  

* **`EnsureCapacity(int newCapacity)`에 입력한 값보다 총용량이 많다면 무슨 일이 발생하는가?**
  
  * 아무런 일도 발생하지 않는다.
  * 입력한 값 > 총용량 : 입력한 인자 값보다 현재 총용량보다 크면 <u>용량을 늘려준다.</u>
  * 입력한 값 < 총용량 : 인자 값이 현재 총용량보다 작은 값이 입력되면 <u>아무런 변화가 없다.</u> 



* **StringBuilder의 개체에서 완성된 문자열을 반환 하시오.**

  ```csharp
  StringBuilder builder = new StringBuilder(4096);
  // 문자열 추가하는 코드 생략
  
  string greetings = ?
  ```

  |

  ```csharp
  StringBuilder builder = new StringBuilder(4096);
  // 문자열 추가하는 코드 생략
  
  string greetings = builder.ToString();
  ```

  * 현재 내부 배열이 사용 중인 길이 만큼만 반환

  

  

## 3. StringBuilder 기타 함수



* **StringBuilder의 개체 중간에 새로운 문자열을 삽입하시오.**

  ```csharp
  StringBuilder builder = new StringBuilder(4096);
  builder.AppendLine("Hello Pope!");
  
  // "Hello and bye Pope!\n"
  ?
  ```

  |

  ```csharp
  StringBuilder builder = new StringBuilder(4096);
  builder.AppendLine("Hello Pope!");
  
  // "Hello and bye Pope!\n"
  builder.Insert(6, "and bye ");
  ```

  

* **StringBuilder의 개체 특정 문자를 바꾸시오.**

  ```cs
  StringBuilder builder = new StringBuilder(4096);
  builder.AppendLine("Hello Pope!");
  
  // "Hello Pobe!\n"
  ?
  ```

  |

  ```cs
  StringBuilder builder = new StringBuilder(4096);
  builder.AppendLine("Hello Pope!");
  
  // "Hello Pobe!\n"
  builder.Replace('p', 'b');
  ```

  


* **다음 코드에서 `builder.Replace` 작동하지 않는다.** 
  **코드를 올바르게 고치고, 그 이유가 무엇인지 서술하시오.**

  ```cs
  StringBuilder builder = new StringBuilder(4096);
  builder.AppendLine("Hello Pope!");
  
  // "Hello Pope!\n"
  builder.Replace('P', 'B', 3, 3);
  ```

  |

  ```cs
  StringBuilder builder = new StringBuilder(4096);
  builder.AppendLine("Hello Pope!");
  
  // "Hello Bope!\n"
  builder.Replace('P', 'B', 3, 4);
  ```

  * **`Replace(char old, char new, int start, int count)`** 
  * start 번째부터 **start + count** 번째 사이 ( 포함 ) 에 있는 모든 old를 new로 바꾼다.

  

* **StringBuilder의 개체 특정 문자를 제거하시오.**

  ```cs
  StringBuilder builder = new StringBuilder(4096);
  builder.AppendLine("Hello Pope!");
  
  // "Hello Po!\n"
  ?
  ```

  |

  ```cs
  StringBuilder builder = new StringBuilder(4096);
  builder.AppendLine("Hello Pope!");
  builder.Remove(8, 2);
  ```

  * **`Remove(int start, int length)`**  : start번 째부터 length개 만큼의 문자를 지운다.





* **StringBuilder의 개체 모든 문자를 제거하시오.**

  ```csharp
  ?
  ```

  |

  ```csharp
  builder.Clear();
  ```

  * 이 함수를 호출 후, 길이를 확인하면 0이 나온다.



* **Clear()은 언제 사용하나?**
  * StringBuilder 개체를 재활용하기 위해 사용한다





## 4. StringBuilder vs 문자열 합치기

* **StringBuilder 개채 생성시 사용 TIP은 무엇인가?**
  * 용량 크게 잡기
    * 자잘한 것 여러 개 가져오는 것 보다 한 번에 크게 ( 임시 문자열 총용량 : 4096 )을 잡아오는 것이 좋다.
    * 문자열 복사를 안 할 수록 좋으므로 처음부터 충분한 공간을 확보하는 것이 좋다.
      * 보통 2의 승수로 잡아 쓴다. ( 256 -> 512 -> 1024 -> 2048 -> 4096 )
    * 대부분 일반적인 경우에 그렇다. 
      ( 메모리 부족한 하드웨어 제외 )



* **StringBuilder 사용 시 총용량 ( 임시 문자열 공간 )을 다 사용하면 어떻게 되는가?**
  * StringBuilder가 자동적으로 내부 공간을 늘린 뒤 모든 데이터를 복사한다.
  * 즉, 아무런 문제 없다.



* **StringBuilder 총용량이 늘어나는 세부 동작에 대해 나열하시오.**
  * 내부 공간 길이가 부족하다고 판단 될 때, 클래스 자체적으로 기존 배열 길이의 두 배 크기로 배열을 생성한다.
  * 이후 기존 배열에 있던 string을 새로운 배열에 복사 붙여넣기 한 후 다음 작업을 진행한다.
  * 복사 이후 기존에 넣으려고 한 문자열을 추가한다.
  * builder는 새로운 배열로 넘어온다.



* **StringBuilder은 언제 쓰는 게 좋은가?**
  * 다수(수 십개 이상)의 문자열을 합치면 그때부터 StringBuilder를 고려한다. 



