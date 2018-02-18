**[*petrone* for python](index.md)** / **Drone**

Modified : 2018.2.12

---

<h3>Introduce drone module</h3>

---


<br>


# Drone classes


<br>


### Drone class constructor

Drone classes constructor as follows :

```py
def __init__(self, flagCheckBackground = True, flagShowErrorMessage = False, flagShowLogMessage = False, flagShowTransferData = False, flagShowReceiveData = False):
```


| Name                  | Description                           |
|:----------------------|:--------------------------------------|
| flagCheckBackground   | Check received data in background     |
| flagShowErrorMessage  | Show error message                    |
| flagShowLogMessage    | Show log message                      |
| flagShowTransferData  | Display the send data array           |
| flagShowReceiveData   | Display the receive data array        |

If Drone class constuctor does not call specify it's initial variable **flagCheckBackground** is ***True*** and all ohter value is ***False***.
If **flagCheckBackground** is ***True***, Whenever receive data, Invoke **check()** function from inner class.
If **flagCheckBackground** is ***False***, Whenever receive data, You must manualy call **check()** function to process the received data. 



<br>
<br>


### Drone class's public methods

Drone class's public methods list.

| Name                                           | Description                                                                                              |
|:-----------------------------------------------|:---------------------------------------------------------------------------------------------------------|
| isOpen()                                       | Serial port connection status return                                                                     |
| isConnected()                                  | BLE connection status return                                                                             |
| open(portName)                                 | Open serial port. If you do not specify a port name, connect to the last detected device. Return True when port is opened   |
| connect(portName, deviceName, flagSystemReset) | If the serial port is not open, open the serial port, Search for PETRONE and connect it to the device with the strongest signal. If you specify a deviceName, Connect only when the specified device is discovered. flagSystemReset is use to reset and start the first PETRONE LINK after the serial communication connection. Default value is False.    |
| close()                                        | Close serial port                                                                                        |
| makeTransferDataArray(header, data)            | Make transfer byte data array.                                                                           |
| transfer(header, data)                         | Trnasfer data(Internal call makeTransferDataArray function)                                              |
| check()                                        | Check received data. Returns DataType when Data Received                                                 |
| checkDetail()                                  | Check received data. Return header and data to tuple                                                     |
| setEventHandler(dataType, eventHandler)        | Register a custom function to call when data of a specific type is received                              |
| getHeader(dataType)                            | Returns the received header with the specified type of data                                              |
| getData(dataType)                              | Returns the received data (If does not have data, Return None.)                                          |
| getCount(dataType)                             | Returns the number of times the specified type was received (If never received data, Return 0.)          |


<br>
<br>


### Drone class data processing unit

Drone class's receive data processing unit is organized as follows 

| Name            | Description                                                                                                  |
|:----------------|:-------------------------------------------------------------------------------------------------------------|
| _receiving()    | Data receiving Thread, Save received data to buffer.                                                         |
| check()         | Read 1-byte of data stored in the buffer and pass it to the receiver. If one data block received call *_handler()*, data parsing and return the datatype. Returns **DataType.None_** if no data received. |
| _handler()      | Save header internally. Data parsing and saved internal class. If event handler is registered call function. |


<br>
<br>


# Function list


<br>


## Common

