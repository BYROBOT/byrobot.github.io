**[*e_drone* for python](index.md)** / **Drone**

Modified : 2021.12.29

---

<h3>drone 모듈을 소개합니다.</h3>

---


<br>


# Drone 클래스


<br>


### Drone 클래스 생성자

Drone 클래스의 생성자는 아래와 같습니다.

```py
def __init__(self, flag_check_background=True, flag_show_error_message=False, flag_show_log_message=False, flag_show_transfer_data=False, flag_show_receive_data=False):
```


|          이름           |                  설명                  |
| :---------------------- | :------------------------------------- |
| flag_check_background   | 수신 받은 데이터를 백그라운드에서 확인 |
| flag_show_error_message | 에러 메세지 표시                       |
| flag_show_log_message   | 로그 메세지 표시                       |
| flag_show_transfer_data | 송신 데이터 배열 표시                  |
| flag_show_receive_data  | 수신 데이터 배열 표시                  |


Drone 클래스 생성자 호출 시 인자를 입력하지 않으면 **flag_check_background**는 ***True***가 되며, 나머지는 모두 False가 됩니다.

**flag_check_background**가 ***True***인 경우에는 데이터를 받을 때마다 내부에서 **check()** 함수를 호출합니다. ***False***인 경우에는 사용자가 직접 **check()** 함수를 호출하여 수신 받은 데이터를 처리해야 합니다.


<br>
<br>


### Drone 클래스의 public 함수 구성

Drone 클래스의 외부에서 접근할 수 있는 함수 목록입니다.

|                    이름                    |                                설명                                |
| :----------------------------------------- | :----------------------------------------------------------------- |
| is_open()                                  | 시리얼 포트가 열린 경우 True 반환                                  |
| open(port_name)                            | 시리얼 포트 열기. 포트가 열린 경우 True 반환                       |
| close()                                    | 시리얼 포트 닫기                                                   |
| make_transfer_data_array(header, data)     | 전송할 데이터 바이트 배열 생성                                     |
| transfer(header, data)                     | 데이터 전송(내부에서 make_transfer_data_array 함수를 실행함)       |
| check()                                    | 수신 받은 데이터 확인. 데이터를 받은 경우 DataType을 반환          |
| check_detail()                             | 수신 받은 데이터 확인. Header와 Data를 튜플로 반환                 |
| set_event_handler(dataType, event_handler) | 특정 타입의 데이터를 수신했을 때 호출할 사용자 지정 함수 등록      |
| get_header(dataType)                       | 지정한 타입의 데이터와 함께 받은 헤더 반환                         |
| get_data(dataType)                         | 지정한 타입의 데이터 반환(데이터가 없으면 None 반환)               |
| get_count(dataType)                        | 지정한 타입의 데이터를 받은 횟수를 반환(데이터가 없으면 None 반환) |
| convert_byte_array_to_string(data_array)   | 바이트 배열을 Hex 문자열로 변경하여 반환                           |


<br>
<br>


### Drone 클래스 데이터 수신 처리부

Drone 클래스의 데이터 수신 처리부는 아래와 같이 구성되어 있습니다.

|     이름     |                                                                                                     설명                                                                                                      |
| :----------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| _receiving() | 데이터 수신 Thread, 수신 받은 데이터를 버퍼에 저장                                                                                                                                                            |
| check()      | 버퍼에 저장된 데이터를 한 바이트씩 읽어 receiver에 전달. 하나의 데이터 블럭을 받은 경우 *_handler()*를 호출하여 받은 데이터를 파싱해서 저장하고 dataType을 반환. 받은 데이터가 없으면 **DataType.None_** 반환 |
| _handler()   | 헤더를 내부에 저장. 데이터는 파싱하여 내부에 저장. 이벤트 처리 함수가 등록된 경우 해당 함수 호출                                                                                                              |


<br>
<br>


# 함수 목록


<br>


## 일반

