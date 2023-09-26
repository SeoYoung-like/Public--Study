# 22 개체 지향 프로그래밍 기초2

## 1. Partial 클래스

* 분할 클래스 / 부분 클래스 / 일부분 클래스
* 파샬클래스



> ---
>
> [ 참고 ]
>
> 클래스도 함수처럼 재활용성을 고려해서 만들어야 한다.
>
> 1번 사용할 것이라면 클래스를 만들 필요가 없다.
>
> ---



### 1.1. 문제 발생 : 거대한 클래스

* Human 클래스 작성한다고 가정
  * 무지막지하게 크다.
  * 너무너무 자세한 Human 클래스
  * 머리, 팔, 다리 등 섬세하게 움직이는 코드를 작성해야 한다.

* **C#에서는 조금 더 예쁘게 관리 할 수 있다.**

![image-20230716105234879](./assets/image-20230716105234879.png)

![image-20230716105123256](./assets/image-20230716105123256.png)







### 1.2. 방법1 : 작은 클래스로 쪼개서 만들기

* **다른 언어에서 해결한 일반적인 방법이다.**
* 클래스를 쪼개서 포함 시킨다.
  1. Human 클래스 쪼개기 
     * Head 클래스
     * Body 클래스 
     * ...
  2. Human 클래스가 작은 클래스들을 포함한다.

![image-20230806130919734](./assets/image-20230806130919734.png)



**[ 장단점 ]**

* **장점**
  * 작게 쪼갠 클래스를 다른 클래스에서 개체로 쓸 수 있다.
  * (ex) Head 클래스를 Human이 아닌 Cat 클래스에서도 쓸 수 있다.
* **단점**
  * 단순 클래스가 너무 작게 쪼개면 문제가 발생할 수 있다.
  * 재활용성이 없다.
  * OOP를 잘 못 이용하고 있는 것이다.
  * 유지보수에 문제가 될 수 있다.













### 1.3. 방법 2 : Partial 클래스

* C#에서만 사용할 수 있는 방법이다.

* 1개의 클래스를 여러 파일에 걸쳐 정의 할 수 있다. 
* 클래스를 물리적으로만 분리 ( 여러 파일로 쪼개기 )
  * partial 키워드를 사용하면 중복되는 클래스 이름이 여러 파일에 걸쳐 존재할 수 있다.
  * 큰 클래스를 여러 파일에 나눠 저장하고 싶을 때 사용할 수 있다.

![image-20230806131223955](./assets/image-20230806131223955.png)

![image-20230806131242475](./assets/image-20230806131242475.png)









### 1.4. 코딩 표준 : partial 클래스의 파일명

네이밍 규칙

* <클래스 명>.<설명>.cs

* 각 단어의 첫 글자는 대문자로

  Human.Head.cs

  Human.Body.cs

  Human.Hand.cs

  Human.Leg.cs

> ---
>
> [질문]
>
> Partial 클래스들이 컴파일될 때는, 각각의 파일 이름 기준으로 ABC 순서로 합쳐지나요?
>
> [답변]
>
> 언어 표준에서 특별한 순서를 정해놓진 않았습니다. 
> https://stackoverflow.com/questions/7965830/is-the-textual-order-across-partial-classes-formally-defined
>
> ---







### 1.5. 실습

* 같은 클래스명 사용 가능
  * [주의!] class 생성시 partial class 키워드 입력

* 생성자와 같은 메서드가 이미 만들어 졌다면 다시 만들 필요 없다.
  * 중복으로 코드를 기입하면 컴파일 error가 발생한다.

```csharp
/* Robot.LeftArm.cs */

using System;

namespace PartialClass
{
    public partial class Robot
    {
        public Robot(string name)
        {
            Name = name;
        }

        public string Name { get; private set; }

        public void ShootLaserBeam()
        {
            Console.WriteLine($"{Name} shooting laser beam!");
        }

        public void ShootMissiles()
        {
            Console.WriteLine($"{Name} shooting missiles!");
        }
    }
}
```

```csharp
/* Robot.RightArm.cs */

using System;

namespace PartialClass
{
    public partial class Robot		
    {
        //public Robot(string name)
        //{
        //    Name = name;
        //}

        //public void ShootLaserBeam()
        //{
        //    Console.WriteLine($"{Name} Shooting laser beam!");
        //}

        public void Nuke()
        {
            Console.WriteLine($"{Name}: Nuclear launch detected!");
        }
    }
}
```