| Name                                                              | Description                                   |
|:------------------------------------------------------------------|:----------------------------------------------|
| [sendPing](#sendPing)                                             | Send Ping                                     |
| [sendRequest](#sendRequest)                                       | Send Request                                  |


<br>


## Control

| Name                                                              | Description                                   |
|:------------------------------------------------------------------|:----------------------------------------------|
| [sendTakeOff](#sendTakeOff)                                       | Takeoff                                       |
| [sendLanding](#sendLanding)                                       | Landing                                       |
| [sendStop](#sendStop)                                             | Stop                                          |
| [sendControl](#sendControl)                                       | Send Flight control                           |
| [sendControlWhile](#sendControlWhile)                             | Send Flight control during the specified time |
| [sendControlDrive](#sendControlDrive)                             | Send Drive control                            |
| [sendControlDriveWhile](#sendControlDriveWhile)                   | Send Drive control during the specified time  |


<br>


## Setting

| Name                                                              | Description                                   |
|:------------------------------------------------------------------|:----------------------------------------------|
| [sendCommand](#sendCommand)                                       | Send command                                  |
| [sendModeVehicle](#sendModeVehicle)                               | Flight/Drive mode change                      |
| [sendHeadless](#sendHeadless)                                     | Headless mode setting                         |
| [sendTrim](#sendTrim)                                             | Trim setting                                  |
| [sendTrimFlight](#sendTrimFlight)                                 | Flight Trim setting                           |
| [sendTrimDrive](#sendTrimDrive)                                   | Drive Trim setting                            |
| [sendFlightEvent](#sendFlightEvent)                               | Execute flight event                          |
| [sendDriveEvent](#sendDriveEvent)                                 | Execute drive event                           |
| [sendClearTrim](#sendClearTrim)                                   | Clear Trim data                               |
| [sendClearGyroBias](#sendClearGyroBias)                           | Clear Gyro bias                               |
| [sendUpdateLookupTarget](#sendUpdateLookupTarget)                 | Check firmware information                    |

<br>


## Motor

| Name                                                              | Description                                   |
|:------------------------------------------------------------------|:----------------------------------------------|
| [sendMotor](#sendMotor)                                           | Control motor                            

<br>


## IR

| Name                                                              | Description                                   |
|:------------------------------------------------------------------|:----------------------------------------------|
| [sendIrMessage](#sendIrMessage)                                   | Send IR Message                               |

<br>


## LED

| Name                                                              | Description                                   |
|:------------------------------------------------------------------|:----------------------------------------------|
| [sendLightMode](#sendLightMode)                                   | Mode setting(Pallet)                          |
| [sendLightModeCommand](#sendLightModeCommand)                     | Mode setting(Pallet), Command                 |
| [sendLightModeCommandIr](#sendLightModeCommandIr)                 | Mode setting(Pallet), Command, IR             |
| [sendLightModeColor](#sendLightModeColor)                         | Mode setting(RGB)                             |
| [sendLightEvent](#sendLightEvent)                                 | Event setting(Pallet)                         |
| [sendLightEventCommand](#sendLightEventCommand)                   | Event setting(Pallet), Command                |
| [sendLightEventCommandIr](#sendLightEventCommandIr)               | Event setting(Pallet), Command, IR            |
| [sendLightEventColor](#sendLightEventColor)                       | Event setting(RGB)                            |

<br>


## LINK

| Name                                                              | Description                                   |
|:------------------------------------------------------------------|:----------------------------------------------|
| [sendLinkModeBroadcast](#sendLinkModeBroadcast)                   | LINK Broadcast mode change                    |
| [sendLinkSystemReset](#sendLinkSystemReset)                       | LINK reset                                    |
| [sendLinkDiscoverStart](#sendLinkDiscoverStart)                   | PETRONE scan start                            |
| [sendLinkDiscoverStop](#sendLinkDiscoverStop)                     | PETRONE scan stop                             |
| [sendLinkConnect](#sendLinkConnect)                               | PETRONE connect                               |
| [sendLinkDisconnect](#sendLinkDisconnect)                         | PETRONE disconnect                            |
| [sendLinkRssiPollingStart](#sendLinkRssiPollingStart)             | RSSI polling start                            |
| [sendLinkRssiPollingStop](#sendLinkRssiPollingStop)               | RSSI polling stop                             |

<br>
<br>


# Function declaration.


<br>
<br>


## <a name="sendPing">sendPing</a>

Send ping

Check drone connection status. Response is ack.

```py
def sendPing(self):
```


<br>
<br>


## <a name="sendRequest">sendRequest</a>

Request data

For request data.

```py
def sendRequest(self, dataType):
```

| Variable name            | Type and Range                          | Description                  |
|:------------------------:|:---------------------------------------:|:-----------------------------|
| dataType                 | [DataType](#DataType)                   | data type                    |


<br>
<br>


## <a name="sendTakeOff">sendTakeOff</a>

TakeOff

This function work only flight mode. ( In Ready state )

```py
def sendTakeOff(self):
```


<br>
<br>


## <a name="sendLanding">sendLanding</a>

Landing

This function work only flight mode. ( In Flight state )

```py
def sendLanding(self):
```



<br>
<br>


## <a name="sendStop">sendStop</a>

Stop

Used to force stop of drone action.

```py
def sendStop(self):
```


<br>
<br>


## <a name="sendControl">sendControl</a>

Flight control

Can be used for both flight and drive mode.

```py
def sendControl(self, roll, pitch, yaw, throttle):
```

| Variable name            | Type and Range                   | Description            |
|:------------------------:|:--------------------------------:|:-----------------------|
| roll                     | -100 ~ 100                       | Roll                   |
| pitch                    | -100 ~ 100                       | Pitch                  |
| yaw                      | -100 ~ 100                       | Yaw                    |
| throttle                 | -100 ~ 100                       | Throttle               |


<br>
<br>


## <a name="sendControlWhile">sendControlWhile</a>

Flight control

Can be used for both flight and drive mode.
Sends the control commands for the ms specified in timeMs.

```py
def sendControlWhile(self, roll, pitch, yaw, throttle, timeMs):
```

| Variable name             | Type and Range                   | Description            |
|:-------------------------:|:--------------------------------:|:-----------------------|
| roll                      | -100 ~ 100                       | Roll                   |
| pitch                     | -100 ~ 100                       | Pitch                  |
| yaw                       | -100 ~ 100                       | Yaw                    |
| throttle                  | -100 ~ 100                       | Throttle               |
| timeMs                    | 0 ~ 1,000,000                    | Work time(ms)          |


<br>
<br>


## <a name="sendControlDrive">sendControlDrive</a>

Drive control

This function work only drive mode.

```py
def sendControlDrive(self, wheel, accel):
```

| Variable name             | Type and Range                   | Description            |
|:-------------------------:|:--------------------------------:|:-----------------------|
| wheel                     | -100 ~ 100                       | Wheel                  |
| accel                     | -100 ~ 100                       | Accel                  |


<br>
<br>


## <a name="sendControlDriveWhile">sendControlDriveWhile</a>

Drive control

This function work only drive mode.
Sends the control commands for the ms specified in timeMs.

```py
def sendControlDriveWhile(self, wheel, accel, timeMs):
```

| Variable name             | Type and Range                   | Description            |
|:-------------------------:|:--------------------------------:|:-----------------------|
| wheel                     | -100 ~ 100                       | Wheel                  |
| accel                     | -100 ~ 100                       | Accel                  |
| timeMs                    | 0 ~ 1,000,000                    | Work time(ms)          |


<br>
<br>


## <a name="sendCommand">sendCommand</a>

Send command

Send drone command.

The option must have a value or a enumerate value for each type.

```py
def sendCommand(self, commandType, option = 0):
```

| Variable name  | Type and Range                                   | Description                  |
|:--------------:|:------------------------------------------------:|:-----------------------------|
| commandType    | [CommandType](03_protocol.md#CommandType)        | Command type                 |
| option         | [ModeVehicle](02_system.md#ModeVehicle)          | Option                       |
|                | [FlightEvent](02_system.md#FlightEvent)          |                              |
|                | [DriveEvent](02_system.md#DriveEvent)            |                              |
|                | [Headless](02_system.md#Headless)                |                              |
|                | [Trim](02_system.md#Trim)                        |                              |
|                | UInt8                                            |                              |


<br>
<br>


## <a name="sendModeVehicle">sendModeVehicle</a>

Vehicle mode setting

You can change the drone to flight or drive mode.

```py
def sendModeVehicle(self, modeVehicle):
```

| Variable name           | Type and Range                               | Description             |
|:-----------------------:|:--------------------------------------------:|:------------------------|
| modeVehicle             | [ModeVehicle](02_system.md#ModeVehicle)      | Vehicle mode            |


<br>
<br>


## <a name="sendHeadless">sendHeadless</a>

Headless mode setting

```py
def sendHeadless(self, headless):
```

| Variable name             | Type and Range                                    | Description                 |
|:-------------------------:|:-------------------------------------------------:|:----------------------------|
| headless                  | [Headless](02_system.md#Headless)                 | Headless mode               |


<br>
<br>


## <a name="sendTrim">sendTrim</a>

Trim setting

```py
def sendTrim(self, trim):
```

| Variable name             | Type and Range                                    | Description                 |
|:-------------------------:|:-------------------------------------------------:|:----------------------------|
| trim                      | [Trim](02_system.md#Trim)                         | Trim setting                |


<br>
<br>


## <a name="sendTrimFlight">sendTrimFlight</a>

Flight Trim setting

```py
def sendTrimFlight(self, roll, pitch, yaw, throttle):
```

| Variable name             | Type and Range                                    | Description                 |
|:-------------------------:|:-------------------------------------------------:|:----------------------------|
| roll                      | -200 ~ 200                                        | Roll                        |
| pitch                     | -200 ~ 200                                        | Pitch                       |
| yaw                       | -200 ~ 200                                        | Yaw                         |
| throttle                  | -200 ~ 200                                        | Throttle                    |


<br>
<br>


## <a name="sendTrimDrive">sendTrimDrive</a>

Drive Trim setting

```py
def sendTrimDrive(self, wheel):
```

| Variable name             | Type and Range                                    | Description                 |
|:-------------------------:|:-------------------------------------------------:|:----------------------------|
| wheel                     | -200 ~ 200                                        | Wheel                       |


<br>
<br>


## <a name="sendFlightEvent">sendFlightEvent</a>

Send Flight event

```py
def sendFlightEvent(self, flightEvent):
```

| Variable name             | Type and Range                                    | Description                 |
|:-------------------------:|:-------------------------------------------------:|:----------------------------|
| flightEvent               | [FlightEvent](02_system.md#FlightEvent)           | Flight event                |


<br>
<br>


## <a name="sendDriveEvent">sendDriveEvent</a>

Send Drive event

```py
def sendDriveEvent(self, driveEvent):
```

| Variable name             | Type and Range                                    | Description                 |
|:-------------------------:|:-------------------------------------------------:|:----------------------------|
| driveEvent                | [DriveEvent](02_system.md#DriveEvent)             | Drive event                 |


<br>
<br>


## <a name="sendClearTrim">sendClearTrim</a>

Clear Flight and Drive Trim

```py
def sendClearTrim(self):
```


<br>
<br>


## <a name="sendClearGyroBias">sendClearGyroBias</a>

Clear Accel and Gyro Bias

```py
def sendClearGyroBias(self):
```


<br>
<br>


## <a name="sendMotor">sendMotor</a>

Rotate the 4 motors in a predefined direction

```py
def sendMotor(self, motor0, motor1, motor2, motor3):
```

| Variable name             | Type and Range                                    | Description                  |
|:-------------------------:|:-------------------------------------------------:|:-----------------------------|
| motor0                    | 0 ~ 4096                                          | Front left moter speed       |
| motor1                    | 0 ~ 4096                                          | Front right moter speed      |
| motor2                    | 0 ~ 4096                                          | Rear right moter speed       |
| motor3                    | 0 ~ 4096                                          | Rear left moter speed        |


<br>
<br>


## <a name="sendIrMessage">sendIrMessage</a>

Send IR Message

```py
def sendIrMessage(self, value):
```

| Variable name             | Type and Range                                    | Description                  |
|:-------------------------:|:-------------------------------------------------:|:-----------------------------|
| value                     | 0x00000000 ~ 0xFFFFFFFF                           | IR Message value        |


<br>
<br>
<br>


---

<h3><i>petrone</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [System](02_system.md)
 3. [Protocol](03_protocol.md)
 4. **Drone**
 5. [Examples - Information](examples_01_information.md)

<br>

[Index](index.md)
