**[*CodingRider* for python](index.md)** / **Drone**

Modified : 2024.5.17

---

<h3>drone 모듈을 소개합니다.</h3>

---


<br>


# Drone 클래스


<br>


### Drone 클래스 생성자

Drone 클래스의 생성자는 아래와 같습니다.

```py
def __init__(self, flagCheckBackground = True, flagShowErrorMessage = False, flagShowLogMessage = False, flagShowTransferData = False, flagShowReceiveData = False):
```


| 이름                  | 설명                                                 |
|:----------------------|:-----------------------------------------------------|
| flagCheckBackground   | 수신 받은 데이터를 백그라운드에서 확인               |
| flagShowErrorMessage  | 에러 메세지 표시                                     |
| flagShowLogMessage    | 로그 메세지 표시                                     |
| flagShowTransferData  | 송신 데이터 배열 표시                                |
| flagShowReceiveData   | 수신 데이터 배열 표시                                |


Drone 클래스 생성자 호출 시 인자를 입력하지 않으면 **flagCheckBackground**는 ***True***가 되며, 나머지는 모두 False가 됩니다.

**flagCheckBackground**가 ***True***인 경우에는 데이터를 받을 때마다 내부에서 **check()** 함수를 호출합니다. ***False***인 경우에는 사용자가 직접 **check()** 함수를 호출하여 수신 받은 데이터를 처리해야 합니다.


<br>
<br>


### Drone 클래스의 public 함수 구성

Drone 클래스의 외부에서 접근할 수 있는 함수 목록입니다.

| 이름                                      | 설명                                                                                                     |
|:------------------------------------------|:---------------------------------------------------------------------------------------------------------|
| isOpen()                                  | 시리얼 포트가 열린 경우 True 반환                                                                        |
| open(portname)                            | 시리얼 포트 열기. 포트가 열린 경우 True 반환                                                             |
| close()                                   | 시리얼 포트 닫기                                                                                         |
| makeTransferDataArray(header, data)       | 전송할 데이터 바이트 배열 생성                                                                           |
| transfer(header, data)                    | 데이터 전송(내부에서 makeTransferDataArray 함수를 실행함)                                                |
| check()                                   | 수신 받은 데이터 확인. 데이터를 받은 경우 DataType을 반환                                                |
| checkDetail()                             | 수신 받은 데이터 확인. Header와 Data를 튜플로 반환                                                       |
| setEventHandler(dataType, eventHandler)   | 특정 타입의 데이터를 수신했을 때 호출할 사용자 지정 함수 등록                                            |
| getHeader(dataType)                       | 지정한 타입의 데이터와 함께 받은 헤더 반환                                                               |
| getData(dataType)                         | 지정한 타입의 데이터 반환(데이터가 없으면 None 반환)                                                     |
| getCount(dataType)                        | 지정한 타입의 데이터를 받은 횟수를 반환(데이터가 없으면 None 반환)                                       |
| convertByteArrayToString(dataArray)       | 바이트 배열을 Hex 문자열로 변경하여 반환                                                                 |


<br>
<br>


### Drone 클래스 데이터 수신 처리부

Drone 클래스의 데이터 수신 처리부는 아래와 같이 구성되어 있습니다.

| 이름            | 설명                                                                                                  |
|:----------------|:------------------------------------------------------------------------------------------------------|
| _receiving()    | 데이터 수신 Thread, 수신 받은 데이터를 버퍼에 저장                                                    |
| check()         | 버퍼에 저장된 데이터를 한 바이트씩 읽어 receiver에 전달. 하나의 데이터 블럭을 받은 경우 *_handler()*를 호출하여 받은 데이터를 파싱해서 저장하고 dataType을 반환. 받은 데이터가 없으면 **DataType.None_** 반환 |
| _handler()      | 헤더를 내부에 저장. 데이터는 파싱하여 내부에 저장. 이벤트 처리 함수가 등록된 경우 해당 함수 호출      |


<br>
<br>


# 함수 목록


<br>


## 일반