```csharp
/* Program.cs */

using System;

namespace PartialClass
{
    class Program
    {
        static void Main(string[] args)
        {
            Robot robot = new Robot("Taekwon V");

            Console.WriteLine(robot.Name);

            robot.ShootLaserBeam();
            robot.ShootMissiles();
            robot.Nuke();
        }
    }
}
```









## 2. 정적 클래스 ( Static Class )

* 다른 언어에서도 있는 개념이다.



### 2.1. static

* 사전적 의미 : 고정된
* 변하지 않는다 정적으로 있겠다는 의미이다.
* 클래스 자체에 소속 되도록 지정하는 한정자이다.

---

* 클래스, 멤버 변수, 멤버 함수에 사용 가능
  * 단, const 상수는 묵시적 static 이다.
  * 묵시적으로 사용하는 것이기 때문에 한 번 더 키워드를 기입하면 컴파일 오류가 발생한다.

```cs
public static class Math			// OK
public static int Count = 0;		// OK
static void Main(string[] args)		// OK
public static const int MAX = 100	// 컴파일 오류 - 묵시적이라 이미 들어가 있음
public const in MAX = 100;			// OK
```







### 2.2. 정적 변수

* 객체에 소속되어 있지 않기 때문에 '정적 멤버 변수'라고 말하기도 애매하다. 

  * 객체가 아닌 상위 개념인 클래스에 소유되어 있다.
  * 몇 몇 부분은 '정적 멤버 변수'으로 약간 잘못 표기하고 있다. ( 이해나 분류를 위해 사용할 뿐이다. )
  * '정적 변수'라고 표기 하는게 적절할 수 있다. ( 개체에 소속이 아니기 때문이다. )

  ---

* 개체에 속하지 않고 클래스형에 속한다.

  * 따라서 **모든 개체**가 하나의 정적 변수를 공유한다.
  * public 이면 개체가 없어도 **외부에서 접근 가능**하다.
  * **멤버 함수에서 접근 가능**하다.


![image-20230806133857066](./assets/image-20230806133857066.png)

![image-20230806133908276](./assets/image-20230806133908276.png)

![image-20230806134108044](./assets/image-20230806134108044.png)







**[ 정적 변수 ( 예시 ) ]**

static이 있는 순간 객체에 소속되지 않게 된다.
객체보다 상위에 있는 클래스에 소속되어 있다. 

클래스에 하나만 있다.

( 만약, static이 없이 Count를 사용하게 된다면 객체에 소속되어 myCat1, myCat2, myCat3 모두 Count가 1이 된다. )

![image-20230716110955248](./assets/image-20230716110955248.png)







### 2.3. 정적 함수

* 개체에 속하지 않고 클래스에 속한다.
* <u>정적 멤버 함수는 비정적 멤버 변수, 함수에 접근하지 못한다.</u>
  * 비정적 멤버 변수, 함수는 개체가 되는 순간 그 수가 많아질 수 밖에 없기 때문에 접근 자체가 불가능하다.


![image-20230806134421022](./assets/image-20230806134421022.png)

![image-20230806134427218](./assets/image-20230806134427218.png)





**[ 정적 함수 ( 예시 ) ]**

![image-20230716111809806](./assets/image-20230716111809806.png)









### 2.4. 정적 클래스

* C#의 고유한 기능이다.

* 객체를 만들어 줄 필요 없이 사용하면 되는 것들은 static 클래스를 만들어 사용하면 된다.

  * 개체를 생성하지 않고 정적 클래스 내의 함수를 사용 가능하다.

  * OOP로 개채 지향으로 완벽하게 만들 수 없는 것들은 이런 식으로 사용한다.

  * 주로 유틸리티 클래스를 만들 때 사용한다.

    (ex) 사칙연산, Math 클래스, Math.PI, Math.Round(10.12487, 3)  등

---

* 정적 멤버만 가질 수 있다.

  * 정적 멤버 변수

  * 정적 멤버 함수 : 멤버 함수에 반드시 static을 붙여야 한다.

    * 안 붙이면 컴파일 오류 발생 => **실수 방지를 위해서 이다.**

      ```csharp
       public int Max(int val1, int val2)
      {
      	return (val1 < val2) ? val2: val1;
      }
      ```

      ![image-20230806134837724](./assets/image-20230806134837724.png)

  

