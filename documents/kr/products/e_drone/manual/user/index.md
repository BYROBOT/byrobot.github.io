**E-Drone User Manual**

Modified : 2019.9.10

---

<h3>E-Drone 사용자 설명서</h3>

---

* Kramdown table of contents
{:toc .toc}

<br>


# 1. E-Drone

E-Drone에 대한 사용자 설명서입니다.


E-Drone의 조종기는 크게 ***조종***과 ***설정*** 두 화면으로 구성되어 있습니다.

<div align="center">
    <img src="./images/20180910_110455.jpg" alt="control"><br>
    〈조종 화면〉
</div>

조종 화면에서는 드론 조종, 트림 설정, 상태 확인 등을 할 수 있습니다.

<br>

<div align="center">
    <img src="./images/20180910_110507.jpg" alt="setup"><br>
    〈설정 화면〉
</div>

설정 화면에서는 드론 설정 변경, 상태 확인 등을 할 수 있습니다.

<br>


<br>


# 2. 버튼 구성 및 기본 기능

<div align="center">
    <img src="./images/20180910_110309.jpg" alt="controller front">
</div>
<br>

<div align="center">
    <img src="./images/20180910_110411.jpg" alt="controller top">
</div>
<br>

## 2.1. 조종 화면에서의 기능

| 번호 | 짧게 눌렀을 때                              | 길게 눌렀을 때                           |
|:----:|:--------------------------------------------|:-----------------------------------------|
| 1    | LCD 백라이트 ON/OFF                         | Return Home                              |
| 2    | -                                           | 전원 ON/OFF                              |
| 3    | Trim Pitch 증가(드론을 앞으로 향하게 함)    | -                                        |
| 4    | Trim Roll 감소(드론을 왼쪽으로 향하게 함)   | -                                        |
| 5    | Trim Roll 증가(드론을 오른쪽으로 향하게 함) | -                                        |
| 6    | Trim Pitch 감소(드론을 뒤로 향하게 함)      | -                                        |
| 7    | 이전 조종 화면으로 전환                     | 설정 화면으로 이동                       |
| 8    | 다음 조종 화면으로 전환                     | 페어링(비행 중에는 작동하지 않음)        |
| 9    | -                                           | -                                        |
| 10   | -                                           | -                                        |
| 11   | -                                           | -                                        |
| 12   | -                                           | -                                        |

## 2.2. 설정 화면에서의 기능

| 번호 | 짧게 눌렀을 때                              | 길게 눌렀을 때                           |
|:----:|:--------------------------------------------|:-----------------------------------------|
| 1    | 기능 없음                                   | -                                        |
| 2    | -                                           | 전원 ON/OFF                              |
| 3    | 메뉴 위로 이동                              | -                                        |
| 4    | 메뉴 왼쪽으로 이동                          | -                                        |
| 5    | 메뉴 오른쪽으로 이동                        | -                                        |
| 6    | 메뉴 아래로 이동                            | -                                        |
| 7    | -                                           | 조종 화면으로 이동                       |
| 8    | -                                           | 페어링(비행 중에는 작동하지 않음)        |
| 10   | -                                           | -                                        |
| 11   | -                                           | -                                        |
| 12   | -                                           | -                                        |
| 12   | 메뉴 선택 또는 메뉴 오른쪽으로 이동         | -                                        |





<br>


# 3. 설정 화면의 메뉴 구성

| 1단계             | 2단계                                     | 설명                                              |
|:------------------|:------------------------------------------|---------------------------------------------------|
| DISPLAY           | 높이-자세-RPM                             | -                                                 |
|                   | 높이-방향-RPM-자세-고도-위치              | -                                                 |
|                   | 속도-위치-자세                            | -                                                 |
|                   | 자세-높이                                 | -                                                 |
|                   | 위치-트림                                 | -                                                 |
|                   | RF 정보 및 상태                           | -                                                 |
|                   | 조이스틱 입력 값                          | -                                                 |
| LIGHT             | DRONE                                     | 드론 LED 기본 색 설정 변경                        |
|                   | CONTROLLER                                | 조종기 LED 기본 색 설정 변경                      |
| CONTROL           | ATTITUDE                                  | 자세 제어                                         |
|                   | POSITION                                  | 위치 제어                                         |
| MODE              | MODE 1                                    | L↕ Elevator, L↔ Rudder, R↕ Throttle, L↔, Aileron  |
|                   | MODE 2                                    | L↕ Throttle, L↔ Rudder, R↕ Elevator, L↔, Aileron  |
|                   | MODE 3                                    | L↕ Elevator, L↔ Aileron, R↕ Throttle, L↔, Rudder  |
|                   | MODE 4                                    | L↕ Throttle, L↔ Aileron, R↕ Elevator, L↔, Rudder  |
| HEADLESS          | HEADLESS                                  | 헤드리스(방향 고정)                               |
|                   | NORMAL                                    | 일반(드론의 현재 방향 기준)                       |
| SPEED             | S1 (50%)                                  | 속도 1단계 (50 %)                                 |
|                   | S2 (75%)                                  | 속도 2단계 (75 %)                                 |
|                   | S3 (100%)                                 | 속도 3단계 (100 %)                                |
| WEIGHT            | 100g ~ 150g                               | 드론 + 추가 장치의 무게                           |
| FUNCTION          | SENSOR RESET                              | 드론의 자이로 바이어스 리셋                       |
|                   | PAIRING                                   | 페어링                                            |
| INFORMATION       | COUNT                                     | 비행 시간 및 이벤트 카운트 값 표시                |
|                   | BIAS                                      | 가속도, 자이로 바이어스 값 표시                   |
|                   | TRIM                                      | Trim 값 표시                                      |
|                   | MOTION                                    | IMU 센서 데이터를 연산하여 변환한 결과 표시       |
|                   | ALTITUDE                                  | 높이-고도와 관련된 센서 데이터 표시               |
|                   | POSITION                                  | 위치 데이터 표시                                  |
|                   | ADDRESS/D                                 | 드론의 고유번호 표시                              |
|                   | ADDRESS/C                                 | 조종기의 고유번호 표시                            |
|                   | BOOT                                      | 조종기의 부트 정보 및 등록 여부 표시              |
|                   | CRC32                                     | 드론과 조종기의 부트로더 및 앱 영역 CRC32 값 표시 |

 * Elevator: 앞뒤 이동(Pitch)
 * Rudder: 좌우 회전(Yaw)
 * Throttle: 위아래 이동(Throttle)
 * Aileron: 좌우 이동(Roll)

