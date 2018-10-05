**[E-DRONE](/documents/kr/products/e_drone/) update log**

Modified : 2018.10.5

---

* Kramdown table of contents
{:toc .toc}


<br>


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
