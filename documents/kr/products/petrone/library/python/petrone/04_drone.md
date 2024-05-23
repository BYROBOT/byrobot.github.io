**[*petrone* for python](index.md)** / **Drone**

Modified : 2018.11.26

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

| 이름                                           | 설명                                                                                                     |
|:-----------------------------------------------|:---------------------------------------------------------------------------------------------------------|
| isOpen()                                       | 시리얼 포트 연결 상태 반환                                                                               |
| isConnected()                                  | BLE 연결 상태 반환                                                                                       |
| open(portName)                                 | 시리얼 포트 열기. 포트 이름을 지정하지 않으면 마지막에 검색된 장치에 연결. 포트가 열린 경우 True 반환    |
| connect(portName, deviceName, flagSystemReset) | 시리얼 포트가 열리지 않은 경우 시리얼 포트를 열고, PETRONE을 검색하여 가장 신호가 강한 장치에 연결합니다. deviceName을 지정하였으면 지정한 장치가 검색되었을 때에만 연결합니다. flagSystemReset은 시리얼 통신 연결 후 처음 PETRONE LINK를 리셋하고 시작할 때 사용합니다. 기본값은 False 입니다.    |
| close()                                        | 시리얼 포트 닫기                                                                                         |
| makeTransferDataArray(header, data)            | 전송할 데이터 바이트 배열 생성                                                                           |
| transfer(header, data)                         | 데이터 전송(내부에서 makeTransferDataArray 함수를 실행함)                                                |
| check()                                        | 수신 받은 데이터 확인. 데이터를 받은 경우 DataType을 반환                                                |
| checkDetail()                                  | 수신 받은 데이터 확인. Header와 Data를 튜플로 반환                                                       |
| setEventHandler(dataType, eventHandler)        | 특정 타입의 데이터를 수신했을 때 호출할 사용자 지정 함수 등록                                            |
| getHeader(dataType)                            | 지정한 타입의 데이터와 함께 받은 헤더 반환                                                               |
| getData(dataType)                              | 지정한 타입의 데이터 반환(데이터가 없으면 None 반환)                                                     |
| getCount(dataType)                             | 지정한 타입의 데이터를 받은 횟수를 반환(한 번도 받지 못한 경우 0 반환)                                   |


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


<br>


## 조종

