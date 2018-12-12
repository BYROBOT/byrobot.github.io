**[E-DRONE](/documents/kr/products/e_drone/) update log**

Modified : 2018.12.12

---

* Kramdown table of contents
{:toc .toc}


<br>


# 2018.12.12

- **Drone: 1.0.6**
- **Controller: 1.0.7**

> - 제품 생산 관련 문제로 12월 11일 버전에서 변경했던 RF 데이터 송수신부 처리 방법과 페어링 변경 사항을 이전 상태로 되돌림(추후 다시 적용할 예정)
> - DeviceType::Tester, DeviceType::Monitor 장치가 조종기와 USB로 연결된 경우 전원 버튼으로 [Link] <-> [조종] 모드 전환을 못하게 막음


[Download](https://drive.google.com/open?id=1bfUo0DlxnkkrpQMV0S6yIWEDJCGH4_yL)


<br>

---


# 2018.12.11

- **Drone: 1.0.5**
- **Controller: 1.0.6**

> - 무게 150g에서 호버링 안정화
> - 리턴 홈 기능 안정화
> - RF 통신 데이터 송수신부분 수정(업데이트 이후에는 이전 조종기 또는 드론과 통신이 안됨)
> - 드론과 조종기 페어링 시 드론이 새로운 주소를 생성하게 함(여러 드론이 하나의 조종기와 페어링되는 현상을 막기 위함)
> - USB에 PC가 연결된 상태일 때 전원 버튼으로 조종 <-> 링크 모드 전환 가능하게 함


[Download](https://drive.google.com/open?id=1SO7FqX1txobr0dopoVJavsJf6rgjI5sB)


<br>

---


# 2018.12.4

- **Drone: 1.0.4**
- **Controller: 1.0.5**

> - Reverse 경고 활성화(이륙 실패 시에만 표시)
> - 바이블럭에서 10% 조종기값 적용 안되는 현상 수정
> - 이륙 속도를 0.7m/s로 변경
> - 모드 1, 3, 4에서 수동 이륙 가능하게 함


[Download](https://drive.google.com/open?id=1-TvDtzoEYvBLOGVrtsiwF4hcQWuIZz2g)


<br>

---


# 2018.11.29

- **Drone: 1.0.3**
- **Controller: 1.0.4**

> - 고도 안정화
> - 호버링 안정화
> - RF 동일 채널을 사용하는 조종기가 있을 때의 조종 안정성 향상
> - 조종 화면 중 조이스틱 화면에 실제 드론에 전달하는 조종 값을 표시(모드에 따라 R, P, Y, T의 위치가 바뀜)
> - 조종 화면 중 RF 화면 중앙 그래프 내부의 폰트를 10x16으로 변경
> - 조종 화면 중 RF 화면 우측 하단에 응답 수신률의 평균 값을 표시


[Download](https://drive.google.com/open?id=1z55A8It5IpabF8iPVIUSqAdGvA86qIE-)


<br>

---


# 2018.11.28

- Drone: 1.0.2
- **Controller: 1.0.3**

> - 이착륙 버튼을 사용 중 낮은 확률로 조종이 중단되는 문제 수정
> - 이착륙 버튼 아래의 버튼을 눌렀을 때 Link 모드로 전환되는 문제 수정
> - LINK 모드에서도 주기적으로 드론의 데이터 요청(배터리 잔량 업데이트 등에 사용)
> - LINK 모드에서 처음 PC에서 데이터를 받기 전까지 조이스틱과 버튼을 조작할 수 없었던 문제 수정
> - LINK 모드일 때 특정 장치로부터 데이터를 받은 후 부터 조이스틱과 버튼 입력을 PC에 전송하게 함(Tester, Monitor, Scratch, Entry, ByScratch)
> - LINK 모드에서 전원 버튼을 짧게 눌렀다가 떼면 조종 모드로 전환(드론에 문제가 생긴 경우 사용, 다시 LINK 모드로 전환하려면 USB를 분리했다 다시 연결해야 함)


[Download](https://drive.google.com/open?id=16KZXNAf9SRyKWoXe7c6Uim_2tzBm428e)


<br>

---


# 2018.11.27

- **Drone: 1.0.2**
- **Controller: 1.0.2**

> - RF 연결과 관련된 Light 이벤트 수정
> - 고도 튀는 현상 수정


[Download](https://drive.google.com/open?id=1N6DntJUG3G6K3NXd8F02Uiu7ub6ykaWv)


<br>

---


# 2018.11.26

- **Drone: 1.0.1**
- **Controller: 1.0.1**

> - 고도, 회번, 자세, 플립 비행 안정화
> - 드론 비행 시간을 시:분:초 로 표시하게 함. 이전에는 ms로 표시
> - 배터리가 30% 미만이거나 기체가 무거울 때 플립을 할 수 없음
> - 충돌 시 모터가 정지하지 않는 문제 수정
> - 백라이트 ON/OFF 설정을 플래시 메모리에 저장
> - 드론과 조종기의 모든 LED 동작 모드에 Sunrise, Sunset 추가
> - 조종기 설정 화면 Light 메뉴에 SUNRISE, SUNSET 모드를 추가
> - 조종기 전면 좌측 위의 버튼을 짧게 누르면 속도 변경
> - 조종기 전면 우측 위의 버튼을 짧게 누르면 LED 기본 색상 변경(R, G, B, C, M, Y, W 순서로 바뀜)
> - 데이터 저장 블럭의 크기를 512바이트에서 256바이트로 줄임
> - RF 데이터 송수신 구조 수정
> - 조종기에서 페어링 시 페어링에 필요한 데이터 이외에는 전송 차단
> - 동작 중 RF 칩이 리셋되면 RF 칩 초기화
> - **Control::Position** 내부 변수 중 **heading**과 **rotationalVelocity**의 변수형을 **float**에서 **int16_t**로 변경
> - InformationAssembledForController의 angleRoll, anglePitch 크기를 1바이트에서 2바이트로 변경


[Download](https://drive.google.com/open?id=13q17lFeyqPS8W_RzjMmsjY2iCOL7-Vmb)


<br>

---


# 2018.11.2

- **Drone: 1.0.0**
- **Controller: 1.0.0**

> - 정식 제품 출시


<br>

---


# 2018.10.31 - 2

- **Drone: 0.2.19**
- Controller: 0.2.15

> - 바이스크래치 블럭 코딩에서 오른쪽으로 회전하지 않는 현상 수정


[Download](https://drive.google.com/open?id=12laWDx2UjLTwVd3jOeRJuYEWvmkY6vx6)


<br>

---


# 2018.10.31

- **Drone: 0.2.18**
- Controller: 0.2.15

> - 드론에서 외부 Range 센서 모듈의 데이터를 수집
> - 드론에 'DataType::Range'를 요청 시 외부 Range 센서의 데이터를 통합하여 전달(센서가 연결되지 않은 경우 -1, 연결되었으나 감지할 수 있는 거리를 벗어난 경우 8000이 넘는 값을 출력함. 값의 단위는 mm)
> - 호버링 안정화


[Download](https://drive.google.com/open?id=1pcdTc3TwpIynK6D0kJO_ugnlO5ZFFSTj)


<br>

---


# 2018.10.26

- **Drone: 0.2.17**
- **Controller: 0.2.15**

> - Control::Position16에서 x, y, z에 대한 각각의 속도를 하나의 속도 값으로 사용하도록 변경함
> - yaw 회전 방향 수정(+값 입력 시 반시계 방향으로 회전)
> - RF 송수신 중단 시 주기적으로 Ping 전송
> - 고도, 속도 안정화
> - 리턴 홈 안정화
> - CommandType에 조종기 백라이트 제어 추가
> - Range 센서 데이터 구조체 추가
> - 조종기를 USB에 연결하여 전원이 켜지는 경우 로고를 표시하지 않게 함


[Download](https://drive.google.com/open?id=1sBZC7AsoRa8H6IQDhcsT9CMiU8919anL)


<br>

---


# 2018.10.16

- **Drone: 0.2.16**
- Controller: 0.2.14

> - 비행 제어 설정이 Position 모드일 때에만 바닥 이미지 경고 활성화
> - 비행 제어 설정이 Attitude 모드일 때에만 트림 값 적용
> - Flow 센서 설정 변경

[Download](https://drive.google.com/open?id=1EOwzym4Ncf7neTeluddCu6258EufrfwV)


<br>

---


# 2018.10.15

- **Drone: 0.2.15**
- **Controller: 0.2.14**

> - Flow 센서 설정 변경
> - 회전 명령 시에 계속 도는 문제 수정
> - Attitude Mode 일 때 최대 각도 40에서 35도로 줄임
> - Trim 설정값을 무시하게 함(Trim 적용 방법 변경 예정)

[Download](https://drive.google.com/open?id=1frTwqh9EYkJAiVj9LugHLo02DE3VCvBl)


<br>

---


# 2018.10.12

- **Drone: 0.2.14**
- **Controller: 0.2.13**

> - Flow 센서와 관련된 설정 변경
> - Attitude 모드에서만 조이스틱 Yaw 조작 시 속도 변경 적용, Position 모드에서는 속도 변경과 상관없이 고정(180deg/s)
> - 조종기 설정 메뉴에서 Weight 설정 제거
> - 드론이 연결되지 않은 경우 Version, Address, CRC 표시창에서 조종기의 정보만 표시

[Download](https://drive.google.com/open?id=1xe-Qdtrq0MugPBwr8ihBoZrAaZ2QJXB3)


<br>

---


# 2018.10.11

- **Drone: 0.2.13**
- **Controller: 0.2.12**

> - 드론이 비행중일 때 Control, Mode, Headless, Function 메뉴에 진입할 수 없게 막음
> - 프로펠러 진동 경고
> - 스피드 설정 변경 시 회전 속도도 변함
> - 고도 유지 안정화
> - 호버링 안정화
> - 이륙 안정화
> - Information에 RF 항목 추가

[Download](https://drive.google.com/open?id=1Ns7FeEJifz3UG3OXGHZ--GhBcn3YCoZ_)


<br>

---


# 2018.10.8

- **Drone: 0.2.12**
- **Controller: 0.2.11**

> - 드론 고도 제어 안정화
> - X, Y 위치 안정화
> - Weight 설정 변경 없이 작동할 수 있도록 제어 변경(현재는 Weight 설정을 무시)
> - 에러 플래그 이름 수정
> - 프로펠러, 모터 문제로 이륙이 안되는 경우 오류 메세지 출력
> - 모든 UART, USB 시리얼 통신의 Baudrate를 57600으로 변경
> - 배터리 경고 이외에 무선 연결 끊어짐, 프로펠러-모터 문제로 이륙 불가, 바닥 이미지 인식 불가, Motion 센서 캘리브레이션 진동 알림 추가

[Download](https://drive.google.com/open?id=1Jefp48LHR00dRrWSEIMVFJNOrADs0K59)


<br>

---


# 2018.10.5

- **Drone: 0.2.11**
- **Controller: 0.2.10**

> - 드론 고도 제어 안정화
> - 바닥 이미지를 인식할 수 없을 때의 제어 처리 및 조종기에 상태 알림 추가
> - 드론, 조종기 앱 동작 시 UART의 Baudrate를 57600으로 변경함. 부트로더에서는 아직 115200 사용 중
> - 드론 UART 통신 안정화
> - 비행 중 컨트롤 모드 변경 불가능하게 막음
> - 드론, 조종기의 RF 주소가 0, 0, 0인 경우 RF 데이터 송수신을 차단

[Download](https://drive.google.com/open?id=1n3gUKYbTCdR6DowdWxySC_OZWJIB4xDl)


<br>

---


# 2018.10.2

- **Drone: 0.2.10**
- **Controller: 0.2.9**

> - 드론 부팅 시 각 센서를 초기화 할 때 정상적으로 연결되지 않는 경우 관련 ERROR 플래그를 활성화하게 함
> - 조종기의 드론 오류와 관련된 메세지 출력 부분 수정
> - 조종기에서 "SET DEFAULT" 선택 시 weight, trim이 초기화되지 않는 문제 수정
> - 조종기 Function 메뉴에서도 드론의 상태 데이터 요청("SET DEFAULT"를 실행했을때 상단 상태 표시줄의 값이 바뀌지 않는 문제가 있었음)
> - 조종기 Information 메뉴의 Altitude, Position 값 소수점 표시 위치를 일치시킴
> - 화면 상단 상태 표시줄의 텍스트 간격을 3에서 4로 변경

[Download](https://drive.google.com/open?id=1Z4ObTvkYi-pkSR1zpvyTJyI3o3vmYYLW)


<br>

---


# 2018.10.1

- **Drone: 0.2.9**
- **Controller: 0.2.8**

> - 드론, 조종기 기본 색을 Green으로 변경
> - 드론을 UART 또는 USB로 연결해서 이륙했을 때 바로 멈추는 문제 수정
> - 고도 제어 안정화
> - 비행 안정화

[Download](https://drive.google.com/open?id=12P5_t1x8C8ePndzkB1kkVVcQQmiAVgC_)


<br>

---


# 2018.9.28

- **Drone: 0.2.8**
- **Controller: 0.2.7**

> - 드론, 조종기 기본 색을 White로 변경
> - DataType에 LostConnection을 추가. 마지막으로 조종 명령을 전송한 장치와의 연결이 끊어진 후, 여기에서 설정한 시간이 지나면 설정된 동작(조종 중립, 착륙, 강제 정지)을 실행. 시간 값을 0으로 설정할 경우 해당 동작은 실행하지 않음. 현재는 수정한 값을 플래시에 저장하지 않음. 그래서 매번 드론을 새로 부팅할 때마다 지정해야 함. 기본 연결 장치는 RF.
> - 조종기 USB를 제거하면 RF와 LCD를 리셋(화면 반전 및 RF 연결 끊어짐 문제 해결)
> - Trim  화면에 Height(Range 센서의 값) 대신 Z(고도)를 표시
> - 비행 안정화

[Download](https://drive.google.com/open?id=13YRVPrqF1b_TGNp4kB4Uzw2rtD0BU82r)


<br>

---


# 2018.9.21 - 3

- **Drone: 0.2.7**
- Controller: 0.2.6

> - RF를 통해 드론 제어 중 RF 연결이 끊기면 10초 후 착륙 시작, 2분 후 강제 정지
> - 착륙 시 조종 중립, 목표 위치 초기화

[Download](https://drive.google.com/open?id=1hcrZP4-3Cyx9UXgjHJz2oz_ofnEIXitH)


<br>

---


# 2018.9.21 - 2

- Drone: 0.2.6
- **Controller: 0.2.6**

> - 페어링 성공/실패 시 조종기 Buzzer 소리 알림 활성화


<br>

---


# 2018.9.21

- **Drone: 0.2.6**
- **Controller: 0.2.5**

> - 드론 이륙을 전면 왼쪽 상단 버튼을 길게 눌러서 하는 것으로 변경. 조이스틱 Throttle 조작으로 이륙하는 것은 막음
> - 조종기 배터리가 5% 이하로 남았을 때에만 경고 창이 나타나고 진동이 발생하도록 수정
> - 트림 최대값 변경
> - 배터리 잔량 계산부 수정
> - 배터리 진동 경고 활성화
> - 전원 버튼을 짧게 누르면 LCD를 초기화 하게 함(화면이 위아래로 뒤집히는 경우 사용)
> - 기본 화면에 트림 화면을 추가
> - 드론과 조종기의 설정을 기본 값으로 바꾸는 명령을 추가(CommandType::SetDefault)
> - 조종기 설정 메뉴 중 'FUNCTION'에 'SET DEFAULT'를 추가. 실행 시 연결된 드론이 있는 경우 드론의 설정값까지 같이 초기화 됨(트림, 조종 화면 설정, LED 기본 색상, 무게 설정, 속도, 헤드리스, 모드 등)
> - 위치 기반 이동 명령 성능 개선
> - 드론이 뒤집히면 정지


<br>

---


# 2018.9.18 - 2

- **Drone: 0.2.4**
- **Controller: 0.2.4**

> - 화면 상단의 상태 표시줄에 Control과 Headless 정보를 한 문자로 표시하게 함
> - 조종 입력값 범위를 30, 70, 100%로 변경
> - RSSI 안테나 표시 기준 변경
> - 야외 비행 시 고도 제어 안정화

<br>

---


# 2018.9.18

- **Drone: 0.2.3**
- **Controller: 0.2.3**

> - 조종 모드에서 조종기 전원 버튼을 짧게 누르면 LCD를 리셋함.(화면이 반전된 경우에 사용)
> - 센서의 RAW 데이터를 읽는데 사용하는 RawFlow, RawMotion 구조체를 추가
> - 조종기 부트로더 진입 시 진동 발생하는 문제 수정
> - Motion 구조체로 전달하는 Accel과 Gyro값을 지정한 단위에 맞추어 계산한 값으로 변경
> - Control::Position16, Control::Position 명령 추가함(위치와 속도로 이동 명령을 내릴 때 사용)
> - 비행 안정화

<br>

---


# 2018.9.14

- **Drone: 0.2.2**
- **Controller: 0.2.2**

> - LED 초기 설정 저장 버그 수정
> - RF 이외의 장치로 조종 명령을 받았을 때, RF 연결 중단에 의해 드론이 멈추는 현상이 발생하지 않게 함(아두이노 등의 장치로 드론에 직접 연결해서 제어하는 경우 RF가 끊어진 상태이기 때문에 강제 착륙 명령이 들어가서 이륙을 할 수 없는 문제가 있었음)
> - RF 이외의 장치로 조종 명령을 받았을 때, RF 연결 이벤트 발생 시 후면 LED를 제어하지 않게 함(아두이노 등의 장치로 드론에 직접 연결해서 제어하는 경우 해당 장치가 후면 LED를 제어할 수 있게 하고, RF 연결 이벤트에 의해 LED 설정이 바뀌지 않게 함)
> - 조종 화면 설정 내용을 플래시 메모리에 저장하여 조종기를 다시 부팅했을 때 이전 설정이 유지되도록 함

<br>

---


# 2018.9.10

- **Drone: 0.2.1**
- **Controller: 0.2.1**

> - 장치 등록 절차 변경
> - 여러 형태로 나누어져 있던 LED 설정 변경을 LightMode, LightEvent, LightDefault로 통합
> - Protocol의 DataType의 순서를 다시 정리(기존의 펌웨어 업데이트, 모니터 등의 프로그램을 사용할 수 없음)
> - 조종기, 드론의 기본색 설정 변경 가능

<br>

---


# 2018.7.10

- Drone: 0.1.2
- **Controller: 0.1.3**

> - 조종기 화면 전환 부분 구조 개선 및 버튼을 짧게 눌렀을 때 전환 화면이 계속 남아있는 문제 수정
> - 조종기 좌상단 버튼을 길게 눌러서 백라이트 ON/OFF 할 때 화면에 표시하게 함

<br>

---


# 2018.7.9

- **Drone: 0.1.2**
- **Controller: 0.1.2**

> - PC에서 드론에 데이터 요청 시 응답으로 돌아오는 데이터의 CRC 값이 0으로 초기화 되어 있는 문제 수정

<br>

---


# 2018.7.5

- **Drone: 0.1.1**
- **Controller: 0.1.1**

> - 펌웨어 릴리즈

<br>
