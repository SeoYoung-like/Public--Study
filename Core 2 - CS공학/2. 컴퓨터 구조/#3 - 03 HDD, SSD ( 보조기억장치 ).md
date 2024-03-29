# 10. HDD , SSD

**Secondary storage, Auxiliary Memory, Secondary Memory - 보조기억장치**

**hard disk drive (HDD) / solid-state drive (SSD)**





### 1) 기억장치의 종류와 역할



<img src="./assets/10.%20%EA%B8%B0%EC%96%B5%EC%9E%A5%EC%B9%98%EC%9D%98%20%EC%A2%85%EB%A5%98%EC%99%80%20%EC%97%AD%ED%95%A0%E2%98%85%E2%98%85%E2%98%85.png" alt="10. 기억장치의 종류와 역할★★★" style="zoom: 50%;" />







### 2) 기억 장치 관리 방법

기억 장치마다 정보가 저장되는 위치의 고유번호가 다르고, 관리체계가 다르다. 



#### **[ 고유번호와 관리체계 ]**

* **레지스터** - 고유 이름

* **주기억장치** - 주소값 / 일련번호

* **보조기억장치** - 트랙(Track) 번호와 섹터(Sector) 번호



**[참고] 기억장치의 역사**

천공장치 => 자가테이프 => 플로피디스크 => HDD => SSD

* 전기 신호로 구분









### 3) HDD, SSD

메모리를 보완하기 위해서 큰 데이터를 저장하고 전원을 꺼도 데이터를 계속 보관할 수 있는 보조기억장치를 함께 사용합니다.

우리가 흔히 하드디스크라고 부르는 [HDD](https://en.wikipedia.org/wiki/Hard_disk_drive)가 가장 보편적인 보조기억장치로 사용되고 있고 최근에는 속도가 더 빠른 [SSD](https://en.wikipedia.org/wiki/Solid-state_drive)를 함께 사용하는 경우가 많습니다.

보조기억장치는 운영체제가 관리합니다. 
파일(file)은 보조기억장치에 데이터를 저장하는 기본 단위입니다. 



[참고] 메모리가 데이터를 다루는 속도에 비해서 HDD나 SSD의 속도는 매우 느립니다. 기본 예제정도에서는 차이를 느낄 수 없겠지만 빅데이터를 다루거나 딥러닝을 할 때는 속도 차이가 크게 다가옵니다.






#### (1) HDD

**트렉 / 섹터**
트렉과 섹터 단위로 저장된다.

* 섹터 수와 트랙을 곱하면 하드 디스크 용량을 알 수 있다.

[참고] 배드섹터 : 너무 많은 쓰기(Overwrite) 행위로 손상된 부분이다. 



**FAT - 파일시스템** ???

일의 할당 정보를 표현한 테이블이다.

FileAlocation Table - 파일이름 / 트렉 / 섹터

* **데이터 완전 삭제**
  트랙, 섹터처럼 'del' 필드라는 것이 존재한다. 그 필드가 표기 되어 있다면 시스템은 데이터가 필요 없다고 인지하고 후에 다른 데이터 공간으로 사용하면서 덧씌우게 된다. 그때  비로소 완벽하게 데이터를 삭제하게 되는 것이다. 
* **복구 및 복원** 
  복구 및 복원은 이런 del 필드에 있는 체크를 없애고 다시 데이터를 복구 시키는 것이다. 복구 과정에서 데이터의 일부가 덧씌워 졌다면 손상된 체 일부만 복구하게 되는 것이다.
* **MBR - Master Boot Record**
  0번 트랙, 0번 섹터로 OS의 부트 로드가 들어가 있다.



---



**Format**
원하는 형식으로 트랙과 섹터를 다시 잘라서 추가하는 것이다. ( 초기화 ) 



**디스크조각모음**
띄엄 띄엄 있던 정보를 한 곳에서 모아서 파일을 더 빨리 읽어 들일 수 있게 만드는 것이다.



**탐색기**
하드웨어의 데이터를 접근하게 위해 도와주는 소프트웨어



---







#### (2) SSD

자기디스크가 칩으로 바뀐 것 뿐이다.
똑같이 트랙과 섹터로 관리된다.

* 조각모음 같은 것이 의미 없다.



