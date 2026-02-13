**[Coding Drone Plus](index.md)** / **Protocol** / **Structs**

Modified : 2026.1.29

---

#### Introduce structures used for data transmission and reception.

---

* Kramdown table of contents
{:toc .toc}

<br>


<a name="Protocol_Header"></a>
## Protocol::Header

Header

Header used for data transmission and reception.

```cpp
namespace Protocol
{
    struct Header
    {
        u8      dataType;       // Data type
        u8      length;         // Data length
        u8      from;           // Sender device's DeviceType
        u8      to;             // Receiver device's DeviceType
        
    };
}
```

| Name     | Type                                                                | Size    | Range   | Description              |
|:--------:|:-------------------------------------------------------------------:|:-------:|:-------:|:-------------------------|
| dataType | [Protocol::DataType::Type](03_datatype.md#Protocol_DataType)        | 1 Byte  | -       | Data type                |
| length   | uint8_t                                                             | 1 Byte  | 0 ~ 255 | Data length              |
| from     | [Protocol::DeviceType::Type](04_definitions.md#Protocol_DeviceType) | 1 Byte  | -       | Sender device            |
| to       | [Protocol::DeviceType::Type](04_definitions.md#Protocol_DeviceType) | 1 Byte  | -       | Receiver device          |


<br>
<br>


<a name="Protocol_Ping"></a>
## Protocol::Ping

Ping

Used to verify whether a specific device exists. The response is Ack.

```cpp
namespace Protocol
{
    struct Ping
    {
        u64     systemTime;   // Time of the device sending Ping
    };
}
```

| Name      | Type     | Size   | Range | Description  |
|:---------:|:--------:|:------:|:-----:|:-------------|
| systemTime| uint64_t | 8 Byte | -     | System time  |


<br>
<br>


<a name="Protocol_Ack"></a>
## Protocol::Ack

Ack

Sends Ack as a response when no specific data was requested. It returns the CRC16 of the received data, so the sender can verify that the header and data were delivered correctly.

```cpp
namespace Protocol
{
    struct Ack
    {
        u64     systemTime;     // Receive time
        u8      dataType;       // Received data type
        u16     crc16;          // CRC16 of received data
    };
}
```

| Name      | Type                                                        | Size   | Range | Description                               |
|:---------:|:-----------------------------------------------------------:|:------:|:-----:|:------------------------------------------|
| systemTime| uint64_t                                                    | 8 Byte | -     | System time                               |
| dataType  | [Protocol::DataType::Type](03_datatype.md#Protocol_DataType)| 1 Byte | -     | Received data type                        |
| crc16     | uint16_t                                                    | 2 Byte | -     | CRC16 of received header and data         |


<br>
<br>


<a name="Protocol_Error"></a>
## Protocol::Error

Error

If a problem occurs on the drone, it transmits the Error structure via RF once every 600 ms.

errorFlagsForSensor and errorFlagsForState combine multiple flags to indicate that multiple errors occurred at the same time.

When the problem is completely resolved, it resets the Error flags to 0 and transmits 5 additional times, then stops transmitting.

```cpp
namespace Protocol
{
    struct Error
    {
        u64     systemTime;             // Time when error message is transmitted
        u32     errorFlagsForSensor;    // Sensor error flags
        u32     errorFlagsForState;     // State error flags
    };
}
```

| Name                | Type                                                               | Size   | Range | Description              |
|:--------------------:|:-------------------------------------------------------------------:|:--------:|:------:|:------------------------|
| systemTime           | uint64_t                                                           | 8 Byte | -     | System time              |
| errorFlagsForSensor  | [ErrorFlagsForSensor::Type](04_definitions.md#ErrorFlagsForSensor) | 4 Byte | -     | Sensor error flags       |
| errorFlagsForState   | [ErrorFlagsForState::Type](04_definitions.md#ErrorFlagsForState)   | 4 Byte | -     | State error flags        |


<br>
<br>


<a name="Protocol_Request"></a>
## Protocol::Request

Request

```cpp
namespace Protocol
{
    struct Request
    {
        u8      dataType;          // Requested data type
    };
}
```

| Name     | Type                                                         | Size   | Range | Description           |
|:-------------:|:-------------------------------------------------------------:|:--------:|:-----:|:----------------------|
| dataType  | [Protocol::DataType::Type](03_datatype.md#Protocol_DataType) | 1 Byte | -     | Requested data type   |


<br>
<br>


<a name="Protocol_Address"></a>
## Protocol::Address

Device address (unique ID)

```cpp
namespace Protocol
{
    struct Address
    {
        u8   address[5];
    };
}
```

| Name    | Type          | Size    | Range | Description     |
|:----------:|:---------------:|:--------:|:-----:|:-------------|
| address | uint8_t Array | 5 Byte  | -     | Device address  |


<br>
<br>


<a name="Protocol_Information"></a>
## Protocol::Information

Firmware information

```cpp
namespace Protocol
{
    struct Information
    {
        u8      modeUpdate;     // Update mode

        u32     modelNumber;    // Model number
        u32     version;        // Firmware version

        u16     year;           // Build year
        u8      month;          // Build month
        u8      day;            // Build day
    };
}
```

| Name        | Type                                                | Size   | Range | Description         |
|:-------------:|:-----------------------------------------------------|:--------:|:----:|:--------------------|
| modeUpdate   | [Updater::ModeUpdate::Type](04_definitions.md#Mode_Update) | 1 Byte | -     | Update mode         |
| modelNumber  | [ModelNumber::Type](04_definitions.md#ModelNumber)  | 4 Byte | -     | Model number        |
| version      | [Protocol::Version](#Protocol_Version)              | 4 Byte | -     | Firmware version    |
| year         | uint16_t                                            | 2 Byte | -     | Build year          |
| month        | uint8_t                                             | 1 Byte | -     | Build month         |
| day          | uint8_t                                             | 1 Byte | -     | Build day           |


<br>
<br>


<a name="Protocol_Version"></a>
## Protocol::Version

Firmware version

To compare versions using the `v` value, the member order in the struct is arranged in reverse compared to other structures.

```cpp
namespace Protocol
{
    union Version
    {
        u32 v;

        struct
        {
            u16     build;      // Build Number
            u8      minor;      // Minor Number
            u8      major;      // Major Number
        };
    };
}
```

| Name  | Type     | Size   | Range     | Description                  |
|:----------:|:------------:|:--------:|:----------:|:-------------|
| build | uint16_t | 2 Byte  | 0 ~ 65535  | Build number                |
| minor | uint8_t  | 1 Byte  | 0 ~ 255    | Minor number                |
| major | uint8_t  | 1 Byte  | 0 ~ 255    | Major number                |
| v     | uint32_t | 4 Byte  | -          | Combined build/minor/major  |



<br>
<br>


<a name="Control_Quad8"></a>
## Control::Quad8

Drone

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

| Name     | Type   | Size   | Range      | Description     | Minus(-)        | Plus(+)         |
|:---------:|:--------:|:--------:|:------------:|:-----------|:----------:|:-------------:|
| roll     | int8_t | 1 Byte | -100 ~ 100 | Left-Right      | Left            | Right           |
| pitch    | int8_t | 1 Byte | -100 ~ 100 | Forward-Backward| Backward        | Forward         |
| yaw      | int8_t | 1 Byte | -100 ~ 100 | Turn Left-Right | Clockwise       | Counterclockwise|
| throttle | int8_t | 1 Byte | -100 ~ 100 | Up-Down         | Down            | Up              |


<br>
<br>


<a name="Control_Quad8AndRequestData"></a>
## Control::Quad8AndRequestData

Drone control and data request

When sending a control command, respond with the requested data instead of Ack.

```cpp
namespace Control
{
    struct Quad8AndRequestData
    {
        s8      roll;       // roll
        s8      pitch;      // pitch
        s8      yaw;        // yaw
        s8      throttle;   // throttle

        u8      dataType;   // DataType
    };
}
```

| Name     | Type   | Size   | Range      | Description     | Minus(-)        | Plus(+)         |
|:---------:|:--------:|:--------:|:------------:|:-----------|:----------:|:-------------:|
| roll     | int8_t | 1 Byte | -100 ~ 100 | Left-Right      | Left            | Right           |
| pitch    | int8_t | 1 Byte | -100 ~ 100 | Forward-Backward| Backward        | Forward         |
| yaw      | int8_t | 1 Byte | -100 ~ 100 | Turn Left-Right | Clockwise       | Counterclockwise|
| throttle | int8_t | 1 Byte | -100 ~ 100 | Up-Down         | Down            | Up              |
| dataType | [Protocol::DataType::Type](03_datatype.md#Protocol_DataType) | 1 Byte | - | Requested data type | - | - |


<br>
<br>


<a name="Control_Position16"></a>
## Control::Position16

Drone movement command

Used to send a movement command to the drone.

```cpp
namespace Control
{
    struct Position16
    {
        s16     positionX;          // meter    x 10
        s16     positionY;          // meter    x 10
        s16     positionZ;          // meter    x 10
        s16     velocity;           // m/s      x 10
        
        s16     heading;            // degree
        s16     rotationalVelocity; // deg/s
    };
}
```


| Name                | Type   | Size   | Range                    | Unit        | Description                  |
|:---------------------:|:--------:|:--------:|:--------------------------:|:--------------|:---------------------|
| positionX            | int16_t | 2 Byte | -100 ~ 100(-10.0 ~ 10.0) | meter x 10  | forward(+), backward(-)     |
| positionY            | int16_t | 2 Byte | -100 ~ 100(-10.0 ~ 10.0) | meter x 10  | left(+), right(-)           |
| positionZ            | int16_t | 2 Byte | -100 ~ 100(-10.0 ~ 10.0) | meter x 10  | up(+), down(-)              |
| velocity             | int16_t | 2 Byte | 0 ~ 50(0.0 ~ 5.0)        | m/s x 10    | move speed                  |
| heading              | int16_t | 2 Byte | -360 ~ 360               | degree      | CCW(+), CW(-)               |
| rotationalVelocity   | int16_t | 2 Byte | 10 ~ 180                 | degree/s    | rotation speed              |


<br>
<br>


<a name="Control_Position"></a>
## Control::Position

Drone movement command

Used to send a movement command to the drone.

```cpp
namespace Control
{
    struct Position
    {
        float       positionX;              // meter
        float       positionY;              // meter
        float       positionZ;              // meter
        float       velocity;               // m/s
        
        s16         heading;                // degree
        s16         rotationalVelocity;     // deg/s
    };
}
```


| Name                | Type   | Size   | Range         | Unit     | Description                 |
|:---------------------:|:--------:|:--------:|:--------------:|:---------|:---------------------|
| positionX            | float  | 4 Byte | -10.0 ~ 10.0 | meter   | forward(+), backward(-)     |
| positionY            | float  | 4 Byte | -10.0 ~ 10.0 | meter   | left(+), right(-)           |
| positionZ            | float  | 4 Byte | -10.0 ~ 10.0 | meter   | up(+), down(-)              |
| velocity             | float  | 4 Byte | 0.0 ~ 5.0    | m/s     | forward/backward speed      |
| heading              | int16_t| 2 Byte | -360 ~ 360   | degree  | CCW(+), CW(-)               |
| rotationalVelocity   | int16_t| 2 Byte | 10 ~ 180     | degree/s| rotation speed              |


<br>
<br>


<a name="Protocol_Command_Command"></a>
## Protocol::Command::Command

Change settings

```cpp
namespace Protocol
{
    namespace Command
    {
        struct Command
        {
            u8      commandType;   // Command type
            u8      option;        // Option for command
        };
    }
}
```

| Name        | Type                                                                 | Size   | Range | Description |
|:-----------:|:-----------------------------------------------------------------------:|:--------:|:-------:|:-------------|
| commandType | [Protocol::CommandType::Type](04_definitions.md#Protocol_CommandType) | 1 Byte | -     | Command type |
| option      | uint8_t                                                               | 1 Byte | -     | Command option |


<br>
<br>


<a name="Protocol_Command_LightEvent"></a>
## Protocol::Command::LightEvent

Change settings + LED event

```cpp
namespace Protocol
{
    namespace Command
    {
        struct LightEvent
        {
            Protocol::Command::Command      command;
            Protocol::Light::Event          event;
        };
    }
}
```

| Name    | Type                                                               | Size   | Range | Description |
|:-----------:|:---------------------------------------------------------------------:|:--------:|:-------:|:-------------|
| command | [Protocol::Command::Command](#Protocol_Command_Command)            | 2 Byte | -     | Command     |
| event   | [Protocol::Light::Event](06_structs_light.md#Protocol_Light_Event) | 4 Byte | -     | LED event   |


<br>
<br>


<a name="Protocol_Command_LightEventColor"></a>
## Protocol::Command::LightEventColor

Change settings + LED event (RGB)

```cpp
namespace Protocol
{
    namespace Command
    {
        struct LightEventColor
        {
            Protocol::Command::Command      command;
            Protocol::Light::Event          event;
            Light::Color                    color;
        };
    }
}
```

| Name    | Type                                                               | Size   | Range | Description |
|:-----------:|:---------------------------------------------------------------------:|:--------:|:-------:|:-------------|
| command | [Protocol::Command::Command](#Protocol_Command_Command)            | 2 Byte | -     | Command     |
| event   | [Protocol::Light::Event](06_structs_light.md#Protocol_Light_Event) | 4 Byte | -     | LED event   |
| color   | [Light::Color](06_structs_light.md#Light_Color)                    | 3 Byte | -     | LED RGB color |


<br>
<br>


<a name="Protocol_Command_LightEventColors"></a>
## Protocol::Command::LightEventColors

Change settings + LED event (Palette)

```cpp
namespace Protocol
{
    namespace Command
    {
        struct LightEventColors
        {
            Protocol::Command::Command      command;
            Protocol::Light::Event          event;
            u8                              colors;
        };
    }
}
```

| Name    | Type                                                               | Size   | Range | Description          |
|:-----------:|:---------------------------------------------------------------------:|:--------:|:-------:|:------------------|
| command | [Protocol::Command::Command](#Protocol_Command_Command)            | 2 Byte | -     | Command              |
| event   | [Protocol::Light::Event](06_structs_light.md#Protocol_Light_Event) | 4 Byte | -     | LED event            |
| colors  | [Light::Colors::Type](06_structs_light.md#Light_Colors)            | 1 Byte | -     | LED palette index    |


<br>
<br>


<a name="Protocol_Pairing"></a>
## Protocol::Pairing

Pairing

Used to check or change pairing information of the device.

If all bytes of the address are 0, RF transmission is not performed and received data is ignored.

channelArray contains 8 channels. In frequency hopping (FHSS) mode, all specified channels are used. In fixed-frequency mode, the first channel in the array is used.

```cpp
namespace Protocol
{
    struct Pairing
    {
        u8      connectorDeviceType;   // Connected device type

        u8      address[5];            // Address
        u8      channelArray[8];       // Channel list
    };
}
```

| Name         | Type     | Size   | Range              | Description |
|:---------------:|:---------:|:--------:|:------------------:|:-----------|
| connectorDeviceType | uint8_t | 1 Byte | - | Connected device type |
| address       | uint8_t Array | 5 Byte | - | Address |
| channelArray  | uint8_t Array | 8 Byte | 0 ~ 81            | Channel |


<br>
<br>


<a name="Protocol_ResponseRate"></a>
## Protocol::ResponseRate

Response rate

Response rate setting.

```cpp
namespace Protocol
{
    struct ResponseRate
    {
        u8      responseRate;
    };
}
```

| Name         | Type    | Size   | Range | Description   |
|:------------:|:-------:|:------:|:-----:|:--------------|
| responseRate | uint8_t | 1 Byte | -     | Response rate |


<br>
<br>


<a name="Protocol_RawMotion"></a>
## Protocol::RawMotion

Motion sensor RAW data

```cpp
namespace Protocol
{
    struct RawMotion
    {
        s16     accelX;
        s16     accelY;
        s16     accelZ;
        
        s16     gyroRoll;
        s16     gyroPitch;
        s16     gyroYaw;
    };
}
```

| Name      | Type  | Size   | Range             | Description  |
|:----------:|:--------:|:--------:|:-----------------:|:---------------|
| accelX    | Int16 | 2 Byte | -32,768 ~ 32,767 | Accel X      |
| accelY    | Int16 | 2 Byte | -32,768 ~ 32,767 | Accel Y      |
| accelZ    | Int16 | 2 Byte | -32,768 ~ 32,767 | Accel Z      |
| gyroRoll  | Int16 | 2 Byte | -32,768 ~ 32,767 | Gyro Roll    |
| gyroPitch | Int16 | 2 Byte | -32,768 ~ 32,767 | Gyro Pitch   |
| gyroYaw   | Int16 | 2 Byte | -32,768 ~ 32,767 | Gyro Yaw     |


<br>
<br>


<a name="Protocol_RawFlow"></a>
## Protocol::RawFlow

Flow sensor RAW data

```cpp
namespace Protocol
{
    struct RawFlow
    {
        float   x;
        float   y;
    };
}
```

| Name | Type  | Size  | Range | Description |
|:----------:|:---------:|:--------:|:-----:|:--------|
| x | float | 4 Byte | - | X axis |
| y | float | 4 Byte | - | Y axis |


<br>
<br>


<a name="Protocol_State"></a>
## Protocol::State

Current drone state

```cpp
namespace Protocol
{
    struct State
    {
        u8      modeSystem;         // System mode
        u8      modeFlight;         // Flight mode

        u8      modeControlFlight;  // Flight control mode
        u8      modeMovement;       // Movement state
        u8      headless;           // Headless mode
        u8      controlSpeed;       // Control speed
        u8      sensorOrientation;  // Sensor orientation
        u8      battery;            // Battery level (0 ~ 100%)
    };
}
```

| Name              | Type                                                                 | Size   | Range   | Description                |
|:-----------------:|:---------------------------------------------------------------------:|:--------:|:--------:|:-----------------------|
| modeSystem        | [Mode::System::Type](04_definitions.md#Mode_System)                  | 1 Byte | -       | System operation mode      |
| modeFlight        | [Mode::Flight::Type](04_definitions.md#Mode_Flight)                  | 1 Byte | -       | Flight controller mode     |
| modeControlFlight | [Mode::Control::Flight::Type](04_definitions.md#Mode_Control_Flight) | 1 Byte | -       | Flight control mode        |
| modeMovement      | [Mode::Movement::Type](04_definitions.md#Mode_Movement)              | 1 Byte | -       | Movement state             |
| headless          | [Headless::Type](04_definitions.md#Headless)                         | 1 Byte | -       | Headless state             |
| controlSpeed      | uint8_t                                                              | 1 Byte | -       | Control speed (1, 2, 3)    |
| sensorOrientation | [SensorOrientation::Type](04_definitions.md#SensorOrientation)       | 1 Byte | -       | Sensor orientation         |
| battery           | uint8_t                                                              | 1 Byte | 0 ~ 100 | Battery level              |


<br>
<br>


<a name="Protocol_Attitude"></a>
## Protocol::Attitude

Attitude

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

| Name   | Type    | Size   | Range            | Description |
|:----------:|:----------:|:--------:|:-----------------:|:-----------|
| roll       | int16_t    | 2 Byte   | -32,768 ~ 32,767  | Roll       |
| pitch      | int16_t    | 2 Byte   | -32,768 ~ 32,767  | Pitch      |
| yaw        | int16_t    | 2 Byte   | -32,768 ~ 32,767  | Yaw        |


When checking the drone attitude, the value ranges are as follows.

| Name  | Type   | Size   | Range      | Description              |
|:--------:|:--------:|:--------:|:-----------:|:-------------------:|
| roll  | int16_t | 2 Byte |  -90 ~  90 | Roll angle (left/right tilt) |
| pitch | int16_t | 2 Byte |  -90 ~  90 | Pitch angle (front/back tilt) |
| yaw   | int16_t | 2 Byte | -180 ~ 180 | Yaw angle (rotation) |


<br>
<br>


<a name="Protocol_Position"></a>
## Protocol::Position

Position

```cpp
namespace Protocol
{
    struct Position
    {
        float       x;      // meter
        float       y;      // meter
        float       z;      // meter
    };
}
```


| Name | Type  | Size   | Range            | Unit   | Description                 |
|:-------------:|:------:|:--------:|:----------------:|:---------|:---------------------|
| x    | float | 4 Byte | -100.0 ~ 100.0  | meter | forward(+), backward(-)     |
| y    | float | 4 Byte | -100.0 ~ 100.0  | meter | left(+), right(-)           |
| z    | float | 4 Byte | -100.0 ~ 100.0  | meter | up(+), down(-)              |


<br>
<br>


<a name="Protocol_Altitude"></a>
## Protocol::Altitude

Altitude

```cpp
namespace Protocol
{
    struct Altitude
    {
        float   temperature;
        float   pressure;
        float   altitude;
        float   rangeHeight;
    };
}
```

| Name        | Type  | Size   | Range | Description            |
|:-------------:|:--------:|:--------:|:-----------------:|:--------------------|
| temperature | float | 4 Byte | - | Temperature            |
| pressure    | float | 4 Byte | - | Pressure               |
| altitude    | float | 4 Byte | - | Altitude               |
| rangeHeight | float | 4 Byte | - | Range sensor height    |


<br>
<br>


<a name="Protocol_Motion"></a>
## Protocol::Motion

Motion sensor data and drone attitude

```cpp
namespace Protocol
{
    struct Motion
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
    };
}
```

| Name      | Type   | Size  | Range                               | Unit                 | Description   |
|:----------:|:--------:|:-------:|:-----------------------------------:|:--------------------:|:--------------|
| accelX    | int16_t | 2 Byte | -1,568 ~ 1,568<br>(-156.8 ~ 156.8) | m/s<sup>2</sup> x 10 | Accel X       |
| accelY    | int16_t | 2 Byte | -1,568 ~ 1,568<br>(-156.8 ~ 156.8) | m/s<sup>2</sup> x 10 | Accel Y       |
| accelZ    | int16_t | 2 Byte | -1,568 ~ 1,568<br>(-156.8 ~ 156.8) | m/s<sup>2</sup> x 10 | Accel Z       |
| gyroRoll  | int16_t | 2 Byte | -2,000 ~ 2,000                     | degree/s             | Gyro Roll     |
| gyroPitch | int16_t | 2 Byte | -2,000 ~ 2,000                     | degree/s             | Gyro Pitch    |
| gyroYaw   | int16_t | 2 Byte | -2,000 ~ 2,000                     | degree/s             | Gyro Yaw      |
| angleRoll | int16_t | 2 Byte | -180 ~ 180                         | degree               | Attitude Roll |
| anglePitch| int16_t | 2 Byte | -180 ~ 180                         | degree               | Attitude Pitch|
| angleYaw  | int16_t | 2 Byte | -180 ~ 180                         | degree               | Attitude Yaw  |


<br>
<br>


<a name="Protocol_Range"></a>
## Protocol::Range

Range sensor output

```cpp
namespace Protocol
{
    struct Range
    {
        s16     left;
        s16     front;
        s16     right;
        s16     rear;
        s16     top;
        s16     bottom;
    };
}
```

| Name   | Type   | Size  | Range      | Unit | Description                               |
|:----------:|:--------:|:-------:|:---------------:|:---------:|:------------------------------------------|
| left   | int16_t | 2 Byte | 0 ~ 2,000 | mm | Output of left-facing range sensor         |
| front  | int16_t | 2 Byte | 0 ~ 2,000 | mm | Output of front-facing range sensor        |
| right  | int16_t | 2 Byte | 0 ~ 2,000 | mm | Output of right-facing range sensor        |
| rear   | int16_t | 2 Byte | 0 ~ 2,000 | mm | Output of rear-facing range sensor         |
| top    | int16_t | 2 Byte | 0 ~ 2,000 | mm | Output of top-facing range sensor          |
| bottom | int16_t | 2 Byte | 0 ~ 2,000 | mm | Output of bottom-facing range sensor       |


<br>
<br>


<a name="Protocol_Count"></a>
## Protocol::Count

Count

Used to read flight time and related counters.

```cpp
namespace Protocol
{
    struct Count
    {
        u32     timeSystem;             // System operation time
        u32     timeFlight;             // Flight time

        u16     countTakeOff;           // Takeoff count
        u16     countLanding;           // Landing count
        u16     countAccident;          // Accident count
    };
}
```

| Name          | Type     | Size   | Range     | Description               |
|:----------------:|:----------:|:--------:|:----------:|:----------------------|
| timeSystem     | uint32_t | 4 Byte | -         | System operation time (sec) |
| timeFlight     | uint32_t | 4 Byte | -         | Flight time (sec)            |
| countTakeOff   | uint16_t | 2 Byte | 0 ~ 65,535| Takeoff count                |
| countLanding   | uint16_t | 2 Byte | 0 ~ 65,535| Landing count                |
| countAccident  | uint16_t | 2 Byte | 0 ~ 65,535| Accident count               |


<br>
<br>


<a name="Protocol_Bias"></a>
## Protocol::Bias

Bias

```cpp
namespace Protocol
{
    struct Bias
    {
        s16     accelX;         // X
        s16     accelY;         // Y
        s16     accelZ;         // Z

        s16     gyroRoll;       // Roll
        s16     gyroPitch;      // Pitch
        s16     gyroYaw;        // Yaw
    };
}
```

| Name   | Type   | Size   | Range            | Description |
|:----------:|:----------:|:--------:|:-----------------:|:------------|
| accelX     | int16_t    | 2 Byte   | -32,768 ~ 32,767  | Accel X     |
| accelY     | int16_t    | 2 Byte   | -32,768 ~ 32,767  | Accel Y     |
| accelZ     | int16_t    | 2 Byte   | -32,768 ~ 32,767  | Accel Z     |
| gyroRoll   | int16_t    | 2 Byte   | -32,768 ~ 32,767  | Gyro Roll   |
| gyroPitch  | int16_t    | 2 Byte   | -32,768 ~ 32,767  | Gyro Pitch  |
| gyroYaw    | int16_t    | 2 Byte   | -32,768 ~ 32,767  | Gyro Yaw    |


<br>
<br>


<a name="Protocol_Trim"></a>
## Protocol::Trim

Trim

```cpp
namespace Protocol
{
    struct Trim
    {
        s16     roll;         // Roll
        s16     pitch;        // Pitch
        s16     yaw;          // Yaw
        s16     throttle;     // Throttle
    };
}
```

| Name     | Type   | Size   | Range      | Description |
|:---------:|:--------:|:--------:|:------------:|:-----------|
| roll      | int16_t  | 2 Byte   | -200 ~ 200   | Roll       |
| pitch     | int16_t  | 2 Byte   | -200 ~ 200   | Pitch      |
| yaw       | int16_t  | 2 Byte   | -200 ~ 200   | Yaw        |
| throttle  | int16_t  | 2 Byte   | -200 ~ 200   | Throttle   |


<br>
<br>


<a name="Protocol_Weight"></a>
## Protocol::Weight

Weight

```cpp
namespace Protocol
{
    struct Weight
    {
        float   weight;         // Weight
    };
}
```

| Name   | Type  | Size   | Range     | Description |
|:---------:|:--------:|:--------:|:------------:|:--------|
| weight | float | 4 Byte | 100 ~ 150 | Weight |


<br>
<br>


<a name="Protocol_LostConnection"></a>
## Protocol::LostConnection

Time settings for drone behavior when connection is lost

Unit is milliseconds. If the value is set to 0, the item is ignored.

If the connection with the device that last sent a drone control command is lost, it performs neutral control, landing, and forced stop after the specified time.

The default connected device is RF, and the setting value is not stored in flash memory, so it must be set each time the drone starts.

```cpp
namespace Protocol
{
    struct LostConnection
    {
        u16     timeNeutral;        // Neutral control
        u16     timeLanding;        // Landing
        u32     timeStop;           // Stop
    };
}
```

| Name        | Type     | Size   | Range              | Description                                   |
|:-------------:|:---------:|:--------:|:------------------:|:------------------------------------------------|
| timeNeutral | uint16_t | 2 Byte | 0 ~ 65,535        | Time to set neutral control after disconnect  |
| timeLanding | uint16_t | 2 Byte | 0 ~ 65,535        | Time to land after disconnect                 |
| timeStop    | uint32_t | 4 Byte | 0 ~ 4,294,967,295 | Time to stop after disconnect                 |


<br>
<br>


<a name="Protocol_Motor"></a>
## Protocol::Motor

Motor

Used to control all 4 motors at once, or to check the current motor input values.

Use the following structure as an array.

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

| Name     | Type                                         | Size   | Range    | Description        |
|:----------:|:---------------------------------------------:|:--------:|:---------:|:----------|
| rotation | [Rotation::Type](04_definitions.md#Rotation) | 1 Byte | -       | Rotation direction |
| value    | int16_t                                      | 2 Byte | -       | Rotation speed     |


<br>
<br>


<a name="Protocol_MotorSingle"></a>
## Protocol::MotorSingle

Single motor control

Used to control a single motor, or to check the current motor input value.

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

| Name     | Type                                              | Size   | Range    | Description        |
|:----------:|:--------------------------------------------------:|:--------:|:---------:|:----------------|
| target   | [Motor::Part::Type](04_definitions.md#Motor_Part) | 1 Byte | 0 ~ 3    | Target motor       |
| rotation | [Rotation::Type](04_definitions.md#Rotation)      | 1 Byte | -        | Rotation direction |
| value    | int16_t                                           | 2 Byte | -       | Rotation speed     |


<br>
<br>

<a name="Protocol_Buzzer"></a>
## Protocol::Buzzer

Buzzer

```cpp
namespace Protocol
{
    struct Buzzer
    {
        u8      mode;   // Buzzer mode
        u16     value;  // Scale or Hz
        u16     time;   // Play time (ms)
    };
}
```

| Name  | Type                                                  | Size   | Range       | Description           |
|:----------:|:-------------------------------------------------------:|:------:|:-----------:|:-----------------------|
| mode       | [Buzzer::Mode::Type](04_definitions.md#Buzzer_Mode)   | 1 Byte | -           | Buzzer mode           |
| value      | [Buzzer::Scale::Type](04_definitions.md#Buzzer_Scale)   | 2 Byte | -           | Scale                  |
|            | uint16_t                                                | 2 Byte | 0 ~ 8,000   | Hz                     |
| time       | uint16_t                                                | 2 Byte | 0 ~ 65,535  | Duration (ms)         |


<br>
<br>


<a name="Protocol_Vibrator"></a>
## Protocol::Vibrator

Vibrator

```cpp
namespace Protocol
{
    struct Vibrator
    {
        u8      mode;   // Mode (0: set, 1: reserve)
        u16     on;     // ON time (ms)
        u16     off;    // OFF time (ms)
        u16     total;  // Total time (ms)
    };
}
```

| Name  | Type                                                 | Size   | Range       | Description        |
|:----------:|:-------------------------------------------------------:|:--------:|:-----------:|:--------------------|
| mode  | [Vibrator::Mode::Type](04_definitions.md#Vibrator_Mode) | 1 Byte | -          | Vibrator mode      |
| on    | uint16_t                                               | 2 Byte | 0 ~ 65,535 | ON time (ms)       |
| off   | uint16_t                                               | 2 Byte | 0 ~ 65,535 | OFF time (ms)      |
| total | uint16_t                                               | 2 Byte | 0 ~ 65,535 | Total time (ms)    |


<br>
<br>


<a name="Protocol_Button"></a>
## Protocol::Button

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

| Name   | Type                                                 | Size   | Range | Description   |
|:---------:|:-----------------------------------------------------:|:--------:|:-----:|:-------------|
| button | uint16_t                                             | 2 Byte | -     | Button input  |
| event  | [Button::Event::Type](04_definitions.md#Button_Event) | 1 Byte | -     | Button event  |


<br>
<br>


<a name="Protocol_JoystickBlock"></a>
## Protocol::JoystickBlock

Input value of one joystick axis on the controller

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

| Name      | Type                                                             | Size   | Range       | Description       |
|:----------:|:-----------------------------------------------------------------:|:--------:|:-------------:|:-----------------|
| x         | int8_t                                                           | 1 Byte | -100 ~ 100 | Joystick X axis   |
| y         | int8_t                                                           | 1 Byte | -100 ~ 100 | Joystick Y axis   |
| direction | [Joystick::Direction::Type](04_definitions.md#Joystick_Direction) | 1 Byte | -         | Joystick direction |
| event     | [Joystick::Event::Type](04_definitions.md#Joystick_Event)         | 1 Byte | -         | Event             |


<br>
<br>


<a name="Protocol_Joystick"></a>
## Protocol::Joystick

Input values of left and right joysticks on the controller

```cpp
namespace Protocol
{
    struct Joystick
    {
        Protocol::JoystickBlock     joystickLeft;
        Protocol::JoystickBlock     joystickRight;
    };
}
```

| Name  | Type                                               | Size   | Range | Description    |
|:---------:|:---------------------------------------------------:|:--------:|:-----:|:----------------|
| joystickLeft  | [Protocol::JoystickBlock](#Protocol_JoystickBlock) | 4 Byte | -     | Left joystick  |
| joystickRight | [Protocol::JoystickBlock](#Protocol_JoystickBlock) | 4 Byte | -     | Right joystick |


<br>
<br>


<a name="Protocol_InformationAssembledForController"></a>
## Protocol::InformationAssembledForController

Assembled information data (Controller)

Structure that combines multiple data fields to increase the update rate of data displayed on the controller.

```cpp
namespace Protocol
{
    struct InformationAssembledForController
    {
        s16     angleRoll;      // Attitude Roll
        s16     anglePitch;     // Attitude Pitch
        s16     angleYaw;       // Attitude Yaw

        u16     rpm;            // RPM

        s16     positionX;      // meter x 10
        s16     positionY;      // meter x 10
        s16     positionZ;      // meter x 10

        s8      speedX;         // meter x 10
        s8      speedY;         // meter x 10

        u8      rangeHeight;    // meter x 100

        u8      responseRate;   // response rate
    };
}
```


<br>
<br>


<a name="Protocol_InformationAssembledForEntry"></a>
## Protocol::InformationAssembledForEntry

Assembled information data (Entry)

```cpp
namespace Protocol
{
    struct InformationAssembledForEntry
    {
        s16     angleRoll;
        s16     anglePitch;
        s16     angleYaw;

        s16     positionX;
        s16     positionY;
        s16     positionZ;

        s16     rangeHeight;
        float   altitude;
    };
}
```


<br>
<br>

---

<h3>Coding Drone Plus</H3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. ***Structs***
6. [Structs - Light](06_structs_light.md)
<!-- 7. [Structs - Display](07_structs_display.md) -->

<br>

[Index](index.md)
