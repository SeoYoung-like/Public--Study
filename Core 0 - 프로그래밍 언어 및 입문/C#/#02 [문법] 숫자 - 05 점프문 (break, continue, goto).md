# 점프문

Jump statements 

흐름을 끊고 프로그램의 실행 위치를 원하는 곳으로 단숨에 도약 시킬 수 있습니다.

* break, continue : 루프문을 끝내거나 건너 뛸 때 사용된다.
* return : 함수의 실행을 종료하고 컨트롤과 함수의 결과(있는 경우)를 호출자에게 반환합니다.
* throw : 예외에서 볼 예정
* goto





## 1. goto문

### 1.1. goto 문

특정 레이블로 이동하는 기능을 합니다. C#에서 레이블은 콜론(`:`) 기호를 레이블 이름 뒤에 붙여 만듭니다. 이렇게 만든 레이블 코드는 평상시에는 주석처럼 아무 의미 없는 코드로 사용하지만, goto 구문 뒤에 레이블을 지정하면 해당 레이블로 이동하는 기능을 합니다.

* 레이블 문은 관례상 대문자로만 쓰는 것이 일반적이다.

```csharp
레이블:
goto 레이블;
```

---

```csharp
static void Main(string[] args)
{
    for (int i = 0; i < 5; i++)
    {
        Console.WriteLine("Outer loop: " + i);
        for (int j = 0; j < 3; j++)
        {
            Console.WriteLine("Inner loop: " + j);
            if (j == 1)
            {
                goto LOOPEXIT; // 내부 루프에서 j가 1이면 외부 루프로 이동
            }
        }
    }

    LOOPEXIT:
	    Console.WriteLine("Break from outer loop");
}
```

[참고] 최근에는 거의 사용하지 않는 구문 입니다. 

* 스파게티 코드를 유발 할 수 있기 때문에 지양해야 하는 코드 이기도 하다.





### 1.2. goto문이 유용한 경우

* 중첩 루프에서 탈출

유일하게 유용하게 사용할 수 있는 경우가 있는데, 중첩된 반복문을 한 번에 뚫고 나올 때 유용하다.

```csharp
for (int i = 0; i < 100; i++)
{
    for (int j = 0; j < 200; j++)
	{
        for (int k = 0; k < 50; k++)
        {
            if ( x == 0 && y == 0)
        		goto EXIT_FOR;
    	}
	}
}

EXIT_FOR:
	Console.WriteLine("Exit");
```











## 2. break, continue

break와 continue는 가독성을 높이기 위해 들여씌 블록을 줄이는 역할도 한다.

continue 문을 적절히 사용하면 눈으로 따라가서 추적해야 하는 "들여쓰기"나 "블록"의 수를 줄일 수 있으므로 코드를 읽고, 이해하기 더 쉬워진다.

```csharp
/* 일반 조건문과 반복문 */

int sum = 0;
int n = 1;
while (n++ < = 1000)
{
	if ((n % 2) == 0)
	{
		if ((n % 3) == 0)
		{
			if ((n % 5) == 0)
			{
				sum += n;
			}
		}
	}
}
```

```csharp
/* break, continue 사용 */

int sum = 0;
int n = 1;
while (n++ < = 1000)
{
	if ((n % 2) != 0) continue;
	if ((n % 3) != 0) continue;
	if ((n % 5) != 0) continue;
}
```