* **new로 개체를 생성할 수 없다. ( 할 필요도 없다. )**

  * new 개체를 생성할 수 없는 것도 이런 태생적인 이유(정적 멤버 사용) 때문이다. 
  * 간편하게 사용하기 위한 이유라고 볼 수 있다. 
  * 어디서든 마음대로 호출 할 수 있다.

  ```
  SimpleMath sm = new SimpleMath();		// 컴파일 오류
  ```

  ![image-20230806134717983](./assets/image-20230806134717983.png)







**[ 정적 클래스 ( 예시 ) ]**

![image-20230716112052447](./assets/image-20230716112052447.png)









### 2.5. 정적 변수와 함수를 사용 이유

---

<img src="./assets/image-20230806135501533.png" alt="image-20230806135501533" style="zoom: 80%;" />

---

> ---
>
> [질문]
>
> 상수는 묵시적으로 static 이라고 하셨는데, 이미 고정되어 수정할 수 없으므로 상수라는 개념 자체가 static 개념을 이미 내포하기 때문에 묵시적으로 static인 것이라고 이해했습니다. 
>
> 그렇다면 클래스 멤버변수로 const int COUNT 을 만들어줬을 때와 static int Count로 만들어줬을 때, 상수의 경우는 수정이 불가하다 뿐 내부적으로 둘 모두 동일하게 static 특성을 가지게 되는 걸까요?  즉, 상수로 멤버변수를 선언했을 때도 static 처럼 그 상수는 개체의 수에 관계없이 클래스에 한 개만 존재하게 되는 건지 궁금합니다.
>
> [답변]
>
> 네 올바르게 이해하셨습니다. 
>
> (그리고 const int COUNT라고 선언해줬을 때... 그걸 멤버 변수라고 부를 수 있는지도 약간 애매하긴 합니다. 그냥 상수라고 부를 것 같네요. 그러나 확실히 이렇다 저렇다 구분하는 사람들을 못봐서 저도 확실히 말씀드리긴 어렵습니다)
>
> ---











## 3. 확장 메서드 ( Extension Method )

* 확장 메서드
* Extension Method

---

개체 지향 프로그램을 할 때 매우 편해진다. 

언어에서 지원하는 기능으로 코드가 깔끔해진다.

※ C# 언어 자체에서 지원해 주는 기능으로 김포프가 개인적으로 객체 지향에서 편하게 사용하고 있는 감탄한 기능이다. ( 이걸 지원해줘? 땡큐! )

> ---
>
> [ 코드 들여다보기 ]
>
> 드래그 해서 'F12' 버튼을 누르면 내부코드를 확인할 수 있다.
>
> <img src="./assets/image-20230723105734886.png" alt="image-20230723105734886" style="zoom:80%;" />
>
> ---





### 3.1. 탄생 계기

#### **1) 클래스 의문**

MyCoolClass에 GetCount 메서드를 정의하는 것 보다 String 클래스에 추가로 정의해서 사용하는 것이 더 깔끔해 보이는데 방법이 없을까? 

* 해결 시도 : 라이브러리 바꾸기를 시도, 하지만 .NET에서 지원하는 라이브러리이기 때문에 추후에 문제가 발생할 수 있다.
* 해결법 : 확장 메서드 사용

![image-20230806140305156](./assets/image-20230806140305156.png)





#### 2) 확장 메서스 - 예시

![image-20230723105935744](./assets/image-20230723105935744.png)





### 3.2. 확장 메서드

#### 1) 확장 메서드 만드는 순서

1. 정적 클래스를 만든다. 

   * static function
   * 클래스 명 : 코딩 표준 상 대상이 되는 '객체 이름'과 'Extension'을 붙여 준다.

2. 확장 메서드를 작성한다. 

   * static method - 반드시 정적 함수여야 한다.
   * 확장 메서드의 첫 번째 인자는 함수에 넣고자 했던 클래스 명을 적는다.
     ( string이라면 string을 사용한다. )
   * 첫 번째 인자 앞에 반드시 **this**를 붙여준다. ( 컴파일러가 간편하게 호출할 수 있게 만든다. )
     * `StringExtension.GetCount(...);`  로만 호출할 수 있던 것을 this를 붙여 줌으로 해서 `input.GetCount(...);` 처럼 호출 할 수 있게 되었다.

