**[PETRONE_V2](index.md)** / **Protocol** / **Structs**

Modified : 2018.02.13

---

#### Introduce data structures used to transmission.

---


<br>


## <a name="Protocol_Header">Protocol::Header</a>

Header

Data transmission header.

```cpp
namespace Protocol
{
    struct Header
    {
        u8      dataType;       // Data Type
        u8      length;         // Data length
        u8      from;           // Transfer Device Type
        u8      to;             // Receiver Device Type
    };
}
```

| Variable Name | Type      | Range  | Size     | Description    |
|:---------:|:--------------------------------------------------------------------:|:---------:|:--------:|:-------------------------|
| dataType  | [Protocol::DataType::Type](03_datatype.md#Protocol_DataType)         | -         | 1 Byte   | Data Type            |
| length    | uint8_t                                                              | 0 ~ 255   | 1 Byte   | Data length            |
| from      | [Protocol::DeviceType::Type](04_definitions.md#Protocol_DeviceType)  | -         | 1 Byte   | Transfer Device Type   |
| to        | [Protocol::DeviceType::Type](04_definitions.md#Protocol_DeviceType)  | -         | 1 Byte   | Receiver Device Type   |


<br>
<br>


## <a name="Protocol_Ping">Protocol::Ping</a>

Ping

Used to check the status of the connection with other devices. The relative device sends an Ack response to the ping.

```cpp
namespace Protocol
{
    struct Ping
    {
        u64     systemTime;   // Ping System time
    };
}
```

| Variable Name | Type      | Range  | Size     | Description    |
|:-----------:|:-----------:|:-----:|:--------:|:---------------|
| systemTime  | uint64_t    | -     | 8 Byte   | System time     |


<br>
<br>


## <a name="Protocol_Ack">Protocol::Ack</a>

Ack

If a data request is sent to drone, the corresponding data is responded. If the data is not ready, Ack is in response.

```cpp
namespace Protocol
{
    struct Ack
    {
        u64     systemTime;     // System time
        u8      dataType;       // Received data type 
        u16     crc16;          // Received data crc16
    };
}
```

| Variable Name | Type      | Range  | Size     | Description    |
|:------------:|:------------------------------------------------------------:|:------:|:--------:|:------------------------------------|
| systemTime   | uint64_t                                                     | -      | 8 Byte   | System time                       |
| dataType     | [Protocol::DataType::Type](03_datatype.md#Protocol_DataType) | -      | 1 Byte   | Received data type                |
| crc16        | uint16_t                                                     | -      | 2 Byte   | Received data crc16  |


<br>
<br>


## <a name="Protocol_Error">Protocol::Error</a>

Error

If there is a problem with the drone, the error structure is transmitted via RF once every 600ms.
errorFlagsForSensor and errorFlagsForState is combine flags corresponding to each value to indicate multiple errors occurring simultaneously.
If the problem is completely eliminated, reset the error flag to zero to stop sending it after five additional deliveries.

```cpp
namespace Protocol
{
    struct Error
    {
        u64     systemTime;             // Error message system time
        u32     errorFlagsForSensor;    // Sensor error flags
        u32     errorFlagsForState;     // State error flags
    };
}
```

| Variable Name | Type      | Range  | Size     | Description    |
|:--------------------:|:-------------------------------------------------------------------:|:------:|:--------:|:------------------------|
| systemTime           | uint64_t                                                            | -      | 8 Byte   | Error message system time             |
| errorFlagsForSensor  | [ErrorFlagsForSensor::Type](04_definitions.md#ErrorFlagsForSensor)  | -      | 4 Byte   | Sensor error flags   |
| errorFlagsForState   | [ErrorFlagsForState::Type](04_definitions.md#ErrorFlagsForState)    | -      | 4 Byte   | State error flags  |


<br>
<br>


## <a name="Protocol_Request">Protocol::Request</a>

Request

Request data to drone or controller

```cpp
namespace Protocol
{
    struct Request
    {
        u8      dataType;          // Request data type
    };
}
```

| Variable Name | Type      | Range  | Size     | Description    |
|:-------------:|:-------------------------------------------------------------:|:-----:|:--------:|:----------------------|
| dataType      | [Protocol::DataType::Type](03_datatype.md#Protocol_DataType)  | -     | 1 Byte   | Request data type    |


<br>
<br>


## <a name="Protocol_Information">Protocol::Information</a>

Firmware information

```cpp
namespace Protocol
{
    struct Information
    {
        u8      modeUpdate;     // The progress of the update

        u32     deviceType;     // Device type
        u32     imageVersion;   // Firmware image version

        u16     year;           // Firmware build year
        u8      month;          // Firmware build month
        u8      day;            // Firmware build day
    };
}
```

| Variable Name | Type      | Range  | Size     | Description    |
|:-------------:|:-------------------------------------------------------------------:|:----:|:--------:|:--------------------|
| modeUpdate    | [Mode::Update::Type](04_definitions.md#Mode_Update)                 | -    | 1 Byte   | The progress of the update  |
| deviceType    | [Protocol::DeviceType::Type](04_definitions.md#Protocol_DeviceType) | -    | 1 Byte   | Device type       |
| version       | [Protocol::Version](#Protocol_Version)                              | -    | 4 Byte   | Firmware image version      |
| year          | uint16_t                                                            | -    | 2 Byte   | Firmware build year     |
| month         | uint8_t                                                             | -    | 1 Byte   | Firmware build month      |
| day           | uint8_t                                                             | -    | 1 Byte   | Firmware build day     |


<br>
<br>


## <a name="Protocol_Version">Protocol::Version</a>

Firmware version

When comparing versions, the order of placement of variables in the stream was set in reverse order to compare v values.

```cpp
namespace Protocol
{
    union Version
    {
        struct
        {
            u16                     build:14;   // Build Number(0~16383)
            DevelopmentStage::Type  stage:2;    // Development stage(0~3)
            u8                      minor;      // Minor Number
            u8                      major;      // Major Number
        };

        u32 v;
    };
}
```

| Variable Name | Type      | Range  | Size     | Description    |
|:----------:|:--------------------------------------------------------------:|:----------:|:--------:|:-------------|
| build      | uint16_t                                                       | 0 ~ 16383  | 14 bit   | Build Number(0~16383)   |
| stage      | [Protocol::DevelopmentStage::Type](#Protocol_DevelopmentStage) | -          | 2 bit    | Development stage(0~3) |
| minor      | uint8_t                                                        | 0 ~ 255    | 1 Byte   | Minor Number  |
| major      | uint8_t                                                        | 0 ~ 255    | 1 Byte   | Major Number   |
| v          | uint32_t                                                       | -          | 4 Byte   | Uniting build, stage, minor, major |


<br>
<br>


## <a name="Protocol_DevelopmentStage">Protocol::DevelopmentStage::Type</a>

Firmware development stage

```cpp
namespace Protocol
{
    namespace DevelopmentStage
    {
        enum Type
        {
            Alpha,
            Beta,
            ReleaseCandidate,
            Release
        };
    }
}
```


<br>
<br>


## <a name="Control_Double8">Control::Double8</a>

Drive control

Ignore sending this command when in drone mode.

```cpp
namespace Control
{
    struct Double8
    {
        s8      wheel;      // wheel
        s8      accel;      // accel
    };
}
```

Control::Double8 The range of the input values is as follows

| Variable Name | Type      | Range  | Size     | Description    | Minus(-) | Plus(+)    |
|:----------:|:------:|:----------:|:--------:|:-------------|:----------:|:-------------:|
| wheel      | int8_t | -100 ~ 100 | 1 Byte   | Left-Right    | Left     | Right        |
| accel      | int8_t | -100 ~ 100 | 1 Byte   | Forward-Backward | Forward | Backward          |


<br>
<br>


## <a name="Control_Quad8">Control::Quad8</a>

Used to control PETRONE.

- Drive mode used only **throttle(Forward-Backward)** and **roll**(Left-Right)

```cpp
namespace Control
{
    struct Quad8
    {
        s8      roll;       // roll
        s8      pitch;      // pitch
        s8      yaw;        // yaw
        s8      throttle;   // throttle
    };
}
```

| Variable Name | Type      | Range  | Size     | Description    | Minus(-) | Plus(+)    |
|:---------:|:--------:|:------------:|:--------:|:-----------|:----------:|:-------------:|
| roll      | int8_t   | -100 ~ 100   | 1 Byte   | Left-Right | Left       | Right          |
| pitch     | int8_t   | -100 ~ 100   | 1 Byte   | Forward-Backward | Backward       | Forward  |
| yaw       | int8_t   | -100 ~ 100   | 1 Byte   | Turn Left-Right | Counterclockwise     | Clockwise  |
| throttle  | int8_t   | -100 ~ 100   | 1 Byte   | Up-Down         | 하Down강       | Up       |


<br>
<br>


## <a name="Protocol_Command">Protocol::Command</a>

Send one command

```cpp
namespace Protocol
{
    struct Command
    {
        u8      commandType;   // Command type
        u8      option;        // Command options
    };
}
```

| Variable Name | Type      | Range  | Size     | Description    |
|:-----------:|:-----------------------------------------------------------------------:|:-------:|:--------:|:-------------|
| commandType | [Protocol::CommandType::Type](04_definitions.md#Protocol_CommandType)   | -       | 1 Byte   | Command Type    |
| option      | [Mode::Vehicle::Type](04_definitions.md#Mode_Vehicle)                   | -       | 1 Byte   | Option         |
|             | [System::FlightEvent::Type](04_definitions.md#FlightEvent)              | -       |          |              |
|             | [System::DriveEvent::Type](04_definitions.md#DriveEvent)                | -       |          |              |
|             | [Coordinate::Type](04_definitions.md#Coordinate)                        | -       |          |              |
|             | [System::Trim::Type](04_definitions.md#Trim)                            | -       |          |              |
|             | uint8_t                                                                 | -       |          |              |


<br>
<br>


## <a name="Protocol_Address">Protocol::Address</a>

Device Address

```cpp
namespace Protocol
{
    struct Address
    {
        u8   address[16];
    };
}
```

| Variable Name | Type      | Range  | Size     | Description    |
|:----------:|:---------------:|:-----:|:--------:|:-------------|
| address    | uint8_t Array   | -     | 16 Byte  | Device Address    |


<br>
<br>


## <a name="Protocol_State">Protocol::State</a>

Current State

```cpp
namespace Protocol
{
    struct State
    {
        u8      modeVehicle;        // Vehicle mode
        
        u8      modeSystem;         // System mode
        u8      modeFlight;         // Flight mode
        u8      modeDrive;          // Drive mode
        
        u8      sensorOrientation;  // sensor orientation
        u8      coordinate;         // vehicle coordinates
        u8      battery;            // Battery(0 ~ 100%)
    };
}
```

| Variable Name | Type      | Range  | Size     | Description    |
|:-----------------:|:--------------------------------------------------------------:|:--------:|:--------:|:-----------------------|
| modeVehicle       | [Mode::Vehicle::Type](04_definitions.md#Mode_Vehicle)          | -        | 1 Byte   | Vehicle operating mode      |
| modeSystem        | [Mode::System::Type](04_definitions.md#Mode_System)            | -        | 1 Byte   | System operating mode       |
| modeFlight        | [Mode::Flight::Type](04_definitions.md#Mode_Flight)            | -        | 1 Byte   | Flight control mode  |
| modeDrive         | [Mode::Drive::Type](04_definitions.md#Mode_Drive)              | -        | 1 Byte   | Drive control mode  |
| sensorOrientation | [SensorOrientation::Type](04_definitions.md#SensorOrientation) | -        | 1 Byte   | Sensor orientation |
| coordinate        | [Coordinate::Type](04_definitions.md#Coordinate)               | -        | 1 Byte   | Coordinate setting state   |
| battery           | uint8_t                                                        | 0 ~ 100  | 1 Byte   | Drone battery remain  |


<br>
<br>


## <a name="Protocol_Attitude">Protocol::Attitude</a>

Vehicle attitude

```cpp
namespace Protocol
{
    struct Attitude
    {
        s16     roll;         // Roll
        s16     pitch;        // Pitch
        s16     yaw;          // Yaw
    };
}
```

| Variable Name | Type      | Range  | Size     | Description    
|:----------:|:----------:|:-----------------:|:--------:|:-----------|
| roll       | int16_t    | -32,768 ~ 32,767  | 2 Byte   | Roll       |
| pitch      | int16_t    | -32,768 ~ 32,767  | 2 Byte   | Pitch      |
| yaw        | int16_t    | -32,768 ~ 32,767  | 2 Byte   | Yaw        |


When checking the position of the drones :

| Variable Name | Type      | Range  | Description     |
|:--------:|:--------:|:-----------:|:-------------------:|
| roll     | int16_t  |  -90 ~  90  | Angle of roll    |
| pitch    | int16_t  |  -90 ~  90  | Angle of pitch |
| yaw      | int16_t  | -180 ~ 180  | Angle of yaw   |


<br>
<br>


## <a name="Protocol_AccelBias">Protocol::AccelBias</a>

Accelometer bias

```cpp
namespace Protocol
{
    struct AccelBias
    {
        s16     x;         // X
        s16     y;         // Y
        s16     z;         // Z
    };
}
```

| Variable Name | Type      | Range  | Size     | Description    |
|:----------:|:----------:|:-----------------:|:--------:|:-----------|
| x          | int16_t    | -32,768 ~ 32,767  | 2 Byte   | X          |
| y          | int16_t    | -32,768 ~ 32,767  | 2 Byte   | Y          |
| z          | int16_t    | -32,768 ~ 32,767  | 2 Byte   | Z          |


<br>
<br>


## <a name="Protocol_GyroBias">Protocol::GyroBias</a>

Gyro bias

```cpp
namespace Protocol
{
    struct GyroBias
    {
        s16     roll;         // Roll
        s16     pitch;        // Pitch
        s16     yaw;          // Yaw
    };
}
```

| Variable Name | Type      | Range  | Size     | Description    |
|:----------:|:----------:|:-----------------:|:--------:|:-----------|
| roll       | int16_t    | -32,768 ~ 32,767  | 2 Byte   | Roll       |
| pitch      | int16_t    | -32,768 ~ 32,767  | 2 Byte   | Pitch      |
| yaw        | int16_t    | -32,768 ~ 32,767  | 2 Byte   | Yaw        |


<br>
<br>


## <a name="Protocol_TrimFlight">Protocol::TrimFlight</a>

Flight Trim

```cpp
namespace Protocol
{
    struct TrimFlight
    {
        s16     roll;         // Roll
        s16     pitch;        // Pitch
        s16     yaw;          // Yaw
        s16     throttle;     // Throttle
    };
}
```

| Variable Name | Type      | Range  | Size     | Description    |
|:---------:|:--------:|:------------:|:--------:|:-----------|
| roll      | int16_t  | -200 ~ 200   | 2 Byte   | Roll       |
| pitch     | int16_t  | -200 ~ 200   | 2 Byte   | Pitch      |
| yaw       | int16_t  | -200 ~ 200   | 2 Byte   | Yaw        |
| throttle  | int16_t  | -200 ~ 200   | 2 Byte   | Throttle   |


<br>
<br>


## <a name="Protocol_TrimDrive">Protocol::TrimDrive</a>

Drive Trim

```cpp
namespace Protocol
{
    struct TrimDrive
    {
        s16     wheel;         // Wheel
        s16     accel;         // Accel
    };
}
```


| Variable Name | Type     | Range      | Size    | Description |
|:---------:|:--------:|:------------:|:--------:|:--------|
| wheel     | int16_t  | -200 ~ 200   | 2 Byte   | Wheel   |
| accel     | int16_t  | -200 ~ 200   | 2 Byte   | Accel   |


<br>
<br>


## <a name="Protocol_TrimAll">Protocol::TrimAll</a>

Flight and Drive Trim

```cpp
namespace Protocol
{
    struct TrimAll
    {
        TrimFlight  flight;
        TrimDrive   drive;
    };
}
```

| Variable Name | Type                                          | Range      | Size    | Description |
|:---------:|:---------------------------------------------:|:------------:|:--------:|:-----------|
| flight    | [Protocol::TrimFlight](#Protocol_TrimFlight)  | -200 ~ 200   | 2 Byte   | 비행 Trim  |
| drive     | [Protocol::TrimDrive](#Protocol_TrimDrive)    | -200 ~ 200   | 2 Byte   | 주행 Trim  |


<br>
<br>


## <a name="Protocol_CountFlight">Protocol::CountFlight</a>

count of flight log

Use to read the stored values associated with the flight mode.

```cpp
namespace Protocol
{
    struct CountFlight
    {
        u64     timeFlight;             // flight time
        
        u16     countTakeOff;           // count of takeoff
        u16     countLanding;           // count of landing
        u16     countAccident;          // count of accident
    };
}
```
| Variable Name | Type  | Range      | Size    | Description |
|:----------------:|:----------:|:----------:|:--------:|:-----------------|
| timeFlight       | uint64_t   | -          | 8 Byte   | flight time(ms)    |
| countTakeOff     | uint16_t   | 0 ~ 65535  | 2 Byte   | count of takeoff |
| countLanding     | uint16_t   | 0 ~ 65535  | 2 Byte   | count of landing |
| countAccident    | uint16_t   | 0 ~ 65535  | 2 Byte   | count of accident |


<br>
<br>


## <a name="Protocol_CountDrive">Protocol::CountDrive</a>

count of drive log

Use to read the stored values associated with the drive mode.

countAccident variable make for count of accident. But count may also increase due to the impact of uneven road surfaces during actual driving. Consider it meaningless at this time.

```cpp
namespace Protocol
{
    struct CountDrive
    {
        u64     timeDrive;              // drive time
        
        u16     countAccident;          // count of accident
    };
}
```
| Variable Name | Type  | Range      | Size    | Description |
|:-------------:|:----------:|:-------------:|:--------:|:---------------|
| timeDrive     | uint64_t   | -             | 8 Byte   | drive time(ms)  |
| countAccident | uint16_t   | 0 ~ 65,535    | 2 Byte   | count of accident |


<br>
<br>


## <a name="Protocol_IrMessage">Protocol::IrMessage</a>

IR Message send/recv

Data that is used to transfer IR data or sent to an external device when IR data is receive by PETRONE
IR sensor is installed on the front and rear of the drone and uses the direction to distinguish data entering each direction.

```cpp
namespace Protocol
{
    struct IrMessage
    {
        u8      direction;               // Data recv direction
        u32     irData;                  // IR Message
    };
}
```

| Variable Name | Type  | Range      | Size    | Description |
|:---------:|:------------------------------------------------------:|:-----------------------:|:------:|:-----------------|
| direction | [System::Direction::Type](04_definitions.md#Direction) | -                       | 1 Byte | IR recieve direction|
| irData    | uint32_t                                               | 0x00000000 ~ 0xFFFFFFFF | 4 Byte | data           |


<br>
<br>


## <a name="Protocol_Imu">Protocol::Imu</a>

IMU sensor data and drone attitude

```cpp
namespace Protocol
{
    struct Imu
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

| Variable Name | Type  | Range      | Size    | Description |
|:----------:|:--------:|:-----------------:|:--------:|:---------------|
| accelX     | Int16    | -32,768 ~ 32,767  | 2 Byte   | accelometer X |
| accelY     | Int16    | -32,768 ~ 32,767  | 2 Byte   | accelometer Y |
| accelZ     | Int16    | -32,768 ~ 32,767  | 2 Byte   | accelometer Z |
| gyroRoll   | Int16    | -32,768 ~ 32,767  | 2 Byte   | gyro Roll    |
| gyroPitch  | Int16    | -32,768 ~ 32,767  | 2 Byte   | gyro Pitch   |
| gyroYaw    | Int16    | -32,768 ~ 32,767  | 2 Byte   | gyro Yaw     |
| angleRoll  | Int16    | -32,768 ~ 32,767  | 2 Byte   | angle of Roll |
| anglePitch | Int16    | -32,768 ~ 32,767  | 2 Byte   | angle of Pitch |
| angleYaw   | Int16    | -32,768 ~ 32,767  | 2 Byte   | angle of Yaw |


<br>
<br>


## <a name="Protocol_Battery">Protocol::Battery</a>

Battery

```cpp
namespace Protocol
{
    struct Battery
    {
        f32     gradient;
        f32     yIntercept;
        f32     adjustGradient;
        f32     adjustYIntercept;
        u8      flagBatteryCalibration;

        s16     batteryRaw;
        f32     batteryPercent;

        f32     voltage;
    };
}
```

| Variable Name | Type  | Range      | Size    | Description |
|:-----------------------:|:--------:|:------------:|:--------:|:------------------------------------|
| gradient                | float    | -            | 4 Byte   | gradient                              |
| yIntercept              | float    | -            | 4 Byte   | Y Intercept                              |
| adjustGradient          | float    | -            | 4 Byte   | adjust Gradient                       |
| adjustYIntercept        | float    | -            | 4 Byte   | adjust Y Intercept     |
| flagBatteryCalibration  | uint8_t  | 0 / 1        | 1 Byte   | flag of Battery calibration complete |
| batteryRaw              | uint16_t | 0 ~ 4096     | 2 Byte   | battery ADC Raw value  |
| batteryPercent          | float    | 0 ~ 100.0    | 4 Byte   | battery % value |
| voltage                 | float    | 0 ~ 4.5      | 4 Byte   | battery power to voltage conversion value |


<br>
<br>


## <a name="Protocol_Pressure">Protocol::Pressure</a>

Pressure sensor

```cpp
namespace Protocol
{
    struct Pressure
    {
        f32     temperature;
        f32     pressure;
    };
}
```

| Variable Name | Type  | Range      | Size    | Description |
|:-----------:|:--------:|:----:|:--------:|:--------------------------------|
| temperature | float    | -    | 4 Byte   | temperature(℃)                        |
| pressure    | float    | -    | 4 Byte   | The conversion of pressure to sea level(m)  |


<br>
<br>


## <a name="Protocol_ImageFlow">Protocol::ImageFlow</a>

ImageFlow

Image optical flow calcurated axis position

```cpp
namespace Protocol
{
    struct ImageFlow
    {
        f32     positionX;
        f32     positionY;
    };
}
```

| Variable Name | Type  | Range      | Size    | Description |
|:----------:|:---------:|:-----:|:--------:|:--------|
| positionX  | float     | -     | 4 Byte   | X axis(m)  |
| positionY  | float     | -     | 4 Byte   | Y axis(m)  |


<br>
<br>


## <a name="Protocol_Range">Protocol::Range</a>

Range sensor

If an additional sensor module is not installed, only the bottom values are output.
The maximum measure range for distance is 0.04m to 2.0m

```cpp
namespace Protocol
{
    struct Range
    {
        f32     left;
        f32     front;
        f32     right;
        f32     rear;
        f32     top;
        f32     bottom;
    };
}
```

| Variable Name | Type  | Range      | Size    | Description |
|:---------:|:----------:|:-------:|:--------:|:---------|
| left      | Float32    | -       | 4 Byte   | left(m)  |
| front     | Float32    | -       | 4 Byte   | front(m)  |
| right     | Float32    | -       | 4 Byte   | right(m)  |
| rear      | Float32    | -       | 4 Byte   | rear(m)  |
| top       | Float32    | -       | 4 Byte   | top(m)    |
| bottom    | Float32    | -       | 4 Byte   | bottom(m)  |


<br>
<br>


## <a name="Protocol_Motor">Protocol::Motor</a>

Motor

Motor control and check current value 

```cpp
namespace Protocol
{
    struct Motor
    {
        u8      rotation;
        s16     value;
    };
}
```

| Variable Name | Type  | Range      | Size    | Description |
|:----------:|:------------------------------------------:|:---------:|:--------:|:----------|
| rotation   | [Rotation::Type](04_definitions.md#Rotation)  | -         | 1 Byte   | rotate direction |
| value      | uint16_t                                   | 0 ~ 4096  | 2 Byte   | rotate speed |


<br>
<br>


## <a name="Protocol_MotorSingle">Protocol::MotorSingle</a>

Single motor control

Used to operate one motor or check current inputs to the motor.

```cpp
namespace Protocol
{
    struct MotorSingle
    {
        u8      target;
        u8      rotation;
        s16     value;
    };
}
```

| Variable Name | Type  | Range      | Size    | Description |
|:----------:|:--------------------------------------------------:|:---------:|:--------:|:----------------|
| target     | [Motor::Part::Type](04_definitions.md#Motor_Part)  | 0 ~ 3     | 1 Byte   | target motor part |
| rotation   | [Rotation::Type](04_definitions.md#Rotation)       | -         | 1 Byte   | rotate direction |
| value      | uint16_t                                           | 0 ~ 4096  | 2 Byte   | rotate speed |


<br>
<br>


## <a name="Protocol_Button">Protocol::Button</a>

Button

```cpp
namespace Protocol
{
    struct Button
    {
        u16     button;
        u8      event;
    };
}
```

| Variable Name | Type  | Range      | Size    | Description |
|:---------:|:-----------------------------------------------------:|:-----:|:--------:|:-------------|
| button    | uint16_t                                              | -     | 2 Byte   | Button input |
| event     | [Button::Event::Type](04_definitions.md#Button_Event) | -     | 1 Byte   | Button event |


<br>
<br>


## <a name="Protocol_JoystickBlock">Protocol::JoystickBlock</a>

Joystick input value of one axis.

```cpp
namespace Protocol
{
    struct JoystickBlock
    {
        s8      x;
        s8      y;
        u8      direction;
        u8      event;
    };
}
```

| Variable Name | Type  | Range      | Size    | Description |
|:----------:|:-----------------------------------------------------------------:|:-------------:|:--------:|:-----------------|
| x          | int8_t                                                            | -100 ~ 100    | 1 Byte   | X axis  |
| y          | int8_t                                                            | -100 ~ 100    | 1 Byte   | Y aixs  |
| direction  | [Joystick::Direction::Type](04_definitions.md#Joystick_Direction) | -             | 1 Byte   | Joystick event  |
| event      | [Joystick::Event::Type](04_definitions.md#Joystick_Event)         | -             | 1 Byte   | Joystick event |


<br>
<br>


## <a name="Protocol_Joystick">Protocol::Joystick</a>

Joystick input value of the left and right.

```cpp
namespace Protocol
{
    struct Joystick
    {
        Protocol::JoystickBlock     left;
        Protocol::JoystickBlock     right;
    };
}
```

| Variable Name | Type  | Range      | Size    | Description |
|:---------:|:---------------------------------------------------:|:-----:|:--------:|:----------------|
| left      | [Protocol::JoystickBlock](#Protocol_JoystickBlock)  | -     | 4 Byte   | left Joystick   |
| right     | [Protocol::JoystickBlock](#Protocol_JoystickBlock)  | -     | 4 Byte   | right Joystick |


<br>
<br>


## <a name="Protocol_Buzzer">Protocol::Buzzer</a>

Buzzer

Use for joystick buzzer.

```cpp
namespace Protocol
{
    struct Buzzer
    {
        u8      mode;   // Buzzer mode
        u16     value;  // Octave scale or hz
        u16     time;   // Playing time(ms)
    };
}
```

| Variable Name | Type  | Range      | Size    | Description |
|:----------:|:-------------------------------------------------------:|:-----------:|:------:|:-----------------------|
| mode       | [Buzzer::Mode::Type](04_definitions.md#Buzzer_Mode)     | -           | 1 Byte | Buzzer mode  |
| value      | [Buzzer::Scale::Type](04_definitions.md#Buzzer_Scale)   | -           | 2 Byte | Scale                  |
|            | UInt16                                                  | 0 ~ 8000    |        | Hz                     |
| time       | UInt16                                                  | 0 ~ 65,535  | 2 Byte | Playing time(ms) |


<br>
<br>


## <a name="Protocol_Vibrator">Protocol::Vibrator</a>

Vibrator

Use for joystick vibrator

```cpp
namespace Protocol
{
    struct Vibrator
    {
        u8      mode;   // vibrator mode(0 is set, 1 is reserve)
        u16     on;     // vibrator on time(ms)
        u16     off;    // vibrator off time(ms)
        u16     total;  // total playing time(ms)
    };
}
```

| Variable Name | Type  | Range      | Size    | Description |
|:----------:|:-------------------------------------------------------:|:-----------:|:--------:|:--------------------|
| mode       | [Vibrator::Mode::Type](04_definitions.md#Vibrator_Mode) | -           | 1 Byte   | vibrator mode(0 is set, 1 is reserve) |
| on         | uint16_t                                                | 0 ~ 65,535  | 2 Byte   | vibrator on time(ms) |
| off        | uint16_t                                                | 0 ~ 65,535  | 2 Byte   | vibrator off time(ms) |
| total      | uint16_t                                                | 0 ~ 65,535  | 2 Byte   | total playing time(ms) |


<br>
<br>


## <a name="Protocol_Pairing">Protocol::Pairing</a>

Pairing

Used to verify or change the pairing information for the device.

Address does not use 0x0000, Broadcasting for 0xFFFF.

```cpp
namespace Protocol
{
    struct Pairing
    {
        u16     addressLocal;
        u16     addressRemote;
        u8      channel;
    };
}
```

| Variable Name | Type  | Range      | Size    | Description |
|:---------------:|:---------:|:----------------:|:--------:|:-------------------|
| addressLocal    | uint16_t  | 0x0001 ~ 0xFFFE  | 2 Byte   | Device address |
| addressRemote   | uint16_t  | 0x0001 ~ 0xFFFE  | 2 Byte   | Remove device address |
| channel         | uint18_t  | 0 ~ 230          | 1 Byte   | Channel  |


<br>
<br>


## <a name="Protocol_Rssi">Protocol::Rssi</a>

RSSI

Received signal strength indication

[http://www.metageek.com/training/resources/understanding-rssi.html](http://www.metageek.com/training/resources/understanding-rssi.html)

Returns the signal strength of connected device.

```cpp
namespace Protocol
{
    struct Rssi
    {
        s8     Rssi;
    };
}
```

| Variable Name | Type  | Range      | Size    | Description |
|:------------:|:--------:|:---------:|:--------:|:-----------|
| rssi         | int8_t   | -100 ~ 0  | 1 Byte   | signal strength |


<br>
<br>


## <a name="Protocol_InformationAssembledForController">Protocol::InformationAssembledForController</a>

Information Assembled For Controller 

If the controller transmits Control commands to RF on a drone to increase the renewal rate of data on the controller, this data is transmitted in response from drone to Ack.

```cpp
namespace Protocol
{
    struct InformationAssembledForController
    {
        s16     angleRoll;
        s16     anglePitch;
        s16     angleYaw;

        float   pressureTemperature;
        float   pressureAltitude;

        float   rangeGround;
    };
}
```


<br>
<br>


## <a name="Protocol_InformationAssembledForEntry">Protocol::InformationAssembledForEntry</a>

Information Assembled For Entry

```cpp
namespace Protocol
{
    struct InformationAssembledForEntry
    {
        s16     accelX;
        s16     accelY;
        s16     accelZ;

        s16     gyroRoll;
        s16     gyroPitch;
        s16     gyroYaw;

        s16     angleRoll;
        s16     anglePitch;
        s16     angleYaw;

        float   pressureTemperature;
        float   pressureAltitude;

        float   imageFlowPositionX;
        float   imageFlowPositionY;

        float   rangeGround;
    };
}
```


<br>

---

<h3>PETRONE V2</H3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. ***Structs***
6. [Structs - Light](06_structs_light.md)
7. [Structs - Display](07_structs_display.md)

<br>

[Index](index.md)
