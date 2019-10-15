**[E-DRIVE](/documents/kr/products/e_drive/) update log**

Modified : 2019.10.15

---

* Kramdown table of contents
{:toc .toc}


<br>


# 2019.10.15

- E-Drive: 19.10.3
- E-Drive BleServer: 19.10.14
- E-Drive Tester: 19.9.1

> - 카드 배치 순서 변경


[Download](https://drive.google.com/open?id=1L8Swy8QvJfmzowGek9T79n6KOj4pkXEH)


<br>

---


# 2019.10.11

- E-Drive: 19.10.2
- E-Drive BleServer: 19.10.14
- E-Drive Tester: 19.9.1

> - E-Drive의 BLE 통신 보드 펌웨어 업데이트 기능 추가
> - Drone7Card.exe의 UI 개선


[Download](https://drive.google.com/open?id=1L8Swy8QvJfmzowGek9T79n6KOj4pkXEH)


<br>

---


# 2019.8.28

- E-Drive: 19.8.3

> - 카드 코딩과 관련된 DataType의 위치 조정, 관련 송수신 클래스 조정


[Download](https://drive.google.com/open?id=1L8Swy8QvJfmzowGek9T79n6KOj4pkXEH)


<br>

---


# 2019.8.23

- E-Drive: 19.8.2

> - ColorClassify 정의 추가 및 Drone7Card 프로그램에서 카드 분류 기준 값 변경가능하도록 수정함
> - 라인 코딩시에도 CARDREADER에서 분류한 카드 값을 그대로 사용


[Download](https://drive.google.com/open?id=19L5twy8qqK4s5LVczYZ-VNIpEEqpsQBq)


<br>

---


# 2019.8.8

- E-Drive: 19.8.1

> - 배터리 알람 기준을 30%로 변경
> - RawLineTracer에서 라인트레이서가 인식한 바닥 색상 값이 업데이트 안되는 문제 수정


[Download](https://drive.google.com/open?id=15k5s_RM6OjIFSWm5wxgxmB8nyZnjwhQx)


<br>

---


# 2019.7.26

- E-Drive: 19.7.18

> - State에서 modeSystem을 modeDrone으로 변경
> - 제어기 수정 사항 반영
> - RawLineTracer에서 바닥 좌우측 IR 데이터 변수 삭제


[Download](https://drive.google.com/open?id=17YawG7WzvIwktDAbe4zfEGrCq0BpCJ2S)


<br>

---


# 2019.7.25 - 2

- E-Drive: 19.7.17

> - Instant run에서 비상등을 브레이크 등에서 좌우 깜빡이를 동시에 작동시키는 것으로 변경(깜빡임 계속 유지)
> - Instant run에서 TailLight를 끌 때 좌우 깜빡이(비상등)도 끄게 함
> - State 클래스 수정(15 -> 11 byte)


[Download](https://drive.google.com/open?id=11A2eWzCWfYtI2IzzSCF8gMwI9xyskUe7)


<br>

---


# 2019.7.25

- E-Drive: 19.7.16

> - Low Battery 알림 추가
> - 카드 코딩에서 TailLight를 끌 때 좌우 깜빡이(비상등)도 끄게 함
> - 버저 버퍼를 64에서 128로 변경
> - '조건이 맞지 않으면' 카드 사용 시 조건 루프를 빠져나가는 버그 수정


[Download](https://drive.google.com/open?id=1QCVqnPEv3GDhrz_sORRgYFB5lJ2tADnG)


<br>

---


# 2019.7.24

- E-Drive: 19.7.15

> - 무한루프에서 버저 사용 시 1회 재생 후 버저가 완전 중단되는 문제 수정
> - 버튼을 길게 눌러 카드 코딩 실행을 할 때 실행 준비가 되면 Buzzer에서 소리가 나게 함
> - 카드 코딩에서 비상등을 브레이크 등에서 좌우 깜빡이를 동시에 작동시키는 것으로 변경(깜빡임 계속 유지)
> - 버저에 멜로디 예약 시 멜로디 전체가 들어갈 공간이 충분한 경우에만 예약하게 함


[Download](https://drive.google.com/open?id=1t7tcTjQexSAdlIIJr4DMqA9H2muomQ5M)


<br>

---


# 2019.7.23

- E-Drive: 19.7.14

> - 버전 구성을 (Major, Minor, Build)에서 (Year, Month, Build)로 변경함. 제품 출시 전까지 적용해보고 문제가 없을 경우 이후 출시하는 다른 제품에도 적용할 예정. 문제가 있으면 이전 구성으로 복원할 계획임

<br>
