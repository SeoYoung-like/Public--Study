# 05 입출력1 ( Character, Number )

※ 문자열 포맷을 제외한 입력과 출력 

---

* 입력
  * 입력 함수 ( 메소드 ) - 활용 
  * 숫자 ( 문자형 => 정수형 변환 )

---

* 출력
  * 출력 함수 ( 메소드 ) - 활용
  * 연산자 활용
  * 큰 따옴표, 작은 따옴표 - 출력
  * 여러 줄 문자열 만들기
    * 줄 바꿈 ( \n )

---

* 문자 ( character )
  * Char, Byte
  * 이스케이프 문자
    * 따옴표 출력
    * 기타
  * 기타

---

* 실습
  *  카지노 ( 랜덤 함수 짧게 설명 기입 )

----











## 4. 예문 - Casino

**최종 복습 예문 - Casino**

```python
from random import randint, randrange

# Welcome to Python Casino
print("Welcome to Python Casino!")
pc_choice = randint(1, 100)

game_set = True

while game_set:
  my_choice = int(input("Choose your number(1-100) : "))
  if my_choice < pc_choice:
    print("▲△▲△ UP △▲△▲")
  elif my_choice > pc_choice:
    print("▼▽▼▽ DOWN ▽▼▽▼")
  elif my_choice < 1 or my_choice > 100:
    print("Choose the number between 1 to 100!")
  else:
    print("★★ You Win!", randrange(999999, 99999999), "get Moneny ★★")
    game_set = False

print("==========================================")
print("▣ randrange type : ", type(randrange(1,10)))
```