```csharp
public static class StringExtension
{
	public static int GetCount(this string message, char[] separators)
	{
	}
}
```

![image-20230723110518557](./assets/image-20230723110518557.png)





#### 2) 확장(extension) 메서드

내부적으로는 정적 함수를 이용하는 것이지만 호출하는 입장에서는 `object.함수`로 호출하는 것이기 때문에 보는 입장에서는 그 기능인 것처럼 동작한다.

마치 그 클래스의 기본 동작인 것 마냥 추가하여 사용하는 것이다.

* 사용 시기 : 클래스에 함수를 추가하지 못할 때 사용한다.
  * 해당 클래스의 소스 코드가 없을 때 ( 다른 사람의 라이브러리 사용할 때 )
  * 추가하려는 함수가 클래스에 필수적이지 않을 때
    * 클래스에서 필수적이지 않기 때문에 상황에 맞게 확장 메서드로 추가해서 유동적으로 사용할 수 있다.
    * 앞서 예제에 나온 문자열의 단어 수 함수 같을 때
    * 뒤에서 곧 다룰 Linq 라이브러리의 ToArray() 같은 함수들

---

* 보통 다른 프로그래밍 언어에서는 정적 메서드를 이용해서 해결한다.
* C#에서는 확장 메서드를 사용하면 된다.

---





#### 3) 확장 메서드 vs 단순 정적 메서드 - 비교

* 정적 메서드는 호출할 경우 클래스명 까지 전부 기입해야 하고 번거롭다.
* 반면, 확장 메서드는 this 사용을 하면 input.GetCount(delims);를 통해 this에 input이 바로 들어와 사용하기 편하다. ( 깔끔하다. )
  * 결과적으로 둘 다 정적함수고 내부적으로 돌아가는 것은 같지만 컴파일러가 가독성 좋게 예쁘게 해준다.

![image-20230723111228482](./assets/image-20230723111228482.png)

* `단순 정적 메서드` 쓰는 대신에 `확장 메서드`를 쓸 수 있는 상황이 된다면 `확장 메서드`를 쓰는 것이 좋다.





### 3.3. 코딩 표준과 베스트 프렉티스

#### 1) 코딩 표준 : 확장 메서드 강조 

* 확장 메서드를 담는 클래스 이름에 Extension을 접미사로 붙인다.

  ```csharp
  public static class <확장을 원하는 클래스>Extension
  ```

  * StringExtension, CatExtension, MathExtension
  * 보통은 Enstenions로 복수형을 붙이는게 일반적이다. 
    ( 확장 메서드가 여러 개인 경우가 많다. )

* 확장 메서드는 다른 파일에 넣는다.

  * 커스텀 데이터형 ( or 클래스 )마다 파일 하나를 만든다.
  * StringExtension 1개, CatExtension 1개 등






#### 2) 베스트 프렉티스 : 확장 메서드

* 기본형의 확장 메서드를 만들 땐 조심한다.

  * 특히 비즈니스 로직을 넣어야 한다면 No No~

    ```csharp
    CourseCode courseCode = something.ToCourseCode();
    ```

  * 차라리 정적 메서드를 만들 것

    ```
    CourseCode courseCode = CourseCode.Parse(something);
    ```

    * string에 너무 일반적인 기본적인 데이터이기 때문에 string 쓸 때마다 확장 메서드 쓸 수 있다고 뜰 수 있기 때문에 헷갈릴 수 있다. 그렇기 때문에 정적 메서드를 만들어 쓰는 것이 맞다.

* 이 외의 클래스 형의 확장 메서드는 괜찮다.

  * 클래스 자체가 이미 비즈니스 로직을 대표한다.

> ---
>
> [ 질의응답 ]
>
> 질문 : List나 Dictionary같이 접근 불가능한 클래스형에 확장 메서드를 쓸 수 있는 건 알겠는데 자신이 만든 클래스도 확장 메서드가 쓰이는 경우가 있나요?
>
> 답변 : 네 있습니다. 라이브러리를 여러개 나눌 때 라이브러리 A에는 필요한 기능만 두고, B라이브러리에서 A 라이브러리를 사용할때 B 라이브러리 안에 A 라이브러리 안에 있는 클래스들의 확장 메서드를 쓰는 경우가 있습니다. 사실 매우 많습니다 ^^
>
> ----











