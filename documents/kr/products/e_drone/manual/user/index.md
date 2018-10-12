**[E-DRONE](/documents/kr/products/e_drone/) User Manual**

Modified : 2018.10.12

---

<h3>E-Drone 사용자 설명서</h3>

---

* Kramdown table of contents
{:toc .toc}

<br>


# 1. 드론


## 1.1. 좌표계

E-Drone은 오른손 좌표계를 사용하고 있습니다.

| 좌표축  | +        | -        |
|:-------:|:--------:|:--------:|
| X       | 앞       | 뒤       |
| Y       | 왼쪽     | 오른쪽   |
| Z       | 위       | 아래     |
| Z 회전  | 반시계   | 시계     |

아래 문서의 Figure 6 이미지를 참고하시기 바랍니다.

[http://www.physics.brocku.ca/PPLATO/h-flap/math2_5.html#section_3](http://www.physics.brocku.ca/PPLATO/h-flap/math2_5.html#section_3)



<br>

<br>



# 2. 조종기


## 2.1 조종기 화면 구성

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


## 2.2. 버튼 구성 및 기능

<div align="center">
    <img src="./images/e_drone_controller_front_nunber.jpg" alt="controller front">
</div>
<br>

<div align="center">
    <img src="./images/e_drone_controller_top_nunber.jpg" alt="controller top">
</div>
<br>

### 2.2.1. 조종 화면

| 번호 | 짧게 눌렀을 때                              | 길게 눌렀을 때                           |
|:----:|:--------------------------------------------|:-----------------------------------------|
| 1    | LCD 백라이트 ON/OFF                         | Return Home                              |
| 2    | LCD 초기화(화면이 뒤집히는 경우 사용)       | 전원 ON/OFF                              |
| 3    | Trim Pitch 증가(드론을 앞으로 향하게 함)    | -                                        |
| 4    | Trim Roll 감소(드론을 왼쪽으로 향하게 함)   | -                                        |
| 5    | Trim Roll 증가(드론을 오른쪽으로 향하게 함) | -                                        |
| 6    | Trim Pitch 감소(드론을 뒤로 향하게 함)      | -                                        |
| 7    | 이전 조종 화면으로 전환                     | 설정 화면으로 이동                       |
| 8    | 다음 조종 화면으로 전환                     | 페어링(비행 중에는 작동하지 않음)        |
| 9    | -                                           | -                                        |
| 10   | -                                           | -                                        |
| 11   | -                                           | 이륙 / 착륙                              |
| 12   | -                                           | -                                        |

 * 좌측 조이스틱을 아래로 향한 상태에서 11번 버튼을 누르면 정지 명령을 전송합니다.

<br>

### 2.2.2. 설정 화면

| 번호 | 짧게 눌렀을 때                              | 길게 눌렀을 때                           |
|:----:|:--------------------------------------------|:-----------------------------------------|
| 1    | -                                           | -                                        |
| 2    | LCD 초기화(화면이 뒤집히는 경우 사용)       | 전원 ON/OFF                              |
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


<br>


## 2.3. 설정 화면 메뉴 구성

<table>
    <tr>
        <td>
            <div align="center">
                1단계
            </div>
        </td>
        <td>
            <div align="center">
                2단계
            </div>
        </td>
        <td>
            <div align="center">
                설명
            </div>
        </td>
    </tr>
    <tr>
        <td rowspan="7">
            <div align="center">
                DISPLAY
            </div>
        </td>
        <td>
            <div align="center">
                높이-자세-RPM
            </div>
        </td>
        <td>
            <div align="left">
                조종 화면에서 보여줄 것인지를 설정(SHOW / HIDE)
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div align="center">
                높이-방향-RPM-자세-고도-위치
            </div>
        </td>
        <td>
            <div align="left">
                조종 화면에서 보여줄 것인지를 설정(SHOW / HIDE)
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div align="center">
                속도-위치-자세
            </div>
        </td>
        <td>
            <div align="left">
                조종 화면에서 보여줄 것인지를 설정(SHOW / HIDE)
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div align="center">
                자세-높이
            </div>
        </td>
        <td>
            <div align="left">
                조종 화면에서 보여줄 것인지를 설정(SHOW / HIDE)
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div align="center">
                위치-트림
            </div>
        </td>
        <td>
            <div align="left">
                조종 화면에서 보여줄 것인지를 설정(SHOW / HIDE)
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div align="center">
                RF 정보 및 상태
            </div>
        </td>
        <td>
            <div align="left">
                조종 화면에서 보여줄 것인지를 설정(SHOW / HIDE)
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div align="center">
                조이스틱 입력 값
            </div>
        </td>
        <td>
            <div align="left">
                조종 화면에서 보여줄 것인지를 설정(SHOW / HIDE)
            </div>
        </td>
    </tr>
    <tr>
        <td rowspan="2">
            <div align="center">
                LIGHT
            </div>
        </td>
        <td>
            <div align="center">
                DRONE
            </div>
        </td>
        <td>
            <div align="left">
                드론 LED 기본 색 설정 변경
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div align="center">
                CONTROLLER
            </div>
        </td>
        <td>
            <div align="left">
                조종기 LED 기본 색 설정 변경
            </div>
        </td>
    </tr>
    <tr>
        <td rowspan="2">
            <div align="center">
                CONTROL
            </div>
        </td>
        <td>
            <div align="center">
                ATTITUDE
            </div>
        </td>
        <td>
            <div align="left">
                자세 제어
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div align="center">
                POSITION
            </div>
        </td>
        <td>
            <div align="left">
                위치 제어
            </div>
        </td>
    </tr>
    <tr>
        <td rowspan="4">
            <div align="center">
                MODE
            </div>
        </td>
        <td>
            <div align="center">
                MODE 1
            </div>
        </td>
        <td>
            <div align="left">
                L↕ Elevator, L↔ Rudder, R↕ Throttle, R↔ Aileron<br>
                L↕ 앞뒤, L↔ 좌우 회전, R↕ 위아래, R↔ 좌우
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div align="center">
                MODE 2
            </div>
        </td>
        <td>
            <div align="left">
                L↕ Throttle, L↔ Rudder, R↕ Elevator, R↔ Aileron<br>
                L↕ 위아래, L↔ 좌우 회전, R↕ 앞뒤, R↔ 좌우
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div align="center">
                MODE 3
            </div>
        </td>
        <td>
            <div align="left">
                L↕ Elevator, L↔ Aileron, R↕ Throttle, R↔ Rudder<br>
                L↕ 앞뒤, L↔ 좌우, R↕ 위아래, R↔ 좌우 회전
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div align="center">
                MODE 4
            </div>
        </td>
        <td>
            <div align="left">
                L↕ Throttle, L↔ Aileron, R↕ Elevator, R↔ Rudder<br>
                L↕ 위아래, L↔ 좌우, R↕ 앞뒤, R↔ 좌우 회전
            </div>
        </td>
    </tr>
    <tr>
        <td rowspan="2">
            <div align="center">
                HEADLESS
            </div>
        </td>
        <td>
            <div align="center">
                HEADLESS
            </div>
        </td>
        <td>
            <div align="left">
                헤드리스(방향 고정)
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div align="center">
                NORMAL
            </div>
        </td>
        <td>
            <div align="left">
                일반(드론의 현재 방향 기준)
            </div>
        </td>
    </tr>
    <tr>
        <td rowspan="3">
            <div align="center">
                HEADLESS
            </div>
        </td>
        <td>
            <div align="center">
                S1 (30%)
            </div>
        </td>
        <td>
            <div align="left">
                속도 1단계 (50 %)
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div align="center">
                S2 (70%)
            </div>
        </td>
        <td>
            <div align="left">
                속도 2단계 (70 %)
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div align="center">
                S3 (100%)
            </div>
        </td>
        <td>
            <div align="left">
                속도 3단계 (100 %)
            </div>
        </td>
    </tr>
    <tr>
        <td rowspan="3">
            <div align="center">
                FUNCTION
            </div>
        </td>
        <td>
            <div align="center">
                SENSOR RESET
            </div>
        </td>
        <td>
            <div align="left">
                드론의 자이로 바이어스 리셋
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div align="center">
                PAIRING
            </div>
        </td>
        <td>
            <div align="left">
                페어링
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div align="center">
                SET DEFAULT
            </div>
        </td>
        <td>
            <div align="left">
                설정값 초기화(드론이 연결된 경우 드론 설정도 초기화 됨)
            </div>
        </td>
    </tr>
    <tr>
        <td rowspan="9">
            <div align="center">
                INFORMATION
            </div>
        </td>
        <td>
            <div align="center">
                COUNT
            </div>
        </td>
        <td>
            <div align="left">
                비행 시간 및 이벤트 카운트 값 표시
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div align="center">
                BIAS
            </div>
        </td>
        <td>
            <div align="left">
                가속도, 자이로 바이어스 값 표시
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div align="center">
                TRIM
            </div>
        </td>
        <td>
            <div align="left">
                Trim 값 표시
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div align="center">
                MOTION
            </div>
        </td>
        <td>
            <div align="left">
                IMU 센서 데이터를 연산하여 변환한 결과 표시
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div align="center">
                ALTITUDE
            </div>
        </td>
        <td>
            <div align="left">
                높이-고도와 관련된 센서 데이터 표시
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div align="center">
                POSITION
            </div>
        </td>
        <td>
            <div align="left">
                위치 데이터 표시
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div align="center">
                ADDRESS
            </div>
        </td>
        <td>
            <div align="left">
                드론과 조종기의 고유번호 표시
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div align="center">
                BOOT
            </div>
        </td>
        <td>
            <div align="left">
                조종기의 부트 정보 및 장치 등록 여부 표시
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div align="center">
                CRC32
            </div>
        </td>
        <td>
            <div align="left">
                드론과 조종기의 부트로더 및 앱 영역 CRC32 값 표시
            </div>
        </td>
    </tr>
</table>

 * Elevator : 앞뒤 이동(Pitch)
 * Rudder : 좌우 회전(Yaw)
 * Throttle : 위아래 이동(Throttle)
 * Aileron : 좌우 이동(Roll)

<br>



여기까지 E-Drone 조종기와 드론에 대한 간략한 설명이었습니다.