| 이름                                                              | 설명                                        |
|:------------------------------------------------------------------|:--------------------------------------------|
| [sendPing](#sendPing)                                             | 핑 전송                                     |
| [sendRequest](#sendRequest)                                       | 데이터 요청                                 |
| [sendPairing](#sendPairing)                                       | 페어링 설정                                 |


<br>


## 조종

| 이름                                                              | 설명                                        |
|:------------------------------------------------------------------|:--------------------------------------------|
| [sendTakeOff](#sendTakeOff)                                       | 이륙                                        |
| [sendLanding](#sendLanding)                                       | 착륙                                        |
| [sendStop](#sendStop)                                             | 정지                                        |
| [sendControl](#sendControl)                                       | 비행 조종                                   |
| [sendControlWhile](#sendControlWhile)                             | 지정한 시간 동안 비행 조종 명령 전송        |
| [sendControlPosition16](#sendControlPosition16)                   | 이동(RF)                                    |
| [sendControlPosition](#sendControlPosition)                       | 이동(UART, USB)                             |


<br>


## 설정

| 이름                                                              | 설명                                        |
|:------------------------------------------------------------------|:--------------------------------------------|
| [sendCommand](#sendCommand)                                       | 명령 전송                                   |
| [sendCommandLightEvent](#sendCommandLightEvent)                   | 명령 전송 + LED 이벤트                      |
| [sendCommandLightEventColor](#sendCommandLightEventColor)         | 명령 전송 + LED 이벤트(RGB)                 |
| [sendCommandLightEventColors](#sendCommandLightEventColors)       | 명령 전송 + LED 이벤트(팔레트)              |
| [sendModeControlFlight](#sendModeControlFlight)                   | 비행 제어 모드 변경                         |
| [sendHeadless](#sendHeadless)                                     | 헤드리스 설정                               |
| [sendTrim](#sendTrim)                                             | Trim 값을 지정하여 변경                     |
| [sendWeight](#sendWeight)                                         | Weight 설정                                 |
| [sendLostConnection](#sendLostConnection)                         | 연결이 끊긴 후 반응 시간 설정               |
| [sendFlightEvent](#sendFlightEvent)                               | 비행 이벤트 실행                            |
| [sendClearBias](#sendClearBias)                                   | 바이어스 초기화                             |
| [sendClearTrim](#sendClearTrim)                                   | Trim 초기화                                 |
| [sendSetDefault](#sendSetDefault)                                 | 장치 설정 초기화                            |

<br>


## 모터

| 이름                                                              | 설명                                        |
|:------------------------------------------------------------------|:--------------------------------------------|
| [sendMotor](#sendMotor)                                           | 모터 동작 제어                              |
| [sendMotorSingle](#sendMotorSingle)                               | 단일 모터 동작 제어                         |

<br>


## LED

| 이름                                                              | 설명                                        |
|:------------------------------------------------------------------|:--------------------------------------------|
| [sendLightManual](#sendLightManual)                               | 수동 제어                                   |
| [sendLightModeColor](#sendLightModeColor)                         | 모드 설정 (RGB)                             |
| [sendLightModeColors](#sendLightModeColors)                       | 모드 설정 (팔레트)                          |
| [sendLightEventColor](#sendLightEventColor)                       | 이벤트 설정 (RGB)                           |
| [sendLightEventColors](#sendLightEventColors)                     | 이벤트 설정 (팔레트)                        |
| [sendLightDefaultColor](#sendLightDefaultColor)                   | 기본 모드 설정 (RGB)                        |

<br>


## 조종기 버저 

| 이름                                                              | 설명                                        |
|:------------------------------------------------------------------|:--------------------------------------------|
| [sendBuzzer](#sendBuzzer)                                         | 소리 내기                                   |
| [sendBuzzerMute](#sendBuzzerMute)                                 | 묵음                                        |
| [sendBuzzerMuteReserve](#sendBuzzerMuteReserve)                   | 묵음 예약                                   |
| [sendBuzzerScale](#sendBuzzerScale)                               | 음계를 사용하여 소리 내기                   |
| [sendBuzzerScaleReserve](#sendBuzzerScaleReserve)                 | 음계를 사용하여 소리 내기 예약              |
| [sendBuzzerHz](#sendBuzzerHz)                                     | 주파수를 사용하여 소리 내기                 |
| [sendBuzzerHzReserve](#sendBuzzerHzReserve)                       | 주파수를 사용하여 소리 내기 예약            |

<br>


## 조종기 진동

| 이름                                                              | 설명                                        |
|:------------------------------------------------------------------|:--------------------------------------------|
| [sendVibrator](#sendVibrator)                                     | 진동 설정                                   |
| [sendVibratorReserve](#sendVibratorReserve)                       | 진동 예약                                   |


<br>
<br>


# 함수 정의


<br>
<br>


## <a name="sendPing">sendPing</a>

핑 전송

다른 장치와의 연결 상태를 확인할 때 사용합니다. 상대 장치는 Ping에 대한 응답으로 Ack를 전송합니다.

```py
def sendPing(self, deviceType):
```

| 변수 이름                  | 형식 또는 범위                              | 설명                             |
|:--------------------------:|:-------------------------------------------:|:---------------------------------|
| deviceType                 | [DeviceType](02_system.md#DeviceType)       | 전송할 대상 장치                 |


<br>
<br>


## <a name="sendRequest">sendRequest</a>

데이터 요청

지정한 장치에 데이터를 요청할 때 사용합니다.

```py
def sendRequest(self, deviceType, dataType):
```

| 변수 이름                  | 형식 또는 범위                              | 설명                             |
|:--------------------------:|:-------------------------------------------:|:---------------------------------|
| deviceType                 | [DeviceType](02_system.md#DeviceType)       | 전송할 대상 장치                 |
| dataType                   | [DataType](#DataType)                       | 데이터의 타입                    |

- e.g. [조종기의 펌웨어 정보 요청](examples_08_information.md#Information)

<br>
<br>


## <a name="sendPairing">sendPairing</a>

페어링 설정

지정한 장치의 페어링 설정을 변경할 때 사용합니다.

```py
def sendPairing(self, deviceType, address0, address1, address2, address3, address4, channel0):
```

| 변수 이름                   | 형식 또는 범위                             | 설명                               |
|:--------------------------:|:-----------------------------------------:|:----------------------------------|
| deviceType                 | [DeviceType](02_system.md#DeviceType)     | 전송할 대상 장치                   |
| address0                   | 0 ~ 65535                                 | 장치의 주소 0                      |
| address1                   | 0 ~ 65535                                 | 장치의 주소 1                      |
| address2                   | 0 ~ 65535                                 | 장치의 주소 2                      |
| address3                   | 0 ~ 65535                                 | 장치의 주소 3                      |
| address4                   | 0 ~ 65535                                 | 장치의 주소 4                      |
| channel0                   | 0 ~ 81                                    | 채널 0                             |



<br>
<br>


## <a name="sendTakeOff">sendTakeOff</a>

이륙

이륙을 할 때 사용합니다.

만약 이륙 준비 상태가 아니라면 자동으로 이륙 준비 상태를 거치게 됩니다.

```py
def sendTakeOff(self):
```

- e.g. [이륙, 호버링, 착륙 테스트](examples_01_control.md#ControlWhileAndLanding)


<br>
<br>


## <a name="sendLanding">sendLanding</a>

착륙

비행 모드로 동작 시 착륙을 할 때 사용합니다.

```py
def sendLanding(self):
```

- e.g. [이륙, 호버링, 착륙 테스트](examples_01_control.md#ControlWhileAndLanding)



<br>
<br>


## <a name="sendStop">sendStop</a>

정지

드론 동작 모드에 관계없이 강제로 정지할 때 사용합니다.

```py
def sendStop(self):
```

- e.g. [이륙, 조종, 정지 테스트](examples_01_control.md#ControlWhile)


<br>
<br>


## <a name="sendControl">sendControl</a>

비행 조종

비행 및 주행에 모두 사용할 수 있습니다.

```py
def sendControl(self, roll, pitch, yaw, throttle):
```

| 변수 이름                 | 형식 또는 범위                   | 설명                   |
|:-------------------------:|:--------------------------------:|:-----------------------|
| roll                      | -100 ~ 100                       | Roll                   |
| pitch                     | -100 ~ 100                       | Pitch                  |
| yaw                       | -100 ~ 100                       | Yaw                    |
| throttle                  | -100 ~ 100                       | Throttle               |


<br>
<br>


## <a name="sendControlWhile">sendControlWhile</a>

비행 조종

비행 및 주행에 모두 사용할 수 있습니다.
timeMs에 지정한 ms동안 연속으로 조종 명령을 전송합니다.

```py
def sendControlWhile(self, roll, pitch, yaw, throttle, timeMs):
```

| 변수 이름                 | 형식 또는 범위                   | 설명                   |
|:-------------------------:|:--------------------------------:|:-----------------------|
| roll                      | -100 ~ 100                       | Roll                   |
| pitch                     | -100 ~ 100                       | Pitch                  |
| yaw                       | -100 ~ 100                       | Yaw                    |
| throttle                  | -100 ~ 100                       | Throttle               |
| timeMs                    | 0 ~ 1,000,000                    | 동작 시간(ms)          |

- e.g. [이륙, 호버링, 착륙 테스트](examples_01_control.md#ControlWhileAndLanding)


<br>
<br>


## <a name="sendControlPosition16">sendControlPosition16</a>

드론 이동 명령

모든 변수에 2byte 정수를 사용하는 대신 position과 velocity의 값에 x10을 적용.

```py
def sendControlPosition16(self, positionX, positionY, positionZ, velocity, heading, rotationalVelocity):
```

| 변수 이름             | 형식     | 범위                       | 단위          | 설명                 |
|:---------------------:|:--------:|:--------------------------:|:--------------|:---------------------|
| positionX             | Int16    | -100 ~ 100(-10.0 ~ 10.0)   | meter x 10    | 앞(+), 뒤(-)         |
| positionY             | Int16    | -100 ~ 100(-10.0 ~ 10.0)   | meter x 10    | 좌(+), 우(-)         |
| positionZ             | Int16    | -100 ~ 100(-10.0 ~ 10.0)   | meter x 10    | 위(+), 아래(-)       |
| velocity              | Int16    | 0 ~ 20(0.0 ~ 2.0)          | m/s x 10      | 위치 이동 속도       |
| heading               | Int16    | -360 ~ 360                 | degree        | 좌회전(+), 우회전(-) |
| rotationalVelocity    | Int16    | 10 ~ 360                   | degree/s      | 좌우 회전 속도       |


<br>
<br>


## <a name="sendControlPosition">sendControlPosition</a>

드론 이동 명령

position과 velocity는 실수 값, heading과 rotationalVelocity에는 정수 값 사용

```py
def sendControlPosition(self, positionX, positionY, positionZ, velocity, heading, rotationalVelocity):
```

| 변수 이름             | 형식   | 범위           | 단위     | 설명                 |
|:---------------------:|:------:|:--------------:|:---------|:---------------------|
| positionX             | float  | -10.0 ~ 10.0   | meter    | 앞(+), 뒤(-)         |
| positionY             | float  | -10.0 ~ 10.0   | meter    | 좌(+), 우(-)         |
| positionZ             | float  | -10.0 ~ 10.0   | meter    | 위(+), 아래(-)       |
| velocity              | float  | 0.1 ~ 2.0      | m/s      | 위치 이동 속도       |
| heading               | Int16  | -360 ~ 360     | degree   | 좌회전(+), 우회전(-) |
| rotationalVelocity    | Int16  | 10 ~ 360       | degree/s | 좌우 회전 속도       |

- e.g. [이륙, 호버링, 전진, 착륙 테스트](examples_01_control.md#ControlPosition)
- e.g. [이륙, 호버링, 1미터 전진, 1미터 오른쪽 이동, 리턴 홈 테스트](examples_01_control.md#ControlReturnHome)


<br>
<br>


## <a name="sendCommand">sendCommand</a>

명령 전송

드론에 명령을 전달할 때 사용합니다.

option에는 각 형식의 value 값 또는 숫자 값을 넣으셔야 합니다.

```py
def sendCommand(self, commandType, option = 0):
```

| 변수 이름      | 형식 또는 범위                                       | 설명                         |
|:--------------:|:----------------------------------------------------:|:-----------------------------|
| commandType    | [CommandType](03_protocol.md#CommandType)            | 명령 타입                    |
| option         | [ModeControlFlight](02_system.md#ModeControlFlight)  | 옵션                         |
|                | [FlightEvent](02_system.md#FlightEvent)              |                              |
|                | [Headless](02_system.md#Headless)                    |                              |
|                | [Trim](02_system.md#Trim)                            |                              |
|                | UInt8                                                |                              |



<br>
<br>


## <a name="sendCommandLightEvent">sendCommandLightEvent</a>

명령 + LED 이벤트

드론에 명령을 전달할 때 사용합니다.

option에는 각 형식의 value 값 또는 숫자 값을 넣으셔야 합니다.

```py
def sendCommandLightEvent(self, commandType, option, lightEvent, interval, repeat):
```

| 변수 이름      | 형식 또는 범위                                       | 설명                          |
|:--------------:|:----------------------------------------------------:|:------------------------------|
| commandType    | [CommandType](03_protocol.md#CommandType)            | 명령 타입                     |
| option         | [ModeControlFlight](02_system.md#ModeControlFlight)  | 옵션                          |
|                | [FlightEvent](02_system.md#FlightEvent)              |                               |
|                | [Headless](02_system.md#Headless)                    |                               |
|                | [Trim](02_system.md#Trim)                            |                               |
|                | UInt8                                                |                               |
| lightEvent     | UInt8                                                | LED 동작 모드                 |
| interval       | 0 ~ 65535                                            | 내부 밝기 제어 함수 호출 주기 |
| repeat         | 0 ~ 255                                              | 반복 횟수                     |


<br>
<br>


## <a name="sendCommandLightEventColor">sendCommandLightEventColor</a>

명령 + LED 이벤트(RGB)

드론에 명령을 전달할 때 사용합니다.

option에는 각 형식의 value 값 또는 숫자 값을 넣으셔야 합니다.

```py
def sendCommandLightEventColor(self, commandType, option, lightEvent, interval, repeat, r, g, b):
```

| 변수 이름      | 형식 또는 범위                                       | 설명                          |
|:--------------:|:----------------------------------------------------:|:------------------------------|
| commandType    | [CommandType](03_protocol.md#CommandType)            | 명령 타입                     |
| option         | [ModeControlFlight](02_system.md#ModeControlFlight)  | 옵션                          |
|                | [FlightEvent](02_system.md#FlightEvent)              |                               |
|                | [Headless](02_system.md#Headless)                    |                               |
|                | [Trim](02_system.md#Trim)                            |                               |
|                | UInt8                                                |                               |
| lightEvent     | UInt8                                                | LED 동작 모드                 |
| interval       | 0 ~ 65535                                            | 내부 밝기 제어 함수 호출 주기 |
| repeat         | 0 ~ 255                                              | 반복 횟수                     |
| r              | 0 ~ 255                                              | Red                           |
| g              | 0 ~ 255                                              | Green                         |
| b              | 0 ~ 255                                              | Blue                          |


<br>
<br>


## <a name="sendCommandLightEventColors">sendCommandLightEventColors</a>

명령 + LED 이벤트(Palette)

드론에 명령을 전달할 때 사용합니다.

option에는 각 형식의 value 값 또는 숫자 값을 넣으셔야 합니다.

```py
def sendCommandLightEventColors(self, commandType, option, lightEvent, interval, repeat, colors):
```

| 변수 이름      | 형식 또는 범위                                       | 설명                          |
|:--------------:|:----------------------------------------------------:|:------------------------------|
| commandType    | [CommandType](03_protocol.md#CommandType)            | 명령 타입                     |
| option         | [ModeControlFlight](02_system.md#ModeControlFlight)  | 옵션                          |
|                | [FlightEvent](02_system.md#FlightEvent)              |                               |
|                | [Headless](02_system.md#Headless)                    |                               |
|                | [Trim](02_system.md#Trim)                            |                               |
|                | UInt8                                                |                               |
| lightEvent     | UInt8                                                | LED 동작 모드                 |
| interval       | 0 ~ 65535                                            | 내부 밝기 제어 함수 호출 주기 |
| repeat         | 0 ~ 255                                              | 반복 횟수                     |
| colors         | [Colors](03_protocol.md#Colors)                      | 색상 팔레트 인덱스            |


<br>
<br>


## <a name="sendModeControlFlight">sendModeControlFlight</a>

비행 제어 모드 설정

드론 비행 제어 모드를 변경합니다.

```py
def sendModeControlFlight(self, modeControlFlight):
```

| 변수 이름                 | 형식 또는 범위                                        | 설명                         |
|:-------------------------:|:-----------------------------------------------------:|:-----------------------------|
| modeControlFlight         | [ModeControlFlight](02_system.md#ModeControlFlight)   | 비행 제어 모드               |

- e.g. [비행 제어 모드를 변경 후 확인](examples_03_setup.md#ModeControlFlight)


<br>
<br>


## <a name="sendHeadless">sendHeadless</a>

Headless 설정

```py
def sendHeadless(self, headless):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                        |
|:-------------------------:|:-------------------------------------------------:|:----------------------------|
| headless                  | [Headless](02_system.md#Headless)                 | Headless 설정               |

- e.g. [드론 Headless 설정 변경 후 확인](examples_03_setup.md#Headless)


<br>
<br>



## <a name="sendTrim">sendTrim</a>

비행 Trim 설정

```py
def sendTrim(self, roll, pitch, yaw, throttle):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                        |
|:-------------------------:|:-------------------------------------------------:|:----------------------------|
| roll                      | -200 ~ 200                                        | Roll                        |
| pitch                     | -200 ~ 200                                        | Pitch                       |
| yaw                       | -200 ~ 200                                        | Yaw                         |
| throttle                  | -200 ~ 200                                        | Throttle                    |

- e.g. [드론 Trim 설정 변경 후 확인](examples_03_setup.md#Trim)


<br>
<br>


## <a name="sendWeight">sendWeight</a>

무게

```py
def sendWeight(self, weight):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                        |
|:-------------------------:|:-------------------------------------------------:|:----------------------------|
| weight                    | [Weight](02_system.md#Weight)                     | 무게                        |


<br>
<br>


## <a name="sendLostConnection">sendLostConnection</a>

통신 연결이 끊긴 후 반응 시간 설정

마지막으로 비행 이벤트 또는 조종 명령을 보냈던 장치와의 연결이 끊어진 후에 지정한 시간이 경과하면 해당 명령을 실행. 시간을 0으로 설정한 경우 해당 명령은 실행하지 않음. 시간 단위는 ms

```py
def sendLostConnection(self, timeNeutral, timeLanding, timeStop):
```

| 변수 이름     | 형식 또는 범위     | 설명      |
|:-------------:|:------------------:|:----------|
| timeNeutral   | 0 ~ 65,535         | 조종 중립 |
| timeLanding   | 0 ~ 65,535         | 착륙      |
| timeStop      | 0 ~ 4,294,967,295  | 정지      |


<br>
<br>


## <a name="sendFlightEvent">sendFlightEvent</a>

비행 이벤트 실행

```py
def sendFlightEvent(self, flightEvent):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                        |
|:-------------------------:|:-------------------------------------------------:|:----------------------------|
| flightEvent               | [FlightEvent](02_system.md#FlightEvent)           | 비행 이벤트                 |


<br>
<br>


## <a name="sendClearBias">sendClearBias</a>

Accel, Gyro Bias 초기화

```py
def sendClearBias(self):
```


<br>
<br>


## <a name="sendClearTrim">sendClearTrim</a>

비행, 주행 Trim 초기화

```py
def sendClearTrim(self):
```


<br>
<br>


## <a name="sendSetDefault">sendSetDefault</a>

장치 설정 초기화

지정한 장치의 설정을 초기화 함

```py
def sendSetDefault(self, deviceType):
```


<br>
<br>


## <a name="sendMotor">sendMotor</a>

4개의 모터를 미리 지정된 방향으로 회전

```py
def sendMotor(self, motor0, motor1, motor2, motor3):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                         |
|:-------------------------:|:-------------------------------------------------:|:-----------------------------|
| motor0                    | 0 ~ 4095                                          | 왼쪽 앞 모터 속도 지정       |
| motor1                    | 0 ~ 4095                                          | 오른쪽 앞 모터 속도 지정     |
| motor2                    | 0 ~ 4095                                          | 오른쪽 뒤 모터 속도 지정     |
| motor3                    | 0 ~ 4095                                          | 왼쪽 뒤 모터 속도 지정       |


<br>
<br>


## <a name="sendMotorSingle">sendMotorSingle</a>

1개의 모터를 회전 방향을 지정하여 동작

target에 들어가는 값은 0~3입니다. 모터의 순서는 왼쪽 앞 모터부터 시계방향입니다.

```py
def sendMotorSingle(self, target, rotation, value):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                          |
|:-------------------------:|:-------------------------------------------------:|:------------------------------|
| target                    | 0 ~ 3                                             | 제어할 모터의 번호            |
| rotation                  | [Rotation](02_system.md#Rotation)                 | 모터의 회전 방향              |
| value                     | 0 ~ 4095                                          | 모터의 속도                   |


<br>
<br>


## <a name="sendLightManual">sendLightManual</a>

LED 수동 제어

flags에는 [LightFlagsDrone](#LightFlagsDrone), [LightFlagsController](#LightFlagsController)의 value 값을 사용하거나 직접 플래그에 해당하는 비트를 선택하시면 됩니다.

brightness는 값은 0일 때 꺼지며 값이 커질수록 밝아집니다.

```py
def sendLightManual(self, deviceType, flags, brightness):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                          |
|:-------------------------:|:-------------------------------------------------:|:------------------------------|
| deviceType                | [DeviceType](02_system.md#DeviceType)             | LED를 제어할 장치             |
| flags                     | 0b00000000 ~ 0b11111111                           | LED 플래그                    |
| brightness                | 0 ~ 255                                           | 밝기                          |

- e.g. [sendLightManual() 함수를 사용하여 조종기 LED 제어하기](examples_06_light.md#LightManual)


<br>
<br>


## <a name="sendLightModeColor">sendLightModeColor</a>

LED 모드 설정(RGB)

lightMode 변수에는 [LightModeDrone](#LightModeDrone), [LightModeController](#LightModeController)의 value 값을 사용합니다.

```py
def sendLightModeColor(self, lightMode, interval, r, g, b):
```

| 변수 이름                 | 형식 또는 범위          | 설명                                     |
|:-------------------------:|:-----------------------:|:-----------------------------------------|
| lightMode                 | UInt8                   | LED 동작 모드                            |
| interval                  | 0 ~ 65535               | 내부 밝기 제어 함수 호출 주기            |
| r                         | 0 ~ 255                 | Red                                      |
| g                         | 0 ~ 255                 | Green                                    |
| b                         | 0 ~ 255                 | Blue                                     |

- e.g. [드론의 LED를 랜덤한 색으로 점점 밝아졌다 어두워지게 하는 명령을 10회 실행 (sendLightModeColor 함수 사용)](examples_06_light.md#LightMode)


<br>
<br>



## <a name="sendLightModeColors">sendLightModeColors</a>

LED 모드 설정(Palette)

lightMode 변수에는 [LightModeDrone](#LightModeDrone), [LightModeController](#LightModeController)의 value 값을 사용합니다.

```py
def sendLightModeColors(self, lightMode, interval, colors):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                                     |
|:-------------------------:|:-------------------------------------------------:|:-----------------------------------------|
| lightMode                 | UInt8                                             | LED 동작 모드                            |
| interval                  | 0 ~ 65535                                         | 내부 밝기 제어 함수 호출 주기            |
| colors                    | [Colors](03_protocol.md#Colors)                   | 색상 팔레트 인덱스                       |

- e.g. [sendLightMode, sendLightEvent 함수를 사용하여 드론 LED 제어하기](examples_06_light.md#LightMode)


<br>
<br>


## <a name="sendLightEventColor">sendLightEventColor</a>

LED 이벤트 설정(RGB)

lightEvent 변수에는 [LightModeDrone](#LightModeDrone), [LightModeController](#LightModeController)의 value 값을 사용합니다.

```py
def sendLightEventColor(self, lightEvent, interval, repeat, r, g, b):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                                     |
|:-------------------------:|:-------------------------------------------------:|:-----------------------------------------|
| lightEvent                | UInt8                                             | LED 동작 모드                            |
| interval                  | 0 ~ 65535                                         | 내부 밝기 제어 함수 호출 주기             |
| repeat                    | 0 ~ 255                                           | 반복 횟수                                |
| r                         | 0 ~ 255                                           | Red                                      |
| g                         | 0 ~ 255                                           | Green                                    |
| b                         | 0 ~ 255                                           | Blue                                     |

- e.g. [sendLightMode, sendLightEvent 함수를 사용하여 드론 LED 제어하기](examples_06_light.md#LightMode)


<br>
<br>


## <a name="sendLightEventColors">sendLightEventColors</a>

LED 이벤트 설정(Palette)

lightEvent 변수에는 [LightModeDrone](#LightModeDrone), [LightModeController](#LightModeController)의 value 값을 사용합니다.

```py
def sendLightEventColors(self, lightEvent, interval, repeat, colors):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                                     |
|:-------------------------:|:-------------------------------------------------:|:-----------------------------------------|
| lightEvent                | UInt8                                             | LED 동작 모드                            |
| interval                  | 0 ~ 65535                                         | 내부 밝기 제어 함수 호출 주기            |
| repeat                    | 0 ~ 255                                           | 반복 횟수                                |
| colors                    | [Colors](03_protocol.md#Colors)                   | 색상 팔레트 인덱스                       |

- e.g. [sendLightMode, sendLightEvent 함수를 사용하여 드론 LED 제어하기](examples_06_light.md#LightMode)


<br>
<br>


## <a name="sendLightDefaultColor">sendLightDefaultColor</a>

LED 기본 모드 설정(RGB)

lightMode 변수에는 [LightModeDrone](#LightModeDrone), [LightModeController](#LightModeController)의 value 값을 사용합니다.

```py
def sendLightDefaultColor(self, lightMode, interval, r, g, b):
```

| 변수 이름                 | 형식 또는 범위          | 설명                                     |
|:-------------------------:|:-----------------------:|:-----------------------------------------|
| lightMode                 | UInt8                   | LED 동작 모드                            |
| interval                  | 0 ~ 65535               | 내부 밝기 제어 함수 호출 주기            |
| r                         | 0 ~ 255                 | Red                                      |
| g                         | 0 ~ 255                 | Green                                    |
| b                         | 0 ~ 255                 | Blue                                     |

<br>
<br>


## <a name="sendBuzzer">sendBuzzer</a>

버저 작동

BuzzerMode가 **BuzzerMode.Scale**이거나 **BuzzerMode.ScaleReserve**인 경우 value에는 [BuzzerScale](03_protocol.md#BuzzerScale)의 value 값을 사용하시면 됩니다.

BuzzerMode가 **BuzzerMode.Hz**이거나 **BuzzerMode.HzReserve**인 경우 value에는 Hz 값을 사용하시면 됩니다.

```py
def sendBuzzer(self, mode, value, time):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                                     |
|:-------------------------:|:-------------------------------------------------:|:-----------------------------------------|
| mode                      | [BuzzerMode](03_protocol.md#BuzzerMode)           | 버저 동작 모드                           |
| value                     | 0 ~ 8000                                          | Scale 값 또는 Hz 값                      |
| time                      | 0 ~ 65,535                                        | 소리를 지속할 시간(ms)                   |

- e.g. [sendBuzzer 함수 테스트](examples_04_buzzer.md#Buzzer)


<br>
<br>


## <a name="sendBuzzerMute">sendBuzzerMute</a>

버저 무음

```py
def sendBuzzerMute(self, time):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                                     |
|:-------------------------:|:-------------------------------------------------:|:-----------------------------------------|
| time                      | 0 ~ 65,535                                        | 소리를 지속할 시간(ms)                   |

- e.g. [sendBuzzer 함수 테스트](examples_04_buzzer.md#Buzzer)


<br>
<br>


## <a name="sendBuzzerMuteReserve">sendBuzzerMuteReserve</a>

버저 무음 예약

```py
def sendBuzzerMuteReserve(self, time):
```

| 변수 이름                 | 형식 또는 범위      | 설명                            |
|:-------------------------:|:-------------------:|:--------------------------------|
| time                      | 0 ~ 65,535          | 소리를 지속할 시간(ms)          |

- e.g. [sendBuzzer 함수 테스트](examples_04_buzzer.md#Buzzer)


<br>
<br>


## <a name="sendBuzzerScale">sendBuzzerScale</a>

버저 음계 사용하여 소리내기

```py
def sendBuzzerScale(self, scale, time):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                                     |
|:-------------------------:|:-------------------------------------------------:|:-----------------------------------------|
| scale                     | [BuzzerScale](03_protocol.md#BuzzerScale)         | Scale                                    |
| time                      | 0 ~ 65,535                                        | 소리를 지속할 시간(ms)                   |

- e.g. ['학교 종이 땡땡땡' 일부 연주](examples_04_buzzer.md#BuzzerScale)


<br>
<br>


## <a name="sendBuzzerScaleReserve">sendBuzzerScaleReserve</a>

버저 음계 사용하여 소리내기 예약

```py
def sendBuzzerScaleReserve(self, scale, time):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                                     |
|:-------------------------:|:-------------------------------------------------:|:-----------------------------------------|
| scale                     | [BuzzerScale](03_protocol.md#BuzzerScale)         | Scale                                    |
| time                      | 0 ~ 65,535                                        | 소리를 지속할 시간(ms)                   |

- e.g. [sendBuzzer 함수 테스트](examples_04_buzzer.md#Buzzer)


<br>
<br>


## <a name="sendBuzzerHz">sendBuzzerHz</a>

버저 주파수 사용하여 소리내기

```py
def sendBuzzerHz(self, hz, time):
```

| 변수 이름                 | 형식 또는 범위    | 설명                                     |
|:-------------------------:|:-----------------:|:-----------------------------------------|
| hz                        | 0 ~ 8,000         | 주파수 값                                |
| time                      | 0 ~ 65,535        | 소리를 지속할 시간(ms)                   |

- e.g. [sendBuzzer 함수 테스트](examples_04_buzzer.md#Buzzer)


<br>
<br>


## <a name="sendBuzzerHzReserve">sendBuzzerHzReserve</a>

버저 주파수 사용하여 소리내기 예약

```py
def sendBuzzerHzReserve(self, hz, time):
```

| 변수 이름                 | 형식 또는 범위    | 설명                                     |
|:-------------------------:|:-----------------:|:-----------------------------------------|
| hz                        | 0 ~ 8,000         | 주파수 값                                |
| time                      | 0 ~ 65,535        | 소리를 지속할 시간(ms)                   |

- e.g. [sendBuzzer 함수 테스트](examples_04_buzzer.md#Buzzer)


<br>
<br>


## <a name="sendVibrator">sendVibrator</a>

진동

```py
def sendVibrator(self, on, off, total):
```

| 변수 이름                 | 형식 또는 범위    | 설명                                     |
|:-------------------------:|:-----------------:|:-----------------------------------------|
| on                        | 0 ~ 65,535        | 진동을 켠 시간                           |
| off                       | 0 ~ 65,535        | 진동을 끈 시간                           |
| total                     | 0 ~ 65,535        | 전체 동작 시간                           |

- e.g. [sendVibrator 함수 테스트](examples_05_vibrator.md#Vibrator)


<br>
<br>


## <a name="sendVibratorReserve">sendVibratorReserve</a>

진동 예약

```py
def sendVibratorReserve(self, on, off, total):
```

| 변수 이름                 | 형식 또는 범위    | 설명                                     |
|:-------------------------:|:-----------------:|:-----------------------------------------|
| on                        | 0 ~ 65,535        | 진동을 켠 시간                           |
| off                       | 0 ~ 65,535        | 진동을 끈 시간                           |
| total                     | 0 ~ 65,535        | 전체 동작 시간                           |


<br>


---

<h3><i>CodingRider</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [System](02_system.md)
 3. [Protocol](03_protocol.md)
 4. **Drone**
 5. [Examples - Control](examples_01_control.md)
 6. [Examples - Sensor](examples_02_sensor.md)
 7. [Examples - Setup](examples_03_setup.md)
 8. [Examples - Buzzer](examples_04_buzzer.md)
 9. [Examples - Vibrator](examples_05_vibrator.md)
10. [Examples - Light](examples_06_light.md)
11. [Examples - Input](examples_07_input.md)
12. [Examples - Information](examples_08_information.md)
<br>

[Index](index.md)