| 이름                                                              | 설명                                        |
|:------------------------------------------------------------------|:--------------------------------------------|
| [sendTakeOff](#sendTakeOff)                                       | 이륙                                        |
| [sendLanding](#sendLanding)                                       | 착륙                                        |
| [sendStop](#sendStop)                                             | 정지                                        |
| [sendControl](#sendControl)                                       | 비행 조종                                   |
| [sendControlWhile](#sendControlWhile)                             | 지정한 시간 동안 비행 조종 명령 전송        |
| [sendControlDrive](#sendControlDrive)                             | 자동차 조종                                 |
| [sendControlDriveWhile](#sendControlDriveWhile)                   | 지정한 시간 동안 자동차 조종 명령 전송      |


<br>


## 설정

| 이름                                                              | 설명                                        |
|:------------------------------------------------------------------|:--------------------------------------------|
| [sendCommand](#sendCommand)                                       | 명령 전송                                   |
| [sendModeVehicle](#sendModeVehicle)                               | Flight/Drive 모드 변경                      |
| [sendHeadless](#sendHeadless)                                     | 헤드리스 설정                               |
| [sendTrim](#sendTrim)                                             | Trim 설정                                   |
| [sendTrimFlight](#sendTrimFlight)                                 | 비행 Trim 설정                              |
| [sendTrimDrive](#sendTrimDrive)                                   | 주행 Trim 설정                              |
| [sendFlightEvent](#sendFlightEvent)                               | 비행 이벤트 실행                            |
| [sendDriveEvent](#sendDriveEvent)                                 | 주행 이벤트 실행                            |
| [sendClearTrim](#sendClearTrim)                                   | Trim 초기화                                 |
| [sendClearGyroBias](#sendClearGyroBias)                           | 자이로 바이어스 초기화                      |
| [sendUpdateLookupTarget](#sendUpdateLookupTarget)                 | 펌웨어 정보 확인                            |

<br>


## 모터

| 이름                                                              | 설명                                        |
|:------------------------------------------------------------------|:--------------------------------------------|
| [sendMotor](#sendMotor)                                           | 모터 동작 제어                             

<br>


## 적외선

| 이름                                                              | 설명                                        |
|:------------------------------------------------------------------|:--------------------------------------------|
| [sendIrMessage](#sendIrMessage)                                   | 적외선 데이터 전송                          |

<br>


## LED

| 이름                                                              | 설명                                        |
|:------------------------------------------------------------------|:--------------------------------------------|
| [sendLightMode](#sendLightMode)                                   | 모드 설정(팔레트)                           |
| [sendLightModeCommand](#sendLightModeCommand)                     | 모드 설정(팔레트), 명령                     |
| [sendLightModeCommandIr](#sendLightModeCommandIr)                 | 모드 설정(팔레트), 명령, 적외선             |
| [sendLightModeColor](#sendLightModeColor)                         | 모드 설정(RGB)                              |
| [sendLightEvent](#sendLightEvent)                                 | 이벤트 설정(팔레트)                         |
| [sendLightEventCommand](#sendLightEventCommand)                   | 이벤트 설정(팔레트), 명령                   |
| [sendLightEventCommandIr](#sendLightEventCommandIr)               | 이벤트 설정(팔레트), 명령, 적외선           |
| [sendLightEventColor](#sendLightEventColor)                       | 이벤트 설정(RGB)                            |

<br>


## LINK

| 이름                                                              | 설명                                        |
|:------------------------------------------------------------------|:--------------------------------------------|
| [sendLinkModeBroadcast](#sendLinkModeBroadcast)                   | LINK Broadcast 모드 변경                    |
| [sendLinkSystemReset](#sendLinkSystemReset)                       | LINK 리셋                                   |
| [sendLinkDiscoverStart](#sendLinkDiscoverStart)                   | PETRONE 스캔                                |
| [sendLinkDiscoverStop](#sendLinkDiscoverStop)                     | PETRONE 스캔 중단                           |
| [sendLinkConnect](#sendLinkConnect)                               | PETRONE 연결                                |
| [sendLinkDisconnect](#sendLinkDisconnect)                         | PETRONE 연결 해제                           |
| [sendLinkRssiPollingStart](#sendLinkRssiPollingStart)             | RSSI 수집 시작                              |
| [sendLinkRssiPollingStop](#sendLinkRssiPollingStop)               | RSSI 수집 중단                              |

<br>
<br>


# 함수 정의


<br>
<br>


## <a name="sendPing">sendPing</a>

핑 전송

드론과의 연결 상태를 확인할 때 사용합니다. 응답으로 Ack를 받습니다.

```py
def sendPing(self):
```


<br>
<br>


## <a name="sendRequest">sendRequest</a>

데이터 요청

데이터를 요청할 때 사용합니다.

```py
def sendRequest(self, dataType):
```

| 변수 이름                  | 형식 또는 범위                              | 설명                             |
|:--------------------------:|:-------------------------------------------:|:---------------------------------|
| dataType                   | [DataType](#DataType)                       | 데이터의 타입                    |


<br>
<br>


## <a name="sendTakeOff">sendTakeOff</a>

이륙

비행 모드로 동작 시 이륙을 할 때 사용합니다.

```py
def sendTakeOff(self):
```


<br>
<br>


## <a name="sendLanding">sendLanding</a>

착륙

비행 모드로 동작 시 착륙을 할 때 사용합니다.

```py
def sendLanding(self):
```



<br>
<br>


## <a name="sendStop">sendStop</a>

정지

드론 동작 모드에 관계없이 강제로 정지할 때 사용합니다.

```py
def sendStop(self):
```


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


<br>
<br>


## <a name="sendControlDrive">sendControlDrive</a>

자동차 조종

드론이 자동차 모드로 동작할 때 사용할 수 있습니다.

```py
def sendControlDrive(self, wheel, accel):
```

| 변수 이름                 | 형식 또는 범위                   | 설명                   |
|:-------------------------:|:--------------------------------:|:-----------------------|
| wheel                     | -100 ~ 100                       | Wheel                  |
| accel                     | -100 ~ 100                       | Accel                  |


<br>
<br>


## <a name="sendControlDriveWhile">sendControlDriveWhile</a>

자동차 조종

드론이 자동차 모드로 동작할 때 사용할 수 있습니다.
timeMs에 지정한 ms동안 연속으로 조종 명령을 전송합니다.

```py
def sendControlDriveWhile(self, wheel, accel, timeMs):
```

| 변수 이름                 | 형식 또는 범위                   | 설명                   |
|:-------------------------:|:--------------------------------:|:-----------------------|
| wheel                     | -100 ~ 100                       | Wheel                  |
| accel                     | -100 ~ 100                       | Accel                  |
| timeMs                    | 0 ~ 1,000,000                    | 동작 시간(ms)          |


<br>
<br>


## <a name="sendCommand">sendCommand</a>

명령 전송

드론에 명령을 전달할 때 사용합니다.

option에는 각 형식의 value 값 또는 숫자 값을 넣으셔야 합니다.

```py
def sendCommand(self, commandType, option = 0):
```

| 변수 이름      | 형식 또는 범위                                   | 설명                         |
|:--------------:|:------------------------------------------------:|:-----------------------------|
| commandType    | [CommandType](03_protocol.md#CommandType)        | 명령 타입                    |
| option         | [ModeVehicle](02_system.md#ModeVehicle)          | 옵션                         |
|                | [FlightEvent](02_system.md#FlightEvent)          |                              |
|                | [DriveEvent](02_system.md#DriveEvent)            |                              |
|                | [Headless](02_system.md#Headless)                |                              |
|                | [Trim](02_system.md#Trim)                        |                              |
|                | UInt8                                            |                              |


<br>
<br>


## <a name="sendModeVehicle">sendModeVehicle</a>

Vehicle 동작 모드 설정

드론을 비행 또는 주행 모드로 변경할 수 있습니다.

```py
def sendModeVehicle(self, modeVehicle):
```

| 변수 이름                 | 형식 또는 범위                                   | 설명                         |
|:-------------------------:|:------------------------------------------------:|:-----------------------------|
| modeVehicle               | [ModeVehicle](02_system.md#ModeVehicle)          | Vehicle 동작 모드            |


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


<br>
<br>


## <a name="sendTrim">sendTrim</a>

Trim 설정

```py
def sendTrim(self, trim):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                        |
|:-------------------------:|:-------------------------------------------------:|:----------------------------|
| trim                      | [Trim](02_system.md#Trim)                         | 트림 설정                   |


<br>
<br>


## <a name="sendTrimFlight">sendTrimFlight</a>

비행 Trim 설정

```py
def sendTrimFlight(self, roll, pitch, yaw, throttle):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                        |
|:-------------------------:|:-------------------------------------------------:|:----------------------------|
| roll                      | -200 ~ 200                                        | Roll                        |
| pitch                     | -200 ~ 200                                        | Pitch                       |
| yaw                       | -200 ~ 200                                        | Yaw                         |
| throttle                  | -200 ~ 200                                        | Throttle                    |


<br>
<br>


## <a name="sendTrimDrive">sendTrimDrive</a>

주행 Trim 설정

```py
def sendTrimDrive(self, wheel):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                        |
|:-------------------------:|:-------------------------------------------------:|:----------------------------|
| wheel                     | -200 ~ 200                                        | Wheel                       |


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


## <a name="sendDriveEvent">sendDriveEvent</a>

주행 이벤트 실행

```py
def sendDriveEvent(self, driveEvent):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                        |
|:-------------------------:|:-------------------------------------------------:|:----------------------------|
| driveEvent                | [DriveEvent](02_system.md#DriveEvent)             | 주행 이벤트                 |


<br>
<br>


## <a name="sendClearTrim">sendClearTrim</a>

비행, 주행 Trim 초기화

```py
def sendClearTrim(self):
```


<br>
<br>


## <a name="sendClearGyroBias">sendClearGyroBias</a>

Accel, Gyro Bias 초기화

```py
def sendClearGyroBias(self):
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


## <a name="sendIrMessage">sendIrMessage</a>

적외선 데이터 전송

```py
def sendIrMessage(self, value):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                               |
|:-------------------------:|:-------------------------------------------------:|:-----------------------------------|
| value                     | 0x00000000 ~ 0xFFFFFFFF                           | 적외선으로 전송할 데이터의 값      |


<br>
<br>


<!-- 

## <a name="sendLightMode">sendLightMode</a>

LED 모드 설정(Palette)

lightMode 변수에는 [LightModeDrone](#LightModeDrone), [LightModeController](#LightModeController)의 value 값을 사용합니다.

brightness는 값은 0일 때 꺼지며 값이 커질수록 밝아집니다.

```py
def sendLightMode(self, lightMode, colors, interval):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                                     |
|:-------------------------:|:-------------------------------------------------:|:-----------------------------------------|
| lightMode                 | [LightMode](#LightMode)                           | LED 동작 모드                            |
| colors                    | [Colors](03_protocol.md#Colors)                   | 색상 팔레트 인덱스                       |
| interval                  | 0 ~ 65535                                         | 내부 밝기 제어 함수 호출 주기            |


<br>
<br>


## <a name="sendLightModeColorsCommand">sendLightModeColorsCommand</a>

LED 모드 설정(Palette) + Command

lightMode 변수에는 [LightModeDrone](#LightModeDrone), [LightModeController](#LightModeController)의 value 값을 사용합니다.

brightness는 값은 0일 때 꺼지며 값이 커질수록 밝아집니다.

```py
def sendLightModeColorsCommand(self, lightMode, interval, colors, commandType, option):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                                     |
|:-------------------------:|:-------------------------------------------------:|:-----------------------------------------|
| lightMode                 | UInt8                                             | LED 동작 모드                            |
| interval                  | 0 ~ 65535                                         | 내부 밝기 제어 함수 호출 주기            |
| colors                    | [Colors](03_protocol.md#Colors)                   | 색상 팔레트 인덱스                       |
| commandType               | [CommandType](03_protocol.md#CommandType)         | 명령 타입                                |
| option                    | UInt8                                             | 옵션                                     |


<br>
<br>


## <a name="sendLightModeColorsCommandIr">sendLightModeColorsCommandIr</a>

LED 모드 설정(Palette) + Command + IR

lightMode 변수에는 [LightModeDrone](#LightModeDrone), [LightModeController](#LightModeController)의 value 값을 사용합니다.

brightness는 값은 0일 때 꺼지며 값이 커질수록 밝아집니다.

```py
def sendLightModeColorsCommandIr(self, lightMode, interval, colors, commandType, option, irData):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                                     |
|:-------------------------:|:-------------------------------------------------:|:-----------------------------------------|
| lightMode                 | UInt8                                             | LED 동작 모드                            |
| interval                  | 0 ~ 65535                                         | 내부 밝기 제어 함수 호출 주기            |
| colors                    | [Colors](03_protocol.md#Colors)                   | 색상 팔레트 인덱스                       |
| commandType               | [CommandType](03_protocol.md#CommandType)         | 명령 타입                                |
| option                    | UInt8                                             | 옵션                                     |
| irData                    | 0x00000000 ~ 0xFFFFFFFF                           | 적외선으로 전송할 데이터                 |



## <a name="sendLightModeColor">sendLightModeColor</a>

LED 모드 설정(RGB)

lightMode 변수에는 [LightModeDrone](#LightModeDrone), [LightModeController](#LightModeController)의 value 값을 사용합니다.

brightness는 값은 0일 때 꺼지며 값이 커질수록 밝아집니다.

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


<br>
<br>

<br>
<br>


## <a name="sendLightEventColor">sendLightEventColor</a>

LED 이벤트 설정(RGB)

lightEvent 변수에는 [LightModeDrone](#LightModeDrone), [LightModeController](#LightModeController)의 value 값을 사용합니다.

brightness는 값은 0일 때 꺼지며 값이 커질수록 밝아집니다.

```py
def sendLightEventColor(self, lightEvent, interval, repeat, r, g, b):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                                     |
|:-------------------------:|:-------------------------------------------------:|:-----------------------------------------|
| lightEvent                | UInt8                                             | LED 동작 모드                            |
| interval                  | 0 ~ 65535                                         | 내부 밝기 제어 함수 호출 주기            |
| repeat                    | 0 ~ 255                                           | 반복 횟수                                |
| r                         | 0 ~ 255                                           | Red                                      |
| g                         | 0 ~ 255                                           | Green                                    |
| b                         | 0 ~ 255                                           | Blue                                     |


<br>
<br>


## <a name="sendLightEventColorCommand">sendLightEventColorCommand</a>

LED 이벤트 설정(RGB) + Command

lightEvent 변수에는 [LightModeDrone](#LightModeDrone), [LightModeController](#LightModeController)의 value 값을 사용합니다.

brightness는 값은 0일 때 꺼지며 값이 커질수록 밝아집니다.

```py
def sendLightEventColorCommand(self, lightEvent, interval, repeat, r, g, b, commandType, option):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                                     |
|:-------------------------:|:-------------------------------------------------:|:-----------------------------------------|
| lightEvent                | UInt8                                             | LED 동작 모드                            |
| interval                  | 0 ~ 65535                                         | 내부 밝기 제어 함수 호출 주기            |
| repeat                    | 0 ~ 255                                           | 반복 횟수                                |
| r                         | 0 ~ 255                                           | Red                                      |
| g                         | 0 ~ 255                                           | Green                                    |
| b                         | 0 ~ 255                                           | Blue                                     |
| commandType               | [CommandType](03_protocol.md#CommandType)         | 명령 타입                                |
| option                    | UInt8                                             | 옵션                                     |


<br>
<br>


## <a name="sendLightEventColorCommandIr">sendLightEventColorCommandIr</a>

LED 이벤트 설정(RGB) + Command + IR

lightEvent 변수에는 [LightModeDrone](#LightModeDrone), [LightModeController](#LightModeController)의 value 값을 사용합니다.

brightness는 값은 0일 때 꺼지며 값이 커질수록 밝아집니다.

```py
def sendLightEventColorCommandIr(self, lightEvent, interval, repeat, r, g, b, commandType, option, irData):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                                     |
|:-------------------------:|:-------------------------------------------------:|:-----------------------------------------|
| lightEvent                | UInt8                                             | LED 동작 모드                            |
| interval                  | 0 ~ 65535                                         | 내부 밝기 제어 함수 호출 주기            |
| repeat                    | 0 ~ 255                                           | 반복 횟수                                |
| r                         | 0 ~ 255                                           | Red                                      |
| g                         | 0 ~ 255                                           | Green                                    |
| b                         | 0 ~ 255                                           | Blue                                     |
| commandType               | [CommandType](03_protocol.md#CommandType)         | 명령 타입                                |
| option                    | UInt8                                             | 옵션                                     |
| irData                    | 0x00000000 ~ 0xFFFFFFFF                           | 적외선으로 전송할 데이터                 |


<br>
<br>


## <a name="sendLightEventColors">sendLightEventColors</a>

LED 이벤트 설정(Palette)

lightEvent 변수에는 [LightModeDrone](#LightModeDrone), [LightModeController](#LightModeController)의 value 값을 사용합니다.

brightness는 값은 0일 때 꺼지며 값이 커질수록 밝아집니다.

```py
def sendLightEventColors(self, lightEvent, interval, repeat, colors):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                                     |
|:-------------------------:|:-------------------------------------------------:|:-----------------------------------------|
| lightEvent                | UInt8                                             | LED 동작 모드                            |
| interval                  | 0 ~ 65535                                         | 내부 밝기 제어 함수 호출 주기            |
| repeat                    | 0 ~ 255                                           | 반복 횟수                                |
| colors                    | [Colors](03_protocol.md#Colors)                   | 색상 팔레트 인덱스                       |


<br>
<br>


## <a name="sendLightEventColorsCommand">sendLightEventColorsCommand</a>

LED 이벤트 설정(Palette) + Command

lightEvent 변수에는 [LightModeDrone](#LightModeDrone), [LightModeController](#LightModeController)의 value 값을 사용합니다.

brightness는 값은 0일 때 꺼지며 값이 커질수록 밝아집니다.

```py
def sendLightEventColorsCommand(self, lightEvent, interval, repeat, colors, commandType, option):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                                     |
|:-------------------------:|:-------------------------------------------------:|:-----------------------------------------|
| lightEvent                | UInt8                                             | LED 동작 모드                            |
| interval                  | 0 ~ 65535                                         | 내부 밝기 제어 함수 호출 주기            |
| repeat                    | 0 ~ 255                                           | 반복 횟수                                |
| colors                    | [Colors](03_protocol.md#Colors)                   | 색상 팔레트 인덱스                       |
| commandType               | [CommandType](03_protocol.md#CommandType)         | 명령 타입                                |
| option                    | UInt8                                             | 옵션                                     |


<br>
<br>


## <a name="sendLightEventColorsCommandIr">sendLightEventColorsCommandIr</a>

LED 이벤트 설정(Palette) + Command + IR

lightEvent 변수에는 [LightModeDrone](#LightModeDrone), [LightModeController](#LightModeController)의 value 값을 사용합니다.

brightness는 값은 0일 때 꺼지며 값이 커질수록 밝아집니다.

```py
def sendLightEventColorsCommandIr(self, lightEvent, interval, repeat, colors, commandType, option, irData):
```

| 변수 이름                 | 형식 또는 범위                                    | 설명                                     |
|:-------------------------:|:-------------------------------------------------:|:-----------------------------------------|
| lightEvent                | UInt8                                             | LED 동작 모드                            |
| interval                  | 0 ~ 65535                                         | 내부 밝기 제어 함수 호출 주기            |
| repeat                    | 0 ~ 255                                           | 반복 횟수                                |
| colors                    | [Colors](03_protocol.md#Colors)                   | 색상 팔레트 인덱스                       |
| commandType               | [CommandType](03_protocol.md#CommandType)         | 명령 타입                                |
| option                    | UInt8                                             | 옵션                                     |
| irData                    | 0x00000000 ~ 0xFFFFFFFF                           | 적외선으로 전송할 데이터                 |

 -->

 
<br>


---

<h3><i>petrone</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [System](02_system.md)
 3. [Protocol](03_protocol.md)
 4. **Drone**
 5. [Examples - Information](examples_01_information.md)
 6. [Examples - Imu](examples_02_imu.md)
 7. [Examples - Test Flight](examples_03_test_flight.md)
 8. [Examples - Light](examples_04_light.md)

<br>

[Index](index.md)