|             이름              |    설명     |
| :---------------------------- | :---------- |
| [send_ping](#send_ping)       | 핑 전송     |
| [send_request](#send_request) | 데이터 요청 |
| [send_pairing](#send_pairing) | 페어링 설정 |


<br>


## 조종

|                            이름                             |                 설명                 |
| :---------------------------------------------------------- | :----------------------------------- |
| [send_takeoff](#send_takeoff)                               | 이륙                                 |
| [send_landing](#send_landing)                               | 착륙                                 |
| [send_stop](#send_stop)                                     | 정지                                 |
| [send_control](#send_control)                               | 비행 조종                            |
| [send_control_time](#send_control_time)                     | 지정한 시간 동안 비행 조종 명령 전송 |
| [send_control_position_short](#send_control_position_short) | 이동(RF)                             |
| [send_control_position](#send_control_position)             | 이동(UART, USB)                      |


<br>


## 설정

|                                이름                                 |              설명              |
| :------------------------------------------------------------------ | :----------------------------- |
| [send_command](#send_command)                                       | 명령 전송                      |
| [send_command_light_event](#send_command_light_event)               | 명령 전송 + LED 이벤트         |
| [send_command_light_event_color](#send_command_light_event_color)   | 명령 전송 + LED 이벤트(RGB)    |
| [send_command_light_event_colors](#send_command_light_event_colors) | 명령 전송 + LED 이벤트(팔레트) |
| [send_mode_control_flight](#send_mode_control_flight)               | 비행 제어 모드 변경            |
| [send_headless](#send_headless)                                     | 헤드리스 설정                  |
| [send_trim](#send_trim)                                             | Trim 값을 지정하여 변경        |
| [send_weight](#send_weight)                                         | Weight 설정                    |
| [send_lost_connection](#send_lost_connection)                       | 연결이 끊긴 후 반응 시간 설정  |
| [send_flight_event](#send_flight_event)                             | 비행 이벤트 실행               |
| [send_clear_bias](#send_clear_bias)                                 | 바이어스 초기화                |
| [send_clear_trim](#send_clear_trim)                                 | Trim 초기화                    |
| [send_set_default](#send_set_default)                               | 장치 설정 초기화               |

<br>


## 모터

|                  이름                   |        설명         |
| :-------------------------------------- | :------------------ |
| [send_motor](#send_motor)               | 모터 동작 제어      |
| [send_motor_single](#send_motor_single) | 단일 모터 동작 제어 |

<br>


## LED

|                         이름                          |         설명         |
| :---------------------------------------------------- | :------------------- |
| [send_light_manual](#send_light_manual)               | 수동 제어            |
| [send_light_mode_color](#send_light_mode_color)       | 모드 설정 (RGB)      |
| [send_light_mode_colors](#send_light_mode_colors)     | 모드 설정 (팔레트)   |
| [send_light_event_color](#send_light_event_color)     | 이벤트 설정 (RGB)    |
| [send_light_event_colors](#send_light_event_colors)   | 이벤트 설정 (팔레트) |
| [send_light_default_color](#send_light_default_color) | 기본 모드 설정 (RGB) |

<br>


## 조종기 LCD 디스플레이

|                               이름                                |          설명          |
| :---------------------------------------------------------------- | :--------------------- |
| [send_display_clear_all](#send_display_clear_all)                 | 전체 지우기            |
| [send_display_clear](#send_display_clear)                         | 일부분 지우기          |
| [send_display_invert](#send_display_invert)                       | 일부분 반전            |
| [send_display_draw_point](#send_display_draw_point)               | 점 찍기                |
| [send_display_draw_line](#send_display_draw_line)                 | 선 그리기              |
| [send_display_draw_rect](#send_display_draw_rect)                 | 사각형 그리기          |
| [send_display_draw_circle](#send_display_draw_circle)             | 원 그리기              |
| [send_display_draw_string](#send_display_draw_string)             | 문자열 쓰기            |
| [send_display_draw_string_align](#send_display_draw_string_align) | 문자열을 정렬하여 쓰기 |

<br>


## 조종기 버저 

|                          이름                           |               설명               |
| :------------------------------------------------------ | :------------------------------- |
| [send_buzzer](#send_buzzer)                             | 소리 내기                        |
| [send_buzzer_mute](#send_buzzer_mute)                   | 묵음                             |
| [send_buzzer_mute_reserve](#send_buzzer_mute_reserve)   | 묵음 예약                        |
| [send_buzzer_scale](#send_buzzer_scale)                 | 음계를 사용하여 소리 내기        |
| [send_buzzer_scale_reserve](#send_buzzer_scale_reserve) | 음계를 사용하여 소리 내기 예약   |
| [send_buzzer_hz](#send_buzzer_hz)                       | 주파수를 사용하여 소리 내기      |
| [send_buzzer_hz_reserve](#send_buzzer_hz_reserve)       | 주파수를 사용하여 소리 내기 예약 |

<br>


## 조종기 진동

|                      이름                       |   설명    |
| :---------------------------------------------- | :-------- |
| [send_vibrator](#send_vibrator)                 | 진동 설정 |
| [send_vibrator_reserve](#send_vibrator_reserve) | 진동 예약 |


<br>
<br>


# 함수 정의


<br>
<br>


## <a name="send_ping">send_ping</a>

핑 전송

다른 장치와의 연결 상태를 확인할 때 사용합니다. 상대 장치는 Ping에 대한 응답으로 Ack를 전송합니다.

```py
def send_ping(self, device_type):
```

|  변수 이름  |            형식 또는 범위             |       설명       |
| :---------: | :-----------------------------------: | :--------------- |
| device_type | [DeviceType](03_system.md#DeviceType) | 전송할 대상 장치 |

- e.g. [Ping 테스트](examples_01_ping.md#Ping)


<br>
<br>


## <a name="send_request">send_request</a>

데이터 요청

지정한 장치에 데이터를 요청할 때 사용합니다.

```py
def send_request(self, device_type, data_type):
```

|  변수 이름  |            형식 또는 범위             |       설명       |
| :---------: | :-----------------------------------: | :--------------- |
| device_type | [DeviceType](03_system.md#DeviceType) | 전송할 대상 장치 |
|  data_type  |         [DataType](#DataType)         | 데이터의 타입    |

- e.g. [조종기의 펌웨어 정보 요청](examples_02_information.md#Information)


<br>
<br>


## <a name="send_pairing">send_pairing</a>

페어링 설정

지정한 장치의 페어링 설정을 변경할 때 사용합니다.

```py
def send_pairing(self, device_type, address_0, address_1, address_2, scramble, channel_0, channel_1, channel_2, channel_3):
```

|  변수 이름  |            형식 또는 범위             |       설명       |
| :---------: | :-----------------------------------: | :--------------- |
| device_type | [DeviceType](03_system.md#DeviceType) | 전송할 대상 장치 |
|  address_0  |               0 ~ 65535               | 장치의 주소 0    |
|  address_1  |               0 ~ 65535               | 장치의 주소 1    |
|  address_2  |               0 ~ 65535               | 장치의 주소 2    |
|  scramble   |                0 ~ 127                | 스크램블         |
|  channel_0  |                0 ~ 81                 | 채널 0           |
|  channel_1  |                0 ~ 81                 | 채널 1           |
|  channel_2  |                0 ~ 81                 | 채널 2           |
|  channel_3  |                0 ~ 81                 | 채널 3           |

- e.g. [페어링 변경 후 변경된 정보 확인](examples_03_pairing.md#Pairing)


<br>
<br>


## <a name="send_takeoff">send_takeoff</a>

이륙

이륙을 할 때 사용합니다.

만약 이륙 준비 상태가 아니라면 자동으로 이륙 준비 상태를 거치게 됩니다.

```py
def send_takeoff(self):
```

- e.g. [이륙, 호버링, 착륙 테스트](examples_04_control.md#ControlTimeAndLanding)


<br>
<br>


## <a name="send_landing">send_landing</a>

착륙

비행 모드로 동작 시 착륙을 할 때 사용합니다.

```py
def send_landing(self):
```

- e.g. [이륙, 호버링, 착륙 테스트](examples_04_control.md#ControlTimeAndLanding)



<br>
<br>


## <a name="send_stop">send_stop</a>

정지

드론 동작 모드에 관계없이 강제로 정지할 때 사용합니다.

```py
def send_stop(self):
```

- e.g. [이륙, 조종, 정지 테스트](examples_04_control.md#ControlTime)


<br>
<br>


## <a name="send_control">send_control</a>

비행 조종

비행 및 주행에 모두 사용할 수 있습니다.

```py
def send_control(self, roll, pitch, yaw, throttle):
```

| 변수 이름 | 형식 또는 범위 |   설명   |
| :-------: | :------------: | :------- |
|   roll    |   -100 ~ 100   | Roll     |
|   pitch   |   -100 ~ 100   | Pitch    |
|    yaw    |   -100 ~ 100   | Yaw      |
| throttle  |   -100 ~ 100   | Throttle |


<br>
<br>


## <a name="send_control_time">send_control_time</a>

비행 조종

비행 및 주행에 모두 사용할 수 있습니다.
timeMs에 지정한 ms동안 연속으로 조종 명령을 전송합니다.

```py
def send_control_time(self, roll, pitch, yaw, throttle, time_ms):
```

| 변수 이름 | 형식 또는 범위 |     설명      |
| :-------: | :------------: | :------------ |
|   roll    |   -100 ~ 100   | Roll          |
|   pitch   |   -100 ~ 100   | Pitch         |
|    yaw    |   -100 ~ 100   | Yaw           |
| throttle  |   -100 ~ 100   | Throttle      |
|  time_ms  | 0 ~ 1,000,000  | 동작 시간(ms) |

- e.g. [이륙, 호버링, 착륙 테스트](examples_04_control.md#ControlTimeAndLanding)


<br>
<br>


## <a name="send_control_position_short">send_control_position_short</a>

드론 이동 명령

모든 변수에 2byte 정수를 사용하는 대신 position과 velocity의 값에 x10을 적용.

```py
def send_control_position_short(self, position_x, position_y, position_z, velocity, heading, rotational_velocity):
```

|      변수 이름      | 형식  |           범위           |    단위    |         설명         |
| :-----------------: | :---: | :----------------------: | :--------- | :------------------- |
|     position_x      | Int16 | -100 ~ 100(-10.0 ~ 10.0) | meter x 10 | 앞(+), 뒤(-)         |
|     position_y      | Int16 | -100 ~ 100(-10.0 ~ 10.0) | meter x 10 | 좌(+), 우(-)         |
|     position_z      | Int16 | -100 ~ 100(-10.0 ~ 10.0) | meter x 10 | 위(+), 아래(-)       |
|      velocity       | Int16 |    5 ~ 20(0.5 ~ 2.0)     | m/s x 10   | 위치 이동 속도       |
|       heading       | Int16 |        -360 ~ 360        | degree     | 좌회전(+), 우회전(-) |
| rotational_velocity | Int16 |         10 ~ 360         | degree/s   | 좌우 회전 속도       |


<br>
<br>


## <a name="send_control_position">send_control_position</a>

드론 이동 명령

position과 velocity는 실수 값, heading과 rotationalVelocity에는 정수 값 사용

```py
def send_control_position(self, position_x, position_y, position_z, velocity, heading, rotational_velocity):
```

|      변수 이름      | 형식  |     범위     |   단위   |         설명         |
| :-----------------: | :---: | :----------: | :------- | :------------------- |
|     position_x      | float | -10.0 ~ 10.0 | meter    | 앞(+), 뒤(-)         |
|     position_y      | float | -10.0 ~ 10.0 | meter    | 좌(+), 우(-)         |
|     position_z      | float | -10.0 ~ 10.0 | meter    | 위(+), 아래(-)       |
|      velocity       | float |  0.5 ~ 2.0   | m/s      | 위치 이동 속도       |
|       heading       | Int16 |  -360 ~ 360  | degree   | 좌회전(+), 우회전(-) |
| rotational_velocity | Int16 |   10 ~ 360   | degree/s | 좌우 회전 속도       |

- e.g. [이륙, 호버링, 전진, 착륙 테스트](examples_04_control.md#ControlPosition)
- e.g. [이륙, 호버링, 1미터 전진, 1미터 오른쪽 이동, 리턴 홈 테스트](examples_04_control.md#ControlReturnHome)


<br>
<br>


## <a name="send_command">send_command</a>

명령 전송

드론에 명령을 전달할 때 사용합니다.

option에는 각 형식의 value 값 또는 숫자 값을 넣으셔야 합니다.

```py
def send_command(self, command_type, option = 0):
```

|  변수 이름   |                   형식 또는 범위                    |   설명    |
| :----------: | :-------------------------------------------------: | :-------- |
| command_type |      [CommandType](04_protocol.md#CommandType)      | 명령 타입 |
|    option    | [ModeControlFlight](03_system.md#ModeControlFlight) | 옵션      |
|              |       [FlightEvent](03_system.md#FlightEvent)       |           |
|              |          [Headless](03_system.md#Headless)          |           |
|              |              [Trim](03_system.md#Trim)              |           |
|              |                        UInt8                        |           |

- e.g. [Motion 센서 보정](examples_13_error.md#Error_MotionCalibrating)


<br>
<br>


## <a name="send_command_light_event">send_command_light_event</a>

명령 + LED 이벤트

드론에 명령을 전달할 때 사용합니다.

option에는 각 형식의 value 값 또는 숫자 값을 넣으셔야 합니다.

```py
def send_command_light_event(self, command_type, option, light_event, interval, repeat):
```

|  변수 이름   |                   형식 또는 범위                    |             설명              |
| :----------: | :-------------------------------------------------: | :---------------------------- |
| command_type |      [CommandType](04_protocol.md#CommandType)      | 명령 타입                     |
|    option    | [ModeControlFlight](03_system.md#ModeControlFlight) | 옵션                          |
|              |       [FlightEvent](03_system.md#FlightEvent)       |                               |
|              |          [Headless](03_system.md#Headless)          |                               |
|              |              [Trim](03_system.md#Trim)              |                               |
|              |                        UInt8                        |                               |
| light_event  |                        UInt8                        | LED 동작 모드                 |
|   interval   |                      0 ~ 65535                      | 내부 밝기 제어 함수 호출 주기 |
|    repeat    |                       0 ~ 255                       | 반복 횟수                     |


<br>
<br>


## <a name="send_command_light_event_color">send_command_light_event_color</a>

명령 + LED 이벤트(RGB)

드론에 명령을 전달할 때 사용합니다.

option에는 각 형식의 value 값 또는 숫자 값을 넣으셔야 합니다.

```py
def send_command_light_event_color(self, command_type, option, light_event, interval, repeat, r, g, b):
```

|  변수 이름   |                   형식 또는 범위                    |             설명              |
| :----------: | :-------------------------------------------------: | :---------------------------- |
| command_type |      [CommandType](04_protocol.md#CommandType)      | 명령 타입                     |
|    option    | [ModeControlFlight](03_system.md#ModeControlFlight) | 옵션                          |
|              |       [FlightEvent](03_system.md#FlightEvent)       |                               |
|              |          [Headless](03_system.md#Headless)          |                               |
|              |              [Trim](03_system.md#Trim)              |                               |
|              |                        UInt8                        |                               |
| light_event  |                        UInt8                        | LED 동작 모드                 |
|   interval   |                      0 ~ 65535                      | 내부 밝기 제어 함수 호출 주기 |
|    repeat    |                       0 ~ 255                       | 반복 횟수                     |
|      r       |                       0 ~ 255                       | Red                           |
|      g       |                       0 ~ 255                       | Green                         |
|      b       |                       0 ~ 255                       | Blue                          |


<br>
<br>


## <a name="send_command_light_event_colors">send_command_light_event_colors</a>

명령 + LED 이벤트(Palette)

드론에 명령을 전달할 때 사용합니다.

option에는 각 형식의 value 값 또는 숫자 값을 넣으셔야 합니다.

```py
def send_command_light_event_colors(self, command_type, option, light_event, interval, repeat, colors):
```

|  변수 이름   |                   형식 또는 범위                    |             설명              |
| :----------: | :-------------------------------------------------: | :---------------------------- |
| command_type |      [CommandType](04_protocol.md#CommandType)      | 명령 타입                     |
|    option    | [ModeControlFlight](03_system.md#ModeControlFlight) | 옵션                          |
|              |       [FlightEvent](03_system.md#FlightEvent)       |                               |
|              |          [Headless](03_system.md#Headless)          |                               |
|              |              [Trim](03_system.md#Trim)              |                               |
|              |                        UInt8                        |                               |
| light_event  |                        UInt8                        | LED 동작 모드                 |
|   interval   |                      0 ~ 65535                      | 내부 밝기 제어 함수 호출 주기 |
|    repeat    |                       0 ~ 255                       | 반복 횟수                     |
|    colors    |           [Colors](04_protocol.md#Colors)           | 색상 팔레트 인덱스            |


<br>
<br>


## <a name="send_mode_control_flight">send_mode_control_flight</a>

비행 제어 모드 설정

드론 비행 제어 모드를 변경합니다.

```py
def send_mode_control_flight(self, mode_control_flight):
```

|      변수 이름      |                   형식 또는 범위                    |      설명      |
| :-----------------: | :-------------------------------------------------: | :------------- |
| mode_control_flight | [ModeControlFlight](03_system.md#ModeControlFlight) | 비행 제어 모드 |

- e.g. [비행 제어 모드를 변경 후 확인](examples_07_setup.md#ModeControlFlight)


<br>
<br>


## <a name="send_headless">send_headless</a>

Headless 설정

```py
def send_headless(self, headless):
```

| 변수 이름 |          형식 또는 범위           |     설명      |
| :-------: | :-------------------------------: | :------------ |
| headless  | [Headless](03_system.md#Headless) | Headless 설정 |

- e.g. [드론 Headless 설정 변경 후 확인](examples_07_setup.md#Headless)


<br>
<br>


## <a name="send_trim">send_trim</a>

비행 Trim 설정

```py
def send_trim(self, roll, pitch, yaw, throttle):
```

| 변수 이름 | 형식 또는 범위 |   설명   |
| :-------: | :------------: | :------- |
|   roll    |   -200 ~ 200   | Roll     |
|   pitch   |   -200 ~ 200   | Pitch    |
|    yaw    |   -200 ~ 200   | Yaw      |
| throttle  |   -200 ~ 200   | Throttle |

- e.g. [드론 Trim 설정 변경 후 확인](examples_07_setup.md#Trim)


<br>
<br>


## <a name="send_weight">send_weight</a>

무게

```py
def send_weight(self, weight):
```

| 변수 이름 |        형식 또는 범위         | 설명 |
| :-------: | :---------------------------: | :--- |
|  weight   | [Weight](03_system.md#Weight) | 무게 |


<br>
<br>


## <a name="send_lost_connection">send_lost_connection</a>

통신 연결이 끊긴 후 반응 시간 설정

마지막으로 비행 이벤트 또는 조종 명령을 보냈던 장치와의 연결이 끊어진 후에 지정한 시간이 경과하면 해당 명령을 실행. 시간을 0으로 설정한 경우 해당 명령은 실행하지 않음. 시간 단위는 ms

```py
def send_lost_connection(self, time_neutral, time_landing, time_stop):
```

|  변수 이름   |  형식 또는 범위   |   설명    |
| :----------: | :---------------: | :-------- |
| time_neutral |    0 ~ 65,535     | 조종 중립 |
| time_landing |    0 ~ 65,535     | 착륙      |
|  time_stop   | 0 ~ 4,294,967,295 | 정지      |


<br>
<br>


## <a name="send_flight_event">send_flight_event</a>

비행 이벤트 실행

```py
def send_flight_event(self, flight_event):
```

|  변수 이름   |             형식 또는 범위              |    설명     |
| :----------: | :-------------------------------------: | :---------- |
| flight_event | [FlightEvent](03_system.md#FlightEvent) | 비행 이벤트 |


<br>
<br>


## <a name="send_clear_bias">send_clear_bias</a>

Accel, Gyro Bias 초기화

```py
def send_clear_bias(self):
```


<br>
<br>


## <a name="send_clear_trim">send_clear_trim</a>

비행, 주행 Trim 초기화

```py
def send_clear_trim(self):
```


<br>
<br>


## <a name="send_set_default">send_set_default</a>

장치 설정 초기화

지정한 장치의 설정을 초기화 함

```py
def send_set_default(self, deviceType):
```


<br>
<br>


## <a name="send_motor">send_motor</a>

4개의 모터를 미리 지정된 방향으로 회전

```py
def send_motor(self, motor_0, motor_1, motor_2, motor_3):
```

| 변수 이름 | 형식 또는 범위 |           설명           |
| :-------: | :------------: | :----------------------- |
|  motor_0  |    0 ~ 4095    | 왼쪽 앞 모터 속도 지정   |
|  motor_1  |    0 ~ 4095    | 오른쪽 앞 모터 속도 지정 |
|  motor_2  |    0 ~ 4095    | 오른쪽 뒤 모터 속도 지정 |
|  motor_3  |    0 ~ 4095    | 왼쪽 뒤 모터 속도 지정   |

- e.g. [모터 동작 테스트](examples_06_motor.md#Motor)


<br>
<br>


## <a name="send_motor_single">send_motor_single</a>

1개의 모터를 회전 방향을 지정하여 동작

target에 들어가는 값은 0~3입니다. 모터의 순서는 왼쪽 앞 모터부터 시계방향입니다.

```py
def send_motor_single(self, target, value):
```

| 변수 이름 | 형식 또는 범위 |        설명        |
| :-------: | :------------: | :----------------- |
|  target   |     0 ~ 3      | 제어할 모터의 번호 |
|   value   |    0 ~ 4095    | 모터의 속도        |

- e.g. [MotorSingle 동작 테스트](examples_06_motor.md#MotorSingle)


<br>
<br>


## <a name="send_motor_single_rotation">send_motor_single_rotation</a>

1개의 모터를 회전 방향을 지정하여 동작

target에 들어가는 값은 0~3입니다. 모터의 순서는 왼쪽 앞 모터부터 시계방향입니다.

```py
def send_motor_single_rotation(self, target, rotation, value):
```

| 변수 이름 |          형식 또는 범위           |        설명        |
| :-------: | :-------------------------------: | :----------------- |
|  target   |               0 ~ 3               | 제어할 모터의 번호 |
| rotation  | [Rotation](03_system.md#Rotation) | 모터의 회전 방향   |
|   value   |             0 ~ 4095              | 모터의 속도        |


<br>
<br>


## <a name="send_light_manual">send_light_manual</a>

LED 수동 제어

flags에는 [LightFlagsDrone](#LightFlagsDrone), [LightFlagsController](#LightFlagsController)의 value 값을 사용하거나 직접 플래그에 해당하는 비트를 선택하시면 됩니다.

brightness는 값은 0일 때 꺼지며 값이 커질수록 밝아집니다.

```py
def send_light_manual(self, device_type, flags, brightness):
```

|  변수 이름  |            형식 또는 범위             |       설명        |
| :---------: | :-----------------------------------: | :---------------- |
| device_type | [DeviceType](03_system.md#DeviceType) | LED를 제어할 장치 |
|    flags    |        0b00000000 ~ 0b11111111        | LED 플래그        |
| brightness  |                0 ~ 255                | 밝기              |

- e.g. [send_light_manual() 함수를 사용하여 조종기 LED 제어하기](examples_10_light.md#LightManual)


<br>
<br>


## <a name="send_light_mode_color">send_light_mode_color</a>

LED 모드 설정(RGB)

light_mode 변수에는 [LightModeDrone](#LightModeDrone), [LightModeController](#LightModeController)의 value 값을 사용합니다.

```py
def send_light_mode_color(self, light_mode, interval, r, g, b):
```

| 변수 이름  | 형식 또는 범위 |             설명              |
| :--------: | :------------: | :---------------------------- |
| light_mode |     UInt8      | LED 동작 모드                 |
|  interval  |   0 ~ 65535    | 내부 밝기 제어 함수 호출 주기 |
|     r      |    0 ~ 255     | Red                           |
|     g      |    0 ~ 255     | Green                         |
|     b      |    0 ~ 255     | Blue                          |

- e.g. [sendLightMode, sendLightEvent 함수를 사용하여 조종기 LED 제어하기](examples_10_light.md#LightMode)


<br>
<br>



## <a name="send_light_mode_colors">send_light_mode_colors</a>

LED 모드 설정(Palette)

light_mode 변수에는 [LightModeDrone](#LightModeDrone), [LightModeController](#LightModeController)의 value 값을 사용합니다.

```py
def send_light_mode_colors(self, light_mode, interval, colors):
```

| 변수 이름  |         형식 또는 범위          |             설명              |
| :--------: | :-----------------------------: | :---------------------------- |
| light_mode |              UInt8              | LED 동작 모드                 |
|  interval  |            0 ~ 65535            | 내부 밝기 제어 함수 호출 주기 |
|   colors   | [Colors](04_protocol.md#Colors) | 색상 팔레트 인덱스            |

- e.g. [sendLightMode, sendLightEvent 함수를 사용하여 조종기 LED 제어하기](examples_10_light.md#LightMode)


<br>
<br>


## <a name="send_light_event_color">send_light_event_color</a>

LED 이벤트 설정(RGB)

light_event 변수에는 [LightModeDrone](#LightModeDrone), [LightModeController](#LightModeController)의 value 값을 사용합니다.

```py
def send_light_event_color(self, light_event, interval, repeat, r, g, b):
```

|  변수 이름  | 형식 또는 범위 |             설명              |
| :---------: | :------------: | :---------------------------- |
| light_event |     UInt8      | LED 동작 모드                 |
|  interval   |   0 ~ 65535    | 내부 밝기 제어 함수 호출 주기 |
|   repeat    |    0 ~ 255     | 반복 횟수                     |
|      r      |    0 ~ 255     | Red                           |
|      g      |    0 ~ 255     | Green                         |
|      b      |    0 ~ 255     | Blue                          |

- e.g. [sendLightMode, sendLightEvent 함수를 사용하여 조종기 LED 제어하기](examples_10_light.md#LightMode)


<br>
<br>


## <a name="send_light_event_colors">send_light_event_colors</a>

LED 이벤트 설정(Palette)

light_event 변수에는 [LightModeDrone](#LightModeDrone), [LightModeController](#LightModeController)의 value 값을 사용합니다.

```py
def send_light_event_colors(self, light_event, interval, repeat, colors):
```

|  변수 이름  |         형식 또는 범위          |             설명              |
| :---------: | :-----------------------------: | :---------------------------- |
| light_event |              UInt8              | LED 동작 모드                 |
|  interval   |            0 ~ 65535            | 내부 밝기 제어 함수 호출 주기 |
|   repeat    |             0 ~ 255             | 반복 횟수                     |
|   colors    | [Colors](04_protocol.md#Colors) | 색상 팔레트 인덱스            |

- e.g. [sendLightMode, sendLightEvent 함수를 사용하여 조종기 LED 제어하기](examples_10_light.md#LightMode)


<br>
<br>


## <a name="send_light_default_color">send_light_default_color</a>

LED 기본 모드 설정(RGB)

light_mode 변수에는 [LightModeDrone](#LightModeDrone), [LightModeController](#LightModeController)의 value 값을 사용합니다.

```py
def send_light_default_color(self, light_mode, interval, r, g, b):
```

| 변수 이름  | 형식 또는 범위 |             설명              |
| :--------: | :------------: | :---------------------------- |
| light_mode |     UInt8      | LED 동작 모드                 |
|  interval  |   0 ~ 65535    | 내부 밝기 제어 함수 호출 주기 |
|     r      |    0 ~ 255     | Red                           |
|     g      |    0 ~ 255     | Green                         |
|     b      |    0 ~ 255     | Blue                          |

- e.g. [드론의 LED를 랜덤한 색으로 점점 밝아졌다 어두워지게 하는 명령을 10회 실행 (LightModeColors / send_light_default_color 함수 사용)](examples_10_light.md#Class_LightDefaultModeColor)


<br>
<br>


## <a name="send_display_clear_all">send_display_clear_all</a>

화면 전체 지우기

```py
def send_display_clear_all(self, pixel = DisplayPixel.BLACK):
```

| 변수 이름 |                형식 또는 범위                |   설명    |
| :-------: | :------------------------------------------: | :-------- |
|   pixel   | [DisplayPixel](04_protocol.md##DisplayPixel) | 채울 색상 |

- e.g. [모든 디스플레이 제어 명령을 차례대로 실행](examples_11_display.md#DisplayAll)


<br>
<br>


## <a name="send_display_clear">send_display_clear</a>

화면 일부 지우기

```py
def send_display_clear(self, x, y, width, height, pixel = DisplayPixel.BLACK):
```

| 변수 이름 |               형식 또는 범위                |     설명      |
| :-------: | :-----------------------------------------: | :------------ |
|     x     |                -2000 ~ 2000                 | X축 시작 위치 |
|     y     |                -2000 ~ 2000                 | Y축 시작 위치 |
|   width   |                -2000 ~ 2000                 | 너비          |
|  height   |                -2000 ~ 2000                 | 높이          |
|   pixel   | [DisplayPixel](04_protocol.md#DisplayPixel) | 채울 색상     |

- e.g. [무작위 위치와 크기의 Clear를 100회 전송 (send_display_clear 함수 사용)](examples_11_display.md#DisplayClear)


<br>
<br>


## <a name="send_display_invert">send_display_invert</a>

화면 일부 반전

```py
def send_display_invert(self, x, y, width, height):
```

| 변수 이름 | 형식 또는 범위 |     설명      |
| :-------: | :------------: | :------------ |
|     x     |  -2000 ~ 2000  | X축 시작 위치 |
|     y     |  -2000 ~ 2000  | Y축 시작 위치 |
|   width   |  -2000 ~ 2000  | 너비          |
|  height   |  -2000 ~ 2000  | 높이          |

- e.g. [모든 디스플레이 제어 명령을 차례대로 실행](examples_11_display.md#DisplayAll)


<br>
<br>


## <a name="send_display_draw_point">send_display_draw_point</a>

점 찍기

```py
def send_display_draw_point(self, x, y, pixel = DisplayPixel.WHITE):
```

| 변수 이름 |               형식 또는 범위                |   설명   |
| :-------: | :-----------------------------------------: | :------- |
|     x     |                -2000 ~ 2000                 | X축 위치 |
|     y     |                -2000 ~ 2000                 | Y축 위치 |
|   pixel   | [DisplayPixel](04_protocol.md#DisplayPixel) | 점 색상  |

- e.g. [모든 디스플레이 제어 명령을 차례대로 실행](examples_11_display.md#DisplayAll)


<br>
<br>


## <a name="send_display_draw_line">send_display_draw_line</a>

선 그리기

```py
def send_display_draw_line(self, x1, y1, x2, y2, pixel = DisplayPixel.WHITE, line = DisplayLine.SOLID):
```

| 변수 이름 |               형식 또는 범위                |     설명      |
| :-------: | :-----------------------------------------: | :------------ |
|    x1     |                -2000 ~ 2000                 | X축 시작 위치 |
|    y1     |                -2000 ~ 2000                 | Y축 시작 위치 |
|    x2     |                -2000 ~ 2000                 | X축 끝 위치   |
|    y2     |                -2000 ~ 2000                 | Y축 끝 위치   |
|   pixel   | [DisplayPixel](04_protocol.md#DisplayPixel) | 선 색상       |
|   line    |  [DisplayLine](04_protocol.md#DisplayLine)  | 선 형태       |

- e.g. [무작위 위치와 길이의 선을 100번 그리기 (send_display_draw_line 함수 사용)](examples_11_display.md#DisplayDrawLine)


<br>
<br>


## <a name="send_display_draw_rect">send_display_draw_rect</a>

사각형 그리기

```py
def send_display_draw_rect(self, x, y, width, height, pixel = DisplayPixel.WHITE, flag_fill = True, line = DisplayLine.SOLID):
```

| 변수 이름 |               형식 또는 범위                |          설명           |
| :-------: | :-----------------------------------------: | :---------------------- |
|     x     |                -2000 ~ 2000                 | X축 시작 위치           |
|     y     |                -2000 ~ 2000                 | Y축 시작 위치           |
|   width   |                -2000 ~ 2000                 | 너비                    |
|  height   |                -2000 ~ 2000                 | 높이                    |
|   pixel   | [DisplayPixel](04_protocol.md#DisplayPixel) | 색상                    |
| flag_fill |                    Bool                     | True인 경우 내부를 채움 |
|   line    |  [DisplayLine](04_protocol.md#DisplayLine)  | 선 형태                 |

- e.g. [무작위 위치와 크기의 사각형을 100번 출력하기 (send_display_draw_rect 함수 사용)](examples_11_display.md#DisplayDrawRect)


<br>
<br>


## <a name="send_display_draw_circle">send_display_draw_circle</a>

원 그리기

```py
def send_display_draw_circle(self, x, y, radius, pixel = DisplayPixel.WHITE, flag_fill = True):
```

| 변수 이름 |               형식 또는 범위                |          설명           |
| :-------: | :-----------------------------------------: | :---------------------- |
|     x     |                -2000 ~ 2000                 | X축 중심점 위치         |
|     y     |                -2000 ~ 2000                 | Y축 중심점 위치         |
|  radius   |                -2000 ~ 2000                 | 반지름                  |
|   pixel   | [DisplayPixel](04_protocol.md#DisplayPixel) | 색상                    |
| flag_fill |                    Bool                     | True인 경우 내부를 채움 |

- e.g. [무작위 위치와 크기의 원을 100번 출력하기 (send_display_draw_circle 함수 사용)](examples_11_display.md#DisplayDrawCircle)


<br>
<br>


## <a name="send_display_draw_string">send_display_draw_string</a>

문자열 그리기

```py
def send_display_draw_string(self, x, y, message, font = DisplayFont.LIBERATION_MONO_5X8, pixel = DisplayPixel.WHITE):
```

| 변수 이름 |               형식 또는 범위                |     설명      |
| :-------: | :-----------------------------------------: | :------------ |
|     x     |                -2000 ~ 2000                 | X축 위치      |
|     y     |                -2000 ~ 2000                 | Y축 위치      |
|   font    |  [DisplayFont](04_protocol.md#DisplayFont)  | 폰트          |
|   pixel   | [DisplayPixel](04_protocol.md#DisplayPixel) | 색상          |
|  message  |           ASCII String(30자 이하)           | 표시할 문자열 |

- e.g. ['HELLO' 문자열을 무작위 위치에 100번 출력하기](examples_11_display.md#DisplayDrawString)


<br>
<br>


## <a name="send_display_draw_string_align">send_display_draw_string_align</a>

문자열 그리기

***x_start***와 ***x_end*** 사이에 지정한 위치로 문자열을 정렬하여 표시합니다.

```py
def send_display_draw_string_align(self, x_start, x_end, y, message, align = DisplayAlign.CENTER, font = DisplayFont.LIBERATION_MONO_5X8, pixel = DisplayPixel.WHITE):
```

| 변수 이름 |               형식 또는 범위                |     설명      |
| :-------: | :-----------------------------------------: | :------------ |
|  x_start  |                -2000 ~ 2000                 | X축 시작 위치 |
|   x_end   |                -2000 ~ 2000                 | X축 끝 위치   |
|     y     |                -2000 ~ 2000                 | Y축 위치      |
|   align   | [DisplayAlign](04_protocol.md#DisplayAlign) | 정렬          |
|   font    |  [DisplayFont](04_protocol.md#DisplayFont)  | 폰트          |
|   pixel   | [DisplayPixel](04_protocol.md#DisplayPixel) | 색상          |
|  message  |           ASCII String(30자 이하)           | 표시할 문자열 |

- e.g. ['LOVE' 문자열을 왼쪽, 중앙, 오른쪽 정렬을 사용하여 무작위 위치에 10번 출력하기](examples_11_display.md#DisplayDrawStringAlign)


<br>
<br>


## <a name="send_buzzer">send_buzzer</a>

버저 작동

BuzzerMode가 **BuzzerMode.SCALE**이거나 **BuzzerMode.SCALE_RESERVE**인 경우 value에는 [BuzzerScale](04_protocol.md#BuzzerScale)의 value 값을 사용하시면 됩니다.

BuzzerMode가 **BuzzerMode.HZ**이거나 **BuzzerMode.HZ_RESERVE**인 경우 value에는 Hz 값을 사용하시면 됩니다.

```py
def send_buzzer(self, mode, value, time):
```

| 변수 이름 |             형식 또는 범위              |          설명          |
| :-------: | :-------------------------------------: | :--------------------- |
|   mode    | [BuzzerMode](04_protocol.md#BuzzerMode) | 버저 동작 모드         |
|   value   |                0 ~ 8000                 | Scale 값 또는 Hz 값    |
|   time    |               0 ~ 65,535                | 소리를 지속할 시간(ms) |

- e.g. [send_buzzer 함수 테스트](examples_08_buzzer.md#Buzzer)


<br>
<br>


## <a name="send_buzzer_mute">send_buzzer_mute</a>

버저 무음

```py
def send_buzzer_mute(self, time):
```

| 변수 이름 | 형식 또는 범위 |          설명          |
| :-------: | :------------: | :--------------------- |
|   time    |   0 ~ 65,535   | 소리를 지속할 시간(ms) |

- e.g. [send_buzzer 함수 테스트](examples_08_buzzer.md#Buzzer)


<br>
<br>


## <a name="send_buzzer_mute_reserve">send_buzzer_mute_reserve</a>

버저 무음 예약

```py
def send_buzzer_mute_reserve(self, time):
```

| 변수 이름 | 형식 또는 범위 |          설명          |
| :-------: | :------------: | :--------------------- |
|   time    |   0 ~ 65,535   | 소리를 지속할 시간(ms) |

- e.g. [send_buzzer 함수 테스트](examples_08_buzzer.md#Buzzer)


<br>
<br>


## <a name="send_buzzer_scale">send_buzzer_scale</a>

버저 음계 사용하여 소리내기

```py
def send_buzzer_scale(self, scale, time):
```

| 변수 이름 |              형식 또는 범위               |          설명          |
| :-------: | :---------------------------------------: | :--------------------- |
|   scale   | [BuzzerScale](04_protocol.md#BuzzerScale) | Scale                  |
|   time    |                0 ~ 65,535                 | 소리를 지속할 시간(ms) |

- e.g. ['학교 종이 땡땡땡' 일부 연주](examples_08_buzzer.md#BuzzerScale)


<br>
<br>


## <a name="send_buzzer_scale_reserve">send_buzzer_scale_reserve</a>

버저 음계 사용하여 소리내기 예약

```py
def send_buzzer_scale_reserve(self, scale, time):
```

| 변수 이름 |              형식 또는 범위               |          설명          |
| :-------: | :---------------------------------------: | :--------------------- |
|   scale   | [BuzzerScale](04_protocol.md#BuzzerScale) | Scale                  |
|   time    |                0 ~ 65,535                 | 소리를 지속할 시간(ms) |

- e.g. [send_buzzer 함수 테스트](examples_08_buzzer.md#Buzzer)


<br>
<br>


## <a name="send_buzzer_hz">send_buzzer_hz</a>

버저 주파수 사용하여 소리내기

```py
def send_buzzer_hz(self, hz, time):
```

| 변수 이름 | 형식 또는 범위 |          설명          |
| :-------: | :------------: | :--------------------- |
|    hz     |   0 ~ 8,000    | 주파수 값              |
|   time    |   0 ~ 65,535   | 소리를 지속할 시간(ms) |

- e.g. [send_buzzer 함수 테스트](examples_08_buzzer.md#Buzzer)


<br>
<br>


## <a name="send_buzzer_hz_reserve">send_buzzer_hz_reserve</a>

버저 주파수 사용하여 소리내기 예약

```py
def send_buzzer_hz_reserve(self, hz, time):
```

| 변수 이름 | 형식 또는 범위 |          설명          |
| :-------: | :------------: | :--------------------- |
|    hz     |   0 ~ 8,000    | 주파수 값              |
|   time    |   0 ~ 65,535   | 소리를 지속할 시간(ms) |

- e.g. [send_buzzer 함수 테스트](examples_08_buzzer.md#Buzzer)


<br>
<br>


## <a name="send_vibrator">send_vibrator</a>

진동

```py
def send_vibrator(self, on, off, total):
```

| 변수 이름 | 형식 또는 범위 |      설명      |
| :-------: | :------------: | :------------- |
|    on     |   0 ~ 65,535   | 진동을 켠 시간 |
|    off    |   0 ~ 65,535   | 진동을 끈 시간 |
|   total   |   0 ~ 65,535   | 전체 동작 시간 |

- e.g. [send_vibrator 함수 테스트](examples_09_vibrator.md#Vibrator)


<br>
<br>


## <a name="send_vibrator_reserve">send_vibrator_reserve</a>

진동 예약

```py
def send_vibrator_reserve(self, on, off, total):
```

| 변수 이름 | 형식 또는 범위 |      설명      |
| :-------: | :------------: | :------------- |
|    on     |   0 ~ 65,535   | 진동을 켠 시간 |
|    off    |   0 ~ 65,535   | 진동을 끈 시간 |
|   total   |   0 ~ 65,535   | 전체 동작 시간 |


<br>


---

<h3><i>e_drone</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [Command Line](02_commandline.md)
 3. [System](03_system.md)
 4. [Protocol](04_protocol.md)
 5. **Drone**
 6. [Examples - Ping](examples_01_ping.md)
 7. [Examples - Information](examples_02_information.md)
 8. [Examples - Pairing](examples_03_pairing.md)
 9. [Examples - Control](examples_04_control.md)
10. [Examples - Sensor](examples_05_sensor.md)
11. [Examples - Motor](examples_06_motor.md)
12. [Examples - Setup](examples_07_setup.md)
13. [Examples - Buzzer](examples_08_buzzer.md)
14. [Examples - Vibrator](examples_09_vibrator.md)
15. [Examples - Light](examples_10_light.md)
16. [Examples - Display](examples_11_display.md)
17. [Examples - Input](examples_12_input.md)
18. [Examples - Error](examples_13_error.md)

<br>

[Index](index.md)
