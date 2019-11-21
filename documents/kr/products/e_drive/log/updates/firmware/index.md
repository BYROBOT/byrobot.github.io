**[E-DRIVE](/documents/kr/products/e_drive/) update log**

Modified : 2019.11.21

---

* Kramdown table of contents
{:toc .toc}


<br>


# 2019.11.21

- **E-Drive: 19.11.38**
- E-Drive BleServer: 19.10.16
- E-Drive Tester: 19.9.1

> - ***이전 버젼과 호환이 안됨***
> - ***이전 버전을 사용하던 자동차는 현 버전으로 변경하려면 부트로더를 변경해야 함***
> - 사용자 데이터 저장 단위를 512byte에서 **1Kbyte**로 변경
> - 카드, 동작 등을 더 이상 입력할 수 없는 경우 경고음으로 알림



[Download](https://drive.google.com/open?id=1Dd96z9nYzwmJaoaHoJKZQfsw4dD0KoXT)


<br>

---


# 2019.11.19

- **E-Drive: 19.11.33**
- E-Drive BleServer: 19.10.16
- E-Drive Tester: 19.9.1

> - 색상 구분 경계 값 기준을 Front, Rear, Line 세 가지로 구분해서 사용하게 함
> - 위의 변경으로 Drone7Card 프로그램이 이전 버전의 펌웨어와 호환되지 않음
> - 색상 구분 경계 값 측정 실행 중 자동차를 45도 이상 기울이면 동작이 중단됨
> - 색상 구분 경계 값 측정 실행 중 지정한 색상 범위를 크게 벗어나는 경우 Error로 처리하게 함
> - 색상 구분 경계 값 측정 실행 완료 시 Front와 Line은 같은 값으로 설정됨



[Download](https://drive.google.com/open?id=1NRZiF2qcRCESBjZgiRyL69bK0CwmGTun)


<br>

---


# 2019.11.18

- **E-Drive: 19.11.29**
- E-Drive BleServer: 19.10.16
- E-Drive Tester: 19.9.1

> - 버튼을 7회 연속으로 누르면 색상 구분 경계값을 측정하는 모드로 동작함
>   - 버튼을 7회 연속으로 누르면 흰색 깜빡이는 상태가 됨
>   - 위의 상태에서 자동차를 들면 빨간색이 깜빡이는 상태가 됨
>   - 이 때 상하가 모두 빨간색인 카드 위에 자동차를 올려두면 빨간색의 최대-최소 값을 측정
>   - 측정하는 동안 버저가 0.5초 간격으로 울리고 측정이 끝나면 '띠딕'하는 소리가 남
>   - 이 때 자동차를 들어올리면 다음 측정할 색상을 표시
>   - 위의 색상 측정 과정을 6회 반복하면 마지막에 색상 경계값을 계산하여 저장하고 LED가 흰색으로 계속 켜진 상태 유지



[Download](https://drive.google.com/open?id=1xsLlMUNzzB40erjz5GXowvOFTMgQVNqq)


<br>

---


# 2019.11.13

- **E-Drive: 19.11.23**
- E-Drive BleServer: 19.10.16
- E-Drive Tester: 19.9.1

> - 색 분류 기준을 카드 코딩과 라인 코딩에 다르게 적용되도록 분리함



[Download](https://drive.google.com/open?id=1fi1nMVQRBYUPs7IUX5c0W4l8ukZe-BWR)


<br>

---


# 2019.11.8

- **E-Drive: 19.11.21**
- E-Drive BleServer: 19.10.16
- E-Drive Tester: 19.9.1

> - 핸드팔로잉 제어 수정
> - 버튼을 3초 이상 눌러 동작 실행 기능 제거(버튼 두 번 연속 누르기만 사용함, 피아노 모드에서는 멜로디 실행 카드 사용)
> - 버튼을 10초 이상 눌러 센서 리셋 기능 제거(버튼 다섯 번 연속 누르기만 사용함)
> - 카드 코딩 중 코딩 완료 또는 대기 상태일 때에만 실행이 가능하도록 수정
> - 모션 모딩 중 코딩 완료 또는 대기 상태일 때에만 실행이 가능하도록 수정
> - 사용자 멜로디 저장 완료 후에만 멜로디 재생이 동작하도록 수정



[Download](https://drive.google.com/open?id=1LRgtF2L9rU9JUHZRxaVP9vobhtPbUibC)


<br>

---


# 2019.11.7

- **E-Drive: 19.11.19**
- E-Drive BleServer: 19.10.16
- E-Drive Tester: 19.9.1

> - 10초 이상 버튼을 눌러서 센서를 초기화 할 때의 LED 이벤트 수정



[Download](https://drive.google.com/open?id=1W24I85kIh-wlCbyGgQei7dc5edpgv99w)


<br>

---


# 2019.11.6

- **E-Drive: 19.11.17**
- E-Drive BleServer: 19.10.16
- E-Drive Tester: 19.9.1

> - 모션 코딩, 라인 코딩 시작이 안되는 문제 수정
> - 블루투스 연결 이벤트를 받으면 드라이브 모드로 전환



[Download](https://drive.google.com/open?id=14F86mkJE4WppJg6UGgEv0uGnNssZB3g2)


<br>

---


# 2019.11.5

- **E-Drive: 19.11.15**
- E-Drive BleServer: 19.10.16
- E-Drive Tester: 19.9.1

> - ***이전 버젼과 호환이 안됨***
> - ***이전 버전을 사용하던 자동차는 현 버전으로 변경하려면 부트로더를 변경해야 함***
> - 사용자 정의 멜로디 기능 추가
>   - 피아노 모드에서 저장한 멜로디를 카드 코딩에서 멜로디 호출 카드를 사용하여 재생할 수 있는 기능
> - 사용자 정의 멜로디 변경 방법
>   - 피아노 모드 전환
>   - 멜로디 입력 시작 카드 읽기
>   - 멜로디 입력
>   - 멜로디 입력 끝 카드 읽기
> - 피아노 모드에서 사용자 정의 멜로디 실행 방법
>   - 멜로디 실행 카드 읽기
>   - 3초 이상 눌렀다 떼기
> - 현재 미묘하게 수정이 필요할 것으로 보이는 사항
>   - 저장한 멜로디가 이어서 연주됨
>   - 같은 음을 두 번 연주할 경우 하나의 음을 길게 연주한 것처럼 들림
> - 카드 코딩, 함수, 멜로디 카드 최대 120장까지 입력할 수 있도록 수정(코딩 시작, 코딩 끝 카드를 제외하면 118장)
> - 버튼을 5회 연속으로 누르거나 10초 이상 누르면 '도레미파솔라시도' 연주와 함께 센서 리셋
> - 사용자 정의 멜로디를 저장하려고 데이터 저장 단위를 변경함. 부트로더 또한 수정되었기 때문에 이전 버젼과 호환이 안됨.



[Download](https://drive.google.com/open?id=1vLFJRM5Y_luuOv7mYYZ7mWleZsLl8Rvv)


<br>

---


# 2019.10.23

- **E-Drive: 19.10.13**
- E-Drive BleServer: 19.10.16
- E-Drive Tester: 19.9.1

> - 카드 코딩에서 Tail LED(브레이크 등) 제어 기능을 제거
> - 브레이크 등은 모터 동작 여부에 따라 제어하도록 변경
> - LED Manual 제어에서도 Tail LED는 조작하지 못하도록 차단
> - 전조등 밝기 조절
> - 브레이크등 밝기 조절
> - E-Drone과 DataType의 Motion, Range 번호 순서를 맞추기 위헤 Altitude를 앞에 추가함
> - 앞으로 PC 프로그램의 중복 개발을 줄이려고 함. 그에 따라 대상 장치에 상관없이 Protocol을 최대한 일치하게 만들 예정

[Download](https://drive.google.com/open?id=1_hwX8KkXVlJ6yJm48oj35MfZ36MY5JBc)


<br>

---


# 2019.10.21

- **E-Drive: 19.10.9**
- E-Drive BleServer: 19.10.16
- E-Drive Tester: 19.9.1

> - 핸드 팔로잉 시 후진 속도를 낮추고 최대 속도를 제한


[Download](https://drive.google.com/open?id=1QYiBlxExXY8rORgW9tHq0Vl6WeRY_L2X)


<br>

---


# 2019.10.18

- **E-Drive: 19.10.7**
- **E-Drive BleServer: 19.10.16**
- E-Drive Tester: 19.9.1

> - 버튼 짧게 누름으로 인식하는 시간을 300ms 이내에서 2초 이내로 변경
> - 버튼 길게 누름으로 인식하는 시간을 1.2초 이상에서 3초 이상으로 변경
> - 버튼 입력 시 정해진 기능 이외에는 오류 알림 소리가 나게 함(버튼 4회 연속 입력 등)
> - 버튼 입력 시 연속 입력으로 인식하는 시간을 0.5초에서 0.6초로 변경(0.6초 이내에 버튼을 다시 누른 경우 연속 입력으로 인식)
> - 각 모드의 기본색 변경
> - 카드 코딩 시 카드 입력 시작(Red -> White), 함수 입력 시작(Green -> Yellow) 기본색을 변경
> - 카드 코딩 모드에서 카드 코딩 시작 전 LED 제어 카드를 눌렀을 때 버튼 입력 소리가 나게 함
> - 통신 보드 BLE 연결이 끊어졌을 때 밝게 깜빡이는 대신 낮은 밝기로 계속 켜져있게 함
> - 펌웨어 자동 업데이트 프로그램 수정


[Download](https://drive.google.com/open?id=1QZizFQrSQEQisZkzl0lWl3I8sgvV1e7X)


<br>

---


# 2019.10.17

- **E-Drive: 19.10.6**
- E-Drive BleServer: 19.10.14
- E-Drive Tester: 19.9.1

> - 모드 전환시 멜로디 알림
> - 핸드팔로잉 기능 추가
>   - 핸드팔로잉 카드를 읽으면 핸드팔로잉 모드로 전환
>   - 바닥에 자동차를 내려놓고 버튼을 **2회 연속** 누르거나 **3초 이상** 누르면 핸드팔로잉 동작 시작
>   - 손 또는 장애물을 자동차 정면 일정 거리 안에 두면 그것과 일정한 거리를 유지하려고 이동 시작
>   - 장애물이 일정거리 이상 멀어지거나 센서 범위를 벗어나면 노란색으로 깜빡이며 정지


[Download](https://drive.google.com/open?id=1oZvVE8qhCGT6SHjvWRQcoIPWul0nUz7G)


<br>

---


# 2019.10.16

- **E-Drive: 19.10.4**
- E-Drive BleServer: 19.10.14
- E-Drive Tester: 19.9.1

> - 모션 코딩 기능 추가
>   - 모션 코딩 카드를 읽으면 모션 코딩 모드로 전환
>   - **코딩 시작 카드**를 읽으면 동작 입력 시작
>   - 앞(전진), 뒤(후진), 좌(왼쪽으로 90도 회전), 우(오른쪽으로 90도 회전)로 기울이면 동작 입력
>   - 다시 수평으로 들면 다음 동작 입력 대기 상태가 됨
>   - 동작 입력이 끝나면 **코딩 종료 카드**를 읽어서 입력을 끝냄
>   - 바닥에 자동차를 내려놓고 버튼을 **2회 연속** 누르거나 **3초 이상** 누르면 모션 코딩 동작 시작


[Download](https://drive.google.com/open?id=14xPjBY8m6U9PoSZFOhTIUz-jQRjnYdnV)


<br>

---


# 2019.10.15

- **E-Drive: 19.10.3**
- E-Drive BleServer: 19.10.14
- E-Drive Tester: 19.9.1

> - 카드 배치 순서 변경


[Download](https://drive.google.com/open?id=1k2oiprOk_ApyQJoRGRCsTo31id5ql8AV)


<br>

---


# 2019.10.11

- **E-Drive: 19.10.2**
- E-Drive BleServer: 19.10.14
- E-Drive Tester: 19.9.1

> - E-Drive의 BLE 통신 보드 펌웨어 업데이트 기능 추가
> - Drone7Card.exe의 UI 개선


[Download](https://drive.google.com/open?id=1rG5oz9p1Ff_SK-llNb-6QiK7pkcznGSk)


<br>

---


# 2019.8.28

- **E-Drive: 19.8.3**

> - 카드 코딩과 관련된 DataType의 위치 조정, 관련 송수신 클래스 조정


[Download](https://drive.google.com/open?id=1L8Swy8QvJfmzowGek9T79n6KOj4pkXEH)


<br>

---


# 2019.8.23

- **E-Drive: 19.8.2**

> - ColorClassify 정의 추가 및 Drone7Card 프로그램에서 카드 분류 기준 값 변경가능하도록 수정함
> - 라인 코딩시에도 CARDREADER에서 분류한 카드 값을 그대로 사용


[Download](https://drive.google.com/open?id=19L5twy8qqK4s5LVczYZ-VNIpEEqpsQBq)


<br>

---


# 2019.8.8

- **E-Drive: 19.8.1**

> - 배터리 알람 기준을 30%로 변경
> - RawLineTracer에서 라인트레이서가 인식한 바닥 색상 값이 업데이트 안되는 문제 수정


[Download](https://drive.google.com/open?id=15k5s_RM6OjIFSWm5wxgxmB8nyZnjwhQx)


<br>

---


# 2019.7.26

- **E-Drive: 19.7.18**

> - State에서 modeSystem을 modeDrone으로 변경
> - 제어기 수정 사항 반영
> - RawLineTracer에서 바닥 좌우측 IR 데이터 변수 삭제


[Download](https://drive.google.com/open?id=17YawG7WzvIwktDAbe4zfEGrCq0BpCJ2S)


<br>

---


# 2019.7.25 - 2

- **E-Drive: 19.7.17**

> - Instant run에서 비상등을 브레이크 등에서 좌우 깜빡이를 동시에 작동시키는 것으로 변경(깜빡임 계속 유지)
> - Instant run에서 TailLight를 끌 때 좌우 깜빡이(비상등)도 끄게 함
> - State 클래스 수정(15 -> 11 byte)


[Download](https://drive.google.com/open?id=11A2eWzCWfYtI2IzzSCF8gMwI9xyskUe7)


<br>

---


# 2019.7.25

- **E-Drive: 19.7.16**

> - Low Battery 알림 추가
> - 카드 코딩에서 TailLight를 끌 때 좌우 깜빡이(비상등)도 끄게 함
> - 버저 버퍼를 64에서 128로 변경
> - '조건이 맞지 않으면' 카드 사용 시 조건 루프를 빠져나가는 버그 수정


[Download](https://drive.google.com/open?id=1QCVqnPEv3GDhrz_sORRgYFB5lJ2tADnG)


<br>

---


# 2019.7.24

- **E-Drive: 19.7.15**

> - 무한루프에서 버저 사용 시 1회 재생 후 버저가 완전 중단되는 문제 수정
> - 버튼을 길게 눌러 카드 코딩 실행을 할 때 실행 준비가 되면 Buzzer에서 소리가 나게 함
> - 카드 코딩에서 비상등을 브레이크 등에서 좌우 깜빡이를 동시에 작동시키는 것으로 변경(깜빡임 계속 유지)
> - 버저에 멜로디 예약 시 멜로디 전체가 들어갈 공간이 충분한 경우에만 예약하게 함


[Download](https://drive.google.com/open?id=1t7tcTjQexSAdlIIJr4DMqA9H2muomQ5M)


<br>

---


# 2019.7.23

- **E-Drive: 19.7.14**

> - 버전 구성을 (Major, Minor, Build)에서 (Year, Month, Build)로 변경함. 제품 출시 전까지 적용해보고 문제가 없을 경우 이후 출시하는 다른 제품에도 적용할 예정. 문제가 있으면 이전 구성으로 복원할 계획임

<br>
