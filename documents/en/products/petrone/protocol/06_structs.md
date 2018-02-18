***PETRONE / BLE / Protocol / Structs***<br>
Modified : 2017.10.18

---

#### 데이터 송수신 시에 사용하는 구조체들을 소개합니다.

---

<br>

## <a name="Ack">Protocol::Ack</a>
Data that PETRONE sends in a response when it receives data. Returns the internal time of PETRONE and the type of data received. Replies most commands except Ack and Control.
```cpp
namespace Protocol
{
    struct Ack
    {
        u32  systemTime;    // receive time
        u8   dataType;      // receive datatype
    };
}
```
- dataType : [Protocol::DataType::Type](03_datatype.md#DataType)


<br>
<br>


## <a name="Request">Protocol::Request</a>
Used to request data to PETRONE.
```cpp
namespace Protocol
{
    struct Request
    {
        u8   dataType;     // request datatype
    };
}
```
- dataType : [Protocol::DataType::Type](03_datatype.md#DataType)


<br>
<br>


## <a name="Control">Protocol::Control</a>
Used to control data to PETRONE.
```cpp
namespace Protocol
{
    struct Control
    {
        s8   roll;        // Roll
        s8   pitch;       // Pitch
        s8   yaw;         // Yaw
        s8   throttle;    // Throttle
    };
}
```

Control input values are in the range :
- Drive mode used only **throttle(Forward-Backward)** and **roll**(Left-Right)


| Name     | Type | Range       | Direction        | Minus(-)         | Plus(+)    |
|:--------:|:----:|:-----------:|:----------------:|:----------------:|:----------:|
| roll     | s8   | -100 ~ 100  | Left-Right       | Left             | Right      |
| pitch    | s8   | -100 ~ 100  | Forward-Backward | Backward         | Forward    |
| yaw      | s8   | -100 ~ 100  | Turn Left-Right  | Counterclockwise | Clockwise  |
| throttle | s8   | -100 ~ 100  | Up-Down          | Down             | Up         |


<br>
<br>


## <a name="Command">Protocol::Command</a>
Send one command
```cpp
namespace Protocol
{
    struct Command
    {
        CommandBase   command;
    };
}
```
- command : [Protocol::CommandBase](05_base_structs.md#CommandBase)


<br>
<br>


## <a name="Command2">Protocol::Command2</a>
Send two command
```cpp
namespace Protocol
{
    struct Command2
    {
        CommandBase   command1;
        CommandBase   command2;
    };
}
```
- command1, command2 : [Protocol::CommandBase](05_base_structs.md#CommandBase)


<br>
<br>


## <a name="Command3">Protocol::Command3</a>
Send three command
```cpp
namespace Protocol
{
    struct Command3
    {
        CommandBase   command1;
        CommandBase   command2;
        CommandBase   command3;
    };
}
```
- command1, command2, command3 : [Protocol::CommandBase](05_base_structs.md#CommandBase)


<br>
<br>


## <a name="Address">Protocol::Address</a>
Return BLE address
```cpp
namespace Protocol
{
    struct Address
    {
        u8   address[6];
    };
}
```

<br>
<br>


## <a name="State">Protocol::State</a>
Return PETRONE state
```cpp
namespace Protocol
{
    struct State
    {
        u8          modeVehicle;        // Vehicle mode
        
        u8          modeSystem;         // System mode 
        u8          modeFlight;         // Flight mode 
        u8          modeDrive;          // Drive mode 
        
        u8          sensorOrientation;  // Sensor Orientation
        u8          coordinate;         // Headless mode 
        u8          battery;            // Drone battery(0 ~ 100)
    };
}
```
- modeVehicle : [System::ModeVehicle::Type](04_definitions.md#ModeVehicle)
- modeSystem : [System::ModeSystem::Type](04_definitions.md#ModeSystem)
- modeFlight : [System::ModeFlight::Type](04_definitions.md#ModeFlight)
- modeDrive : [System::ModeDrive::Type](04_definitions.md#ModeDrive)
- sensorOrientation : [System::SensorOrientation::Type](04_definitions.md#SensorOrientation)
- coordinate : [System::Coordinate::Type](04_definitions.md#Coordinate)


<br>
<br>


## <a name="Attitude">Protocol::Attitude</a>
Drone Attitude
```cpp
namespace Protocol
{
    struct Attitude
    {
        s16          roll;         // Roll
        s16          pitch;        // Pitch
        s16          yaw;          // Yaw
    };
}
```

The drones's attitude range of use is as follows :

| Name     | Type | Range       | Description                    |
|:--------:|:----:|:-----------:|:------------------------------:|
| roll     | s16  | -180 ~ 180  | Angle of left-right            |
| pitch    | s16  | -180 ~ 180  | Angle of forward-backward      |
| yaw      | s16  |    0 ~ 360  | Angle of gravity rotated axis  |

Sensor data value range is follows :

| Name     | Type | Range           |
|:--------:|:----:|:---------------:|
| roll     | s16  | -32768 ~ 32767  |
| pitch    | s16  | -32768 ~ 32767  |
| yaw      | s16  | -32768 ~ 32767  |


<br>
<br>


## <a name="GyroBias">Protocol::GyroBias</a>
Retruns gyro bias value.
```cpp
namespace Protocol
{
    struct GyroBias
    {
        s16          roll;         // Roll
        s16          pitch;        // Pitch
        s16          yaw;          // Yaw
    };
}
```

<br>
<br>


## <a name="TrimFlight">Protocol::TrimFlight</a>
Flight mode trim setting protocol.
```cpp
namespace Protocol
{
    struct TrimFlight
    {
        s16          roll;         // Roll
        s16          pitch;        // Pitch
        s16          yaw;          // Yaw
        s16          throttle;     // Throttle
    };
}
```

<br>
<br>


## <a name="TrimDrive">Protocol::TrimDrive</a>
Drive mode trim setting protocol.
```cpp
namespace Protocol
{
    struct TrimDrive
    {
        s16          wheel;         // Wheel
    };
}
```

<br>
<br>


## <a name="TrimAll">Protocol::TrimAll</a>
All trim setting once.
```cpp
namespace Protocol
{
    struct TrimAll
    {
        TrimFlight   flight;
        TrimDrive    drive;
    };
}
```
- flight : [Protocol::TrimFlight](#TrimFlight)
- drive : [Protocol::TrimDrive](#TrimDrive)


<br>
<br>


## <a name="CountFlight">Protocol::CountFlight</a>
Use to read the stored flight log.
```cpp
namespace Protocol
{
    struct CountFlight
    {
        u32     timeFlight;             // Flight time
        
        u16     countTakeOff;           // count of Takeoff
        u16     countLanding;           // count of Landing
        u16     countAccident;          // count of Accident
    };
}
```

<br>
<br>


## <a name="CountDrive">Protocol::CountDrive</a>
Use to read the stored drive log.
```cpp
namespace Protocol
{
    struct CountDrive
    {
        u32     timeDrive;              // Drive time
        
        u16     countAccident;          // count of Accident
    };
}
```
countAccident variable make for count of accident. But count may also increase due to the impact of uneven road surfaces during actual driving. Consider it meaningless at this time.


<br>
<br>


## <a name="IrMessage">Protocol::IrMessage</a>
Data that is used to transfer IR data or sent to an external device when IR data is receive by PETRONE
```cpp
namespace Protocol
{
    struct IrMessage
    {
        u8  direction;               // Receive direction
        u32 irData;                  // IR message
    };
}
```
- direction : [System::Direction::Type](04_definitions.md#Direction)


<br>
<br>


## <a name="ImuRawAndAngle">Protocol::ImuRawAndAngle</a>
Returns the value of the gyro sensor and the attitude value of the drone.
```cpp
namespace Protocol
{
    struct ImuRawAndAngle
    {
        s16     accX;
        s16     accY;
        s16     accZ;
        s16     gyroRoll;
        s16     gyroPitch;
        s16     gyroYaw;
        s16     angleRoll;
        s16     anglePitch;
        s16     angleYaw;
    };
}
```


<br>
<br>


## <a name="Pressure">Protocol::Pressure</a>
Retruns pressure sensor. d1 and d2 is output only MS5607. DPS310 use device return only 0.
```cpp
namespace Protocol
{
    struct Pressure
    {
        s32		d1;
        s32		d2;
        s32		temperature;
        s32		pressure;
    };
}
```
- Pressure output unit are in millimetres(mm).


<br>
<br>


## <a name="ImageFlow">Protocol::ImageFlow</a>
Image optical flow calcurated axis position
```cpp
namespace Protocol
{
    struct ImageFlow
    {
        s32		positionX;
        s32		positionY;
    };
}
```
- positionX, positionYoutput unit are in millimetres(mm).


<br>
<br>


## <a name="Button">Protocol::Button</a>
Drone button flag

```cpp
namespace Protocol
{
    struct Button
    {
        u8      button;
    };
}
```


<br>
<br>


## <a name="Motor">Protocol::Motor</a>
Motor control and check current value 
```cpp
namespace Protocol
{
    struct Motor
    {
        MotorBase motor[4];
    };
}
```
- motor : [Protocol::MotorBase::Type](05_base_structs.md#MotorBase)


<br>
<br>


## <a name="Range">Protocol::Range</a>
Range sensor data
If an additional sensor module is not installed, output only bottom value.

```cpp
namespace Protocol
{
    struct Range
    {
        u16	left;
        u16	front;
        u16	right;
        u16	rear;
        u16	top;
        u16	bottom;
    };
}
```
- All unit are in millimetres(mm).


<br>
<br>


## <a name="UpdateLookupTarget">Protocol::UpdateLookupTarget</a>
Request firmware Information.<br>
PETRONE has control MCU(Main) and communication MCU(sub).
Protocol::UpdateLookupTarget used for request target MCU's Protocol::UpdateInformation
```cpp
namespace Protocol
{
    struct UpdateLookupTarget
    {
        u32	deviceType;
    };
}
```
- deviceType : [System::DeviceType::Type](04_definitions.md#DeviceType)


<br>
<br>


## <a name="UpdateInformation">Protocol::UpdateInformation</a>
Firmware Information<br>
If PC or App send Protocol::UpdateLookupTarget, the device with the deviceType matches it,
response Protocol::UpdateInformation.
```cpp
namespace Protocol
{
    struct UpdateInformation
    {
        u8      modeUpdate;     // The progress of the update

        u32     deviceType;     // Device type
        u8      imageType;      // Firmware image type  
        u16     imageVersion;   // Firmware image version

        u8      year;           // Firmware build year
        u8      month;          // Firmware build month
        u8      day;            // Firmware build day
    };
}
```
- modeUpdate : [System::ModeUpdate::Type](04_definitions.md#ModeUpdate)
- deviceType : [System::DeviceType::Type](04_definitions.md#DeviceType)
- imageType : [System::ImageType::Type](04_definitions.md#ImageType)


<br>
<br>


## <a name="Update">Protocol::Update</a>
Firmware update.<br>
When updating the firmware, the file transfers data that is truncated to 16 bytes. There are no other responses during the Protocol::Update transfer. If a transfer failure occurs, drone sends  Protocol::UpdateLocationCorrect. When you receive the packet, you can start sending it again from the block location you specified.
```cpp
namespace Protocol
{
    struct Update
    {
        u16     indexBlock;         // Block index(16byte block index)
        u8      dataArray[16];      // data block
    };
}
```
- indexBlock : The value divided by 16 from the actual location of the file.


<br>
<br>


## <a name="UpdateLocationCorrect">Protocol::UpdateLocationCorrect</a>
Correct Firmware Update Locations.<br>
If the firmware update encounters a block that fails to transfer, send a request to send it again from indexBlockNext.
```cpp
namespace Protocol
{
    struct UpdateLocationCorrect
    {
        u16     indexBlockNext;     // indexblock number
    };
}
```
- indexBlockNext :  The value divided by 16 from the actual location of the file.


<br>

---

### PETRONE

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. [Base Structs](05_base_structs.md)
6. ***Structs***
7. [Structs - Light](07_structs_light.md)
8. [Firmware Update](08_firmware_update.md)


### PETRONE Link

1. [Intro](link/01_intro.md)
2. [DataType](link/02_datatype.md)
3. [Definitions](link/03_definitions.md)
4. [Structs](link/04_structs.md)
5. [Examples](link/05_examples.md)

<br>

[Index](index.md)

<br>

