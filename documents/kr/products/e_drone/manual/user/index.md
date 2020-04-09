<style>

    td.spec       { background: #EEFAFA !important; }
    td.coord      { background: #FFF9FA !important; }
    td.setup_odd  { background: #FFFEF5 !important; }
    td.setup_even { background: #F5FAFF !important; }
    td.white      { background: #FFFFFF !important; }

    td.joystick_left   { background: #FFF5F5 !important; }
    td.joystick_right  { background: #F5F5FF !important; }

    td.throttle   { background: #FFDDDD !important; }
    td.rudder     { background: #FFFFDD !important; }
    td.elevator   { background: #DDFFFF !important; }
    td.aileron    { background: #DDFFDD !important; }

</style>

**[E-DRONE](/documents/kr/products/e_drone/) User Manual**

Modified : 2020.4.10

---

<h3>E-DRONE 사용자 설명서</h3>

---

* Kramdown table of contents
{:toc .toc}

<br>


# 1. 드론

<div align="center">
    <img src="./images/byrobot_drone_4.jpg" alt="E-DRONE" width="600" height="600">
    <p>E-DRONE</p>
</div>


<br>

## 1.1. 사양

<br>

<div align="center">
    <table>
        <tr>
            <td class="spec"><div align="center"><b>항목</b></div></td>
            <td class="spec"><div align="center"><b>E-DRONE</b></div></td>
        </tr>
        <tr>
            <td class="spec"><div align="center">모터 축간 대각선 길이</div></td>
            <td class="white"><div align="center">135 mm</div></td>
        </tr>
        <tr>
            <td class="spec"><div align="center">무게</div></td>
            <td class="spec"><div align="center">113g<br>(배터리 포함)</div></td>
        </tr>
        <tr>
            <td class="spec"><div align="center">배터리</div></td>
            <td class="white"><div align="center">7.4V<br>1,000mAh<br>LiPo(Lithium polymer) battery</div></td>
        </tr>
        <tr>
            <td class="spec"><div align="center">비행시간</div></td>
            <td class="spec"><div align="center">7 ~ 10분</div></td>
        </tr>
        <tr>
            <td class="spec"><div align="center">최대조종거리</div></td>
            <td class="white"><div align="center">50m</div></td>
        </tr>
        <tr>
            <td class="spec"><div align="center">통신방식</div></td>
            <td class="spec"><div align="center">2.4Ghz RF</div></td>
        </tr>
        <tr>
            <td class="spec"><div align="center">조종 모드</div></td>
            <td class="white"><div align="center">Mode 1, 2, 3, 4</div></td>
        </tr>
        <tr>
            <td class="spec" rowspan="4"><div align="center">센서</div></td>
            <td class="spec"><div align="center">Optical flow</div></td>
        </tr>
        <tr>
            <td class="white"><div align="center">6-Axis MEMS MotionTracking</div></td>
        </tr>
        <tr>
            <td class="spec"><div align="center">IR Time of Flight</div></td>
        </tr>
        <tr>
            <td class="white"><div align="center">Barometer</div></td>
        </tr>
        <tr>
            <td class="spec" rowspan="3"><div align="center">확장</div></td>
            <td class="spec"><div align="center">4핀 UART 포트(RX, TX, 5V, GND) x 2</div></td>
        </tr>
        <tr>
            <td class="white"><div align="center">RGB LED 포트 x 1</div></td>
        </tr>
        <tr>
            <td class="spec"><div align="center">단색 LED 포트 x 2</div></td>
        </tr>
        <tr>
            <td class="spec" rowspan="3"><div align="center">주요기능</div></td>
            <td class="white"><div align="center">실내 위치 인식</div></td>
        </tr>
        <tr>
            <td class="spec"><div align="center">Return Home</div></td>
        </tr>
        <tr>
            <td class="white"><div align="center">앱, 파이썬 코딩</div></td>
        </tr>
    </table>
</div>


<br>



## 1.2. 좌표계

E-DRONE은 오른손 좌표계를 사용하고 있습니다.

<div align="center">
    <table>
        <tr>
            <td class="coord"><div align="center"><b>좌표축</b></div></td>
            <td class="coord"><div align="center"><b>+</b></div></td>
            <td class="coord"><div align="center"><b>-</b></div></td>
        </tr>
        <tr>
            <td class="coord"><div align="center">X</div></td>
            <td class="white"><div align="center">앞</div></td>
            <td class="white"><div align="center">뒤</div></td>
        </tr>
        <tr>
            <td class="coord"><div align="center">Y</div></td>
            <td class="coord"><div align="center">왼쪽</div></td>
            <td class="coord"><div align="center">오른쪽</div></td>
        </tr>
        <tr>
            <td class="coord"><div align="center">Z</div></td>
            <td class="white"><div align="center">위</div></td>
            <td class="white"><div align="center">아래</div></td>
        </tr>
        <tr>
            <td class="coord"><div align="center">Z 회전</div></td>
            <td class="coord"><div align="center">반시계</div></td>
            <td class="coord"><div align="center">시계</div></td>
        </tr>
    </table>
</div>

아래 문서의 Figure 6 이미지를 참고하시기 바랍니다.

[http://www.physics.brocku.ca/PPLATO/h-flap/math2_5.html#section_3](http://www.physics.brocku.ca/PPLATO/h-flap/math2_5.html#section_3)



<br>

<br>



# 2. 조종기


## 2.1 조종기 화면 구성

E-DRONE의 조종기는 크게 ***조종***과 ***설정*** 두 화면으로 구성되어 있습니다.

<div align="center">
    <img src="./images/display_control.jpg" alt="control"><br>
    〈조종 화면〉
</div>

조종 화면에서는 드론 조종, 트림 설정, 상태 확인 등을 할 수 있습니다.

<br>

<div align="center">
    <img src="./images/display_setup.jpg" alt="setup"><br>
    〈설정 화면〉
</div>

설정 화면에서는 드론 설정 변경, 상태 확인 등을 할 수 있습니다.

<br>


## 2.2 조종 화면 세부 구성

<br>

### 2.2.1. 높이-자세-RPM

<table>
    <tr>
        <td>
            <div align="center">
                <a href="./images/drone4controller_1.png" target="_blank"><img src="./images/drone4controller_1.png"></a>
            </div>
        </td>
        <td>
            <div align="center">
                <a href="./images/drone4controller_1_desc.png" target="_blank"><img src="./images/drone4controller_1_desc.png"></a>
            </div>
        </td>
    </tr>
</table>


<br>


### 2.2.2. 높이-방향-RPM-자세-고도-위치

<table>
    <tr>
        <td>
            <div align="center">
                <a href="./images/drone4controller_2.png" target="_blank"><img src="./images/drone4controller_2.png"></a>
            </div>
        </td>
        <td>
            <div align="center">
                <a href="./images/drone4controller_2_desc.png" target="_blank"><img src="./images/drone4controller_2_desc.png"></a>
            </div>
        </td>
    </tr>
</table>


<br>


### 2.2.3. 속도-위치-자세

<table>
    <tr>
        <td>
            <div align="center">
                <a href="./images/drone4controller_3.png" target="_blank"><img src="./images/drone4controller_3.png"></a>
            </div>
        </td>
        <td>
            <div align="center">
                <a href="./images/drone4controller_3_desc.png" target="_blank"><img src="./images/drone4controller_3_desc.png"></a>
            </div>
        </td>
    </tr>
</table>


<br>


### 2.2.4. 자세-높이

<table>
    <tr>
        <td>
            <div align="center">
                <a href="./images/drone4controller_4.png" target="_blank"><img src="./images/drone4controller_4.png"></a>
            </div>
        </td>
        <td>
            <div align="center">
                <a href="./images/drone4controller_4_desc.png" target="_blank"><img src="./images/drone4controller_4_desc.png"></a>
            </div>
        </td>
    </tr>
</table>


<br>


### 2.2.5. 위치-트림

<table>
    <tr>
        <td>
            <div align="center">
                <a href="./images/drone4controller_5.png" target="_blank"><img src="./images/drone4controller_5.png"></a>
            </div>
        </td>
        <td>
            <div align="center">
                <a href="./images/drone4controller_5_desc.png" target="_blank"><img src="./images/drone4controller_5_desc.png"></a>
            </div>
        </td>
    </tr>
</table>


<br>


### 2.2.6. RF 정보 및 상태 

<table>
    <tr>
        <td>
            <div align="center">
                <a href="./images/drone4controller_6.png" target="_blank"><img src="./images/drone4controller_6.png"></a>
            </div>
        </td>
        <td>
            <div align="center">
                <a href="./images/drone4controller_6_desc.png" target="_blank"><img src="./images/drone4controller_6_desc.png"></a>
            </div>
        </td>
    </tr>
</table>


<br>


### 2.2.7. 조이스틱 입력 값 

<table>
    <tr>
        <td>
            <div align="center">
                <a href="./images/drone4controller_7.png" target="_blank"><img src="./images/drone4controller_7.png"></a>
            </div>
        </td>
        <td>
            <div align="center">
                <a href="./images/drone4controller_7_desc.png" target="_blank"><img src="./images/drone4controller_7_desc.png"></a>
            </div>
        </td>
    </tr>
</table>


<br>


### 2.2.8. 버전

<table>
    <tr>
        <td>
            <div align="center">
                <a href="./images/drone4controller_8.png" target="_blank"><img src="./images/drone4controller_8.png"></a>
            </div>
        </td>
        <td>
            <div align="center">
                <a href="./images/drone4controller_8_desc.png" target="_blank"><img src="./images/drone4controller_8_desc.png"></a>
            </div>
        </td>
    </tr>
</table>


<br>


<br>


## 2.3. 버튼 구성 및 기능

<br>

### 2.3.1. 조종 화면

<div align="center">
    <img src="./images/button_control_front.jpg" alt="조종기 전면">
    <p>조종 화면에서 전면 버튼의 기능</p>
</div>
<br>

<div align="center">
    <img src="./images/button_control_top.jpg" alt="조종기 상단">
    <p>조종 화면에서 상단 버튼의 기능</p>
</div>
<br>

<br>

### 2.3.2. 설정 화면

<div align="center">
    <img src="./images/button_setup_front.jpg" alt="조종기 전면">
    <p>설정 화면에서 전면 버튼의 기능</p>
</div>
<br>

<div align="center">
    <img src="./images/button_setup_top.jpg" alt="조종기 상단">
    <p>설정 화면에서 상단 버튼의 기능</p>
</div>
<br>

<br>


<br>


## 2.4. 설정 화면 메뉴 구성

<div align="center">
    <table>
        <tr>
            <td class="setup_even">
                <div align="center">
                    1단계
                </div>
            </td>
            <td class="setup_even">
                <div align="center">
                    2단계
                </div>
            </td>
            <td class="setup_even" colspan="4">
                <div align="center">
                    설명
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_odd" rowspan="7">
                <div align="center">
                    DISPLAY
                </div>
            </td>
            <td class="setup_odd">
                <div align="center">
                    높이-자세-RPM
                </div>
            </td>
            <td class="setup_odd" colspan="4">
                <div align="left">
                    조종 화면에서 보여줄 것인지를 설정(SHOW / HIDE)
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    높이-방향-RPM-자세-고도-위치
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    조종 화면에서 보여줄 것인지를 설정(SHOW / HIDE)
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_odd">
                <div align="center">
                    속도-위치-자세
                </div>
            </td>
            <td class="setup_odd" colspan="4">
                <div align="left">
                    조종 화면에서 보여줄 것인지를 설정(SHOW / HIDE)
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    자세-높이
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    조종 화면에서 보여줄 것인지를 설정(SHOW / HIDE)
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_odd">
                <div align="center">
                    위치-트림
                </div>
            </td>
            <td class="setup_odd" colspan="4">
                <div align="left">
                    조종 화면에서 보여줄 것인지를 설정(SHOW / HIDE)
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    RF 정보 및 상태
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    조종 화면에서 보여줄 것인지를 설정(SHOW / HIDE)
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_odd">
                <div align="center">
                    조이스틱 입력 값
                </div>
            </td>
            <td class="setup_odd" colspan="4">
                <div align="left">
                    조종 화면에서 보여줄 것인지를 설정(SHOW / HIDE)
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_even" rowspan="2">
                <div align="center">
                    LIGHT
                </div>
            </td>
            <td class="setup_even">
                <div align="center">
                    DRONE
                </div>
            </td>
            <td class="setup_even" colspan="4">
                <div align="left">
                    드론 LED 기본 색 설정 변경
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    CONTROLLER
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    조종기 LED 기본 색 설정 변경
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_odd" rowspan="2">
                <div align="center">
                    CONTROL
                </div>
            </td>
            <td class="setup_odd">
                <div align="center">
                    ATTITUDE
                </div>
            </td>
            <td class="setup_odd" colspan="4">
                <div align="left">
                    자세 제어
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    POSITION
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    위치 제어
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_even" rowspan="5">
                <div align="center">
                    MODE
                </div>
            </td>
            <td class="setup_even">
                <div align="center">
                    MODE
                </div>
            </td>
            <td class="joystick_left">
                <div align="center">
                    Left ↕
                </div>
            </td>
            <td class="joystick_left">
                <div align="center">
                    Left ↔
                </div>
            </td>
            <td class="joystick_right">
                <div align="center">
                    Right ↕
                </div>
            </td>
            <td class="joystick_right">
                <div align="center">
                    Right ↔
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    MODE 1
                </div>
            </td>
            <td class="elevator">
                <div align="center">
                    앞뒤<br>(Elevator)
                </div>
            </td>
            <td class="rudder">
                <div align="center">
                    좌우 회전<br>(Rudder)
                </div>
            </td>
            <td class="throttle">
                <div align="center">
                    위아래<br>(Throttle)
                </div>
            </td>
            <td class="aileron">
                <div align="center">
                    좌우<br>(Aileron)
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_even">
                <div align="center">
                    MODE 2
                </div>
            </td>
            <td class="throttle">
                <div align="center">
                    위아래<br>(Throttle)
                </div>
            </td>
            <td class="rudder">
                <div align="center">
                    좌우 회전<br>(Rudder)
                </div>
            </td>
            <td class="elevator">
                <div align="center">
                    앞뒤<br>(Elevator)
                </div>
            </td>
            <td class="aileron">
                <div align="center">
                    좌우<br>(Aileron)
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    MODE 3
                </div>
            </td>
            <td class="elevator">
                <div align="center">
                    앞뒤<br>(Elevator)
                </div>
            </td>
            <td class="aileron">
                <div align="center">
                    좌우<br>(Aileron)
                </div>
            </td>
            <td class="throttle">
                <div align="center">
                    위아래<br>(Throttle)
                </div>
            </td>
            <td class="rudder">
                <div align="center">
                    좌우 회전<br>(Rudder)
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_even">
                <div align="center">
                    MODE 4
                </div>
            </td>
            <td class="throttle">
                <div align="center">
                    위아래<br>(Throttle)
                </div>
            </td>
            <td class="aileron">
                <div align="center">
                    좌우<br>(Aileron)
                </div>
            </td>
            <td class="elevator">
                <div align="center">
                    앞뒤<br>(Elevator)
                </div>
            </td>
            <td class="rudder">
                <div align="center">
                    좌우 회전<br>(Rudder)
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_odd" rowspan="2">
                <div align="center">
                    HEADLESS
                </div>
            </td>
            <td class="setup_odd">
                <div align="center">
                    HEADLESS
                </div>
            </td>
            <td class="setup_odd" colspan="4">
                <div align="left">
                    헤드리스(방향 고정)
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    NORMAL
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    일반(드론의 현재 방향 기준)
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_even" rowspan="3">
                <div align="center">
                    SPEED
                </div>
            </td>
            <td class="setup_even">
                <div align="center">
                    S1
                </div>
            </td>
            <td class="setup_even" colspan="4">
                <div align="left">
                    속도 1단계(느림)
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    S2
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    속도 2단계
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_even">
                <div align="center">
                    S3
                </div>
            </td>
            <td class="setup_even" colspan="4">
                <div align="left">
                    속도 3단계(빠름)
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_odd" rowspan="2">
                <div align="center">
                    FHSS
                </div>
            </td>
            <td class="setup_odd">
                <div align="center">
                    ON
                </div>
            </td>
            <td class="setup_odd" colspan="4">
                <div align="left">
                    채널 호핑
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    OFF
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    고정 채널
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_even" rowspan="3">
                <div align="center">
                    FUNCTION
                </div>
            </td>
            <td class="setup_even">
                <div align="center">
                    SENSOR RESET
                </div>
            </td>
            <td class="setup_even" colspan="4">
                <div align="left">
                    드론의 자이로 바이어스 리셋
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    PAIRING
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    페어링
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_even">
                <div align="center">
                    SET DEFAULT
                </div>
            </td>
            <td class="setup_even" colspan="4">
                <div align="left">
                    설정값 초기화(드론이 연결된 경우 드론 설정도 초기화 됨)
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_odd" rowspan="10">
                <div align="center">
                    INFORMATION
                </div>
            </td>
            <td class="setup_odd">
                <div align="center">
                    COUNT
                </div>
            </td>
            <td class="setup_odd" colspan="4">
                <div align="left">
                    비행 시간 및 이벤트 카운트 값 표시
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    BIAS
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    가속도, 자이로 바이어스 값 표시
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_odd">
                <div align="center">
                    TRIM
                </div>
            </td>
            <td class="setup_odd" colspan="4">
                <div align="left">
                    Trim 값 표시
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    MOTION
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    IMU 센서 데이터를 연산하여 변환한 결과 표시
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_odd">
                <div align="center">
                    ALTITUDE
                </div>
            </td>
            <td class="setup_odd" colspan="4">
                <div align="left">
                    높이-고도와 관련된 센서 데이터 표시
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    POSITION
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    위치 데이터 표시
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_odd">
                <div align="center">
                    RF
                </div>
            </td>
            <td class="setup_odd" colspan="4">
                <div align="left">
                    RF 설정 데이터 표시
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    ADDRESS
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    드론과 조종기의 고유번호 표시
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_odd">
                <div align="center">
                    BOOT
                </div>
            </td>
            <td class="setup_odd" colspan="4">
                <div align="left">
                    조종기의 부트 정보 및 장치 등록 여부 표시
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    CRC32
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    드론과 조종기의 부트로더 및 앱 영역 CRC32 값 표시
                </div>
            </td>
        </tr>
    </table>
</div>

<br>


<br>


## 2.5. MODE

### 2.5.1. MODE 1

<div align="center">
    <img src="./images/mode1.jpg" alt="MODE 1" width="800">
    <p>MODE 1</p>
</div>
<br>

<br>

### 2.5.2. MODE 2

<div align="center">
    <img src="./images/mode2.jpg" alt="MODE 2" width="800">
    <p>MODE 2</p>
</div>
<br>

<br>



여기까지 E-DRONE 조종기와 드론에 대한 간략한 설명이었습니다.