<br>


# 3. 드론 펌웨어 업데이트

<b>(1) 조종기에 USB 커넥터를 연결합니다.</b>
<br>

<b>(2) 조종기 하단 중앙의 스위치를 <i>ON</i>에서 <i>USB</i>로 밀어서 전원을 켭니다.</b>

<div align="center">
    <img src="2_drone_1_on.jpg" alt="controller on">
    <p>조종기 전원을 켠 상태</p>
</div>
<br>

<b>(3) 드론의 전원이 꺼진 상태에서 드론 측면의 버튼을 누른 채로 배터리를 밀어 넣어 전원을 켭니다. 드론이 부트로더의 펌웨어 업데이트 모드가 되면 LED가 하늘색으로 느리게 깜빡입니다.</b>

<div align="center">
    <img src="2_drone_2_side_button.jpg" alt="drone switch">
    <p>드론 측면 스위치를 누른 상태에서 배터리를 연결</p>
</div>
<br>

<b>(4) 드론이 부트로더의 펌웨어 업데이트 모드로 켜진 상태에서 조종기와 연결된 경우 아래와 같은 화면을 볼 수 있습니다. 만약 드론과 조종기의 전원이 모두 켜진 상태에서 아래와 같은 화면이 나오지 않고 연결이 끊어졌다고 표시되는 경우 페어링을 하셔야 합니다. 보통 때의 페어링과 동일한 방법으로, 전원이 켜진 상태에서 드론 측면의 버튼을 길게 눌러서 페어링 대기 상태로 만들고, 조종기를 설정 모드로 바꾼 다음 조종기의 우측 하단의 원형 버튼을 길게 눌러서 페어링을 하시면 됩니다.</b>

<div align="center">
    <img src="2_drone_3_drone_connected.jpg" alt="update ready">
    <p>드론 펌웨어 업데이트 모드</p>
</div>
<br>

<b>(5) 펌웨어 업데이트 프로그램을 실행한 뒤 펌웨어 선택 콤보박스에서 드론 펌웨어를 선택합니다.</b>

<div align="center">
    <img src="2_drone_4_firmware_combobox.jpg" alt="firmware combobox">
    <p>펌웨어 선택 콤보박스</p>
</div>
<br>

<div align="center">
    <img src="2_drone_5_firmware_selected.jpg" alt="firmware selected">
    <p>드론 펌웨어를 선택한 후 화면</p>
</div>
<br>

<b>(6) SCAN 버튼을 눌러 시리얼 포트 검색을 실행합니다. 그 후 SCAN 버튼 하단의 콤보 박스를 눌러 원하는 시리얼 포트를 선택합니다. 조종기를 먼저 연결한 후 프로그램을 실행하였다면 이 단계를 건너뛰셔도 됩니다.</b>

<div align="center">
    <img src="2_drone_6_scan.jpg" alt="scan">
    <p>스캔 버튼</p>
</div>
<br>

<b>(7) UPDATE 버튼을 눌러 펌웨어 업데이트를 시작합니다.</b>

<div align="center">
    <img src="2_drone_7_update.jpg" alt="update">
    <p>업데이트 버튼</p>
</div>
<br>

<div align="center">
    <img src="2_drone_8_firmware_update.jpg" alt="update">
    <p>업데이트 진행 화면</p>
</div>
<br>

<div align="center">
    <img src="2_drone_9_update_controller.jpg" alt="update controller">
    <p>드론 펌웨어 업데이트 시 조종기 업데이트 진행 화면</p>
</div>
<br>

<b>(8) 업데이트가 완료된 후 조종기 또는 드론의 전원을 껐다 켜면 드론이 새로운 펌웨어로 시작합니다.</b>

<div align="center">
    <img src="2_drone_10_firmware_update_complete.jpg" alt="update complete">
    <p>드론 업데이트 완료 상태</p>
</div>
<br>

<br>


여기까지 E-Drone 조종기와 드론의 펌웨어 업데이트를 완료하였습니다.

