***DRONEFIGHTER2017 / Protocol / Structs***<br>
Modified : 2018.02.08

---

#### Introduce the structures used to send and receive data.

---

<br>

## <a name="Protocol_Ping">Protocol::Ping</a>
Use for check specific device is exists. Response is ACK type.

```cpp
namespace Protocol
{
    struct Ping
    {
        u32  systemTime;   // Ping send time
    };
}
```
- Device that received this data sent Protocol::Ack


<br>
<br>


## <a name="Protocol_Ack">Protocol::Ack</a>
Send Ack when the specific data is not requested. This protocols has crc16 of the received data, it can be checked whether the data was transmitted correctly.
```cpp
namespace Protocol
{
    struct Ack
    {
        u32     systemTime;     // Recieve time
        u8      dataType;       // Recieve datatype
        u16     crc16;          // Recieve data crc16
    };
}
```
- dataType : [Protocol::DataType::Type](03_datatype.md#Protocol_DataType)
- If the data request clearly, response data. Otherwise is Protocol::Ack respond.
- The crc16 of the received data was sent back in response. It can be checked whether the data was transmitted correctly.

<br>
<br>


## <a name="Protocol_Request">Protocol::Request</a>
Request data to Drone Fighter 2017.
```cpp
namespace Protocol
{
    struct Request
    {
        u8   dataType;     // Request datatype
    };
}
```
- dataType : [Protocol::DataType::Type](03_datatype.md#Protocol_DataType)


<br>
<br>


## <a name="Control_Double8">Control::Double8</a>
Control for drive mode. Ignore in flight mode this command.
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

Control::Double8 input values are this range 

| Name     | Type | Range       | Direction        | Minus(-) | Plus(+) |
|:--------:|:----:|:-----------:|:----------------:|:--------:|:-------:|
| wheel    | s8   | -100 ~ 100  | Left-Right       | Left     | Right   |
| accel    | s8   | -100 ~ 100  | Forward-Backward | Backward | Forward |


<br>
<br>


## <a name="Control_Quad8">Control::Quad8</a>
Control for Drone Fighter 2017.
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

Control input values are this range :
! Drive Mode uses **throttle**(Forward/Backward) and  **roll** (Left/Right).

|   Name   | Type | Range       | Direction        | Minus(-)   | Plus(+)    |
|:--------:|:----:|:-----------:|:----------------:|:----------:|:----------:|
| roll     | s8   | -100 ~ 100  | Left-Right       | Left       | Right      |
| pitch    | s8   | -100 ~ 100  | Forward-Backward | Backward   | Forward    |
| yaw      | s8   | -100 ~ 100  | Turn Left-Right  | Turn Left  | Turn Right |
| throttle | s8   | -100 ~ 100  | Up/Down          | Down       | Up         |


<br>
<br>


## <a name="Protocol_Command">Protocol::Command</a>
Request data or change settings for Drone Fighter 2017.
```cpp
namespace Protocol
{
    struct Command
    {
        u8 commandType;   // command type
        u8 option;        // command option
    };
}
```
- commandType : [Protocol::CommandType::Type](04_definitions.md#Protocol_CommandType)
- option : [Mode::Vehicle::Type](04_definitions.md#Mode_Vehicle), [Coordinate::Type](04_definitions.md#Coordinate), [System::Trim::Type](04_definitions.md#Trim),  [System::FlightEvent::Type](04_definitions.md#FlightEvent), [Protocol::DataType::Type](03_datatype.md#Protocol_DataType), [UserInterface::Preset::Type](04_definitions.md#UserInterface_Preset)


<br>
<br>


## <a name="Protocol_Address">Protocol::Address</a>
Respons device address or Change device address.
```cpp
namespace Protocol
{
    struct Address
    {
        u8   address[8];
    };
}
```
- Communication device, such as BLE or Zigbee, and when given a unique device address, return device's unique device address.
  (DroneFighter is using Zigbee for communication and uses communication chip's MAC address.)

<br>
<br>


## <a name="Protocol_State">Protocol::State</a>
Drone Fighter 2017's current state response.
```cpp
namespace Protocol
{
    struct State
    {
        u8          modeVehicle;        // vehicle mode.
        
        u8          modeSystem;         // system mode
        u8          modeFlight;         // flight mode
        u8          modeDrive;          // drive mode
        
        u8          sensorOrientation;  // sensor orientation
        u8          coordinate;         // coordinate
        u8          battery;            // battery state (0 ~ 100)
    };
}
```
- modeVehicle : [Mode::Vehicle::Type](04_definitions.md#Mode_Vehicle)
- modeSystem : [Mode::System::Type](04_definitions.md#Mode_System)
- modeFlight : [Mode::Flight::Type](04_definitions.md#Mode_Flight)
- modeDrive : [Mode::Drive::Type](04_definitions.md#Mode_Drive)
- sensorOrientation : [SensorOrientation::Type](04_definitions.md#SensorOrientation)
- coordinate : [Coordinate::Type](04_definitions.md#Coordinate)


<br>
<br>


## <a name="Protocol_Attitude">Protocol::Attitude</a>
Returns the Attitude value.
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

|   Name   | Type | Range       | Description                   | 
|:--------:|:----:|:-----------:|:-----------------------------:|
| roll     | s16  | -180 ~ 180  | Angle of roll                 |
| pitch    | s16  | -180 ~ 180  | Angle of pitch                |
| yaw      | s16  |    0 ~ 360  | Angle of gravity rotated axis |

<br>
<br>


## <a name="Protocol_GyroBias">Protocol::GyroBias</a>
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

When checking the gyro sensor data, the range of use is as follows :

|   Name   | Type | Range           | 
|:--------:|:----:|:---------------:|
| roll     | s16  | -32768 ~ 32767  |
| pitch    | s16  | -32768 ~ 32767  |
| yaw      | s16  | -32768 ~ 32767  |


<br>
<br>


## <a name="Protocol_TrimFlight">Protocol::TrimFlight</a>
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


## <a name="Protocol_TrimDrive">Protocol::TrimDrive</a>
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


## <a name="Protocol_TrimAll">Protocol::TrimAll</a>
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
- flight : [Protocol::TrimFlight](#Protocol_TrimFlight)
- drive : [Protocol::TrimDrive](#Protocol_TrimDrive)


<br>
<br>


## <a name="Protocol_CountFlight">Protocol::CountFlight</a>
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


## <a name="Protocol_CountDrive">Protocol::CountDrive</a>
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


## <a name="Protocol_IrMessage">Protocol::IrMessage</a>
Data that is used to transfer IR data or sent to an external device when IR data is received.
```cpp
namespace Protocol
{
    struct IrMessage
    {
        u32     irData;                  // IR message
    };
}
```
- Drone Fighter 2017 uses only 7 bits. Therefore, only the values from 0 to 127 can be used.


<br>
<br>


## <a name="Protocol_Imu">Protocol::Imu</a>
Returns the value of the gyro sensor and the attitude value of the drone.

```cpp
namespace Protocol
{
    struct Imu
    {
        u32     systemTime;
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


## <a name="Protocol_Button">Protocol::Button</a>
Drone Controller's button input

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


## <a name="Protocol_Motor">Protocol::Motor</a>

Operate motor or determine the current motor inputs,
Mostly used for operate the 4 motors or to check their movement. 
Use the following structure as an array in this case :
```cpp
namespace Protocol
{
    struct Motor
    {
        u8	direction;
        s16	value;
    };
}
```

- Transport using 4 Protocol::Motor arrays in the data area. Applied to motors 0, 1, 2, 3. The order is from the left front motor to the clockwise. Drone Fighter 2017r can not reverse the motor ; these values are not applicable for motor control when using Motor::Direction:::None or Moto::Direction::Direction::None.

- direction : [Motor::Direction::Type](04_definitions.md#Motor_Direction)
- value : 0 ~ 4095


<br>
<br>

## <a name="Protocol_MotorSingle">Protocol::MotorSingle</a>
Used to operate one motor or check current inputs to the motor.

```cpp
namespace Protocol
{
    struct MotorSingle
    {
        u8	target;
        u8	direction;
        s16	value;
    };
}
```
- Used to operate motor of specified number. Drone Fighter 2017 can not reverse the motor ; these values are not applicable for motor control when using Motor::Direction:::None or Moto::Direction::Direction::None.
- target : [Motor::Part::Type](04_definitions.md#Motor_Part)
- direction : [Motor::Direction::Type](04_definitions.md#Motor_Direction)
- value : 0 ~ 4095


<br>
<br>


## <a name="Protocol_JoystickBlock">Protocol::JoystickBlock</a>
Joystick input value of one axis.
```cpp
namespace Protocol
{
    struct JoystickBlock
    {
        s8      x;              // X axis(-100 ~ 100)
        s8      y;              // Y aixs(-100 ~ 100)
        u8      direction;      // Joystick direction (Joystick::Direction::Type)
        u8      event;          // Joystick event (Joystick::Event::Type)
        u8      command;        // Joystick command (Joystick::Command::Type)
    };
}
```
- x : Joystick's horizontal value, -100 ~ 100
- y : Joystick's vertical value, -100 ~ 100
- direction : [Joystick::Direction::Type](04_definitions.md#Joystick_Direction)
- event : [Joystick::Event::Type](04_definitions.md#Joystick_Event)
- command : [Joystick::Command::Type](04_definitions.md#Joystick_Command)


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
- left : [Protocol::JoystickBlock](#Protocol_JoystickBlock)
- right : [Protocol::JoystickBlock](#Protocol_JoystickBlock)


<br>
<br>


## <a name="Protocol_Buzzer">Protocol::Buzzer</a>
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
- mode : [Buzzer::Mode::Type](04_definitions.md#Buzzer_Mode)
- value : ScaleInstantally or ScaleContinually mode use [Buzzer::Scale::Type](04_definitions.md#Buzzer_Scale), HzInstantally or HzContinually mode use 0 ~ 8000(Hz)
- time : 0 ~ 65535(ms)


<br>
<br>


## <a name="Protocol_Vibrator">Protocol::Vibrator</a>
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
- mode : [Vibrator::Mode::Type](04_definitions.md#Vibrator_Mode)
- on : 0 ~ 65535(ms)
- off : 0 ~ 65535(ms)
- total : 0 ~ 65535(ms)


<br>
<br>


## <a name="Protocol_UserInterface">Protocol::UserInterface</a>
Specify the desired function for each button and joystick direction in Joystick setting mode.
```cpp
namespace Protocol
{
    struct UserInterface
    {
        u8      command;    // command
        u8      function;   // function
    };
}
```
- command : [UserInterface::Commands](04_definitions.md#UserInterface_Commands)
- function : [UserInterface::Functions](04_definitions.md#UserInterface_Functions)


<br>
<br>


## <a name="Protocol_Pairing">Protocol::Pairing</a>
Used to pairing the device.
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
- addressLocal : 0x0001 ~ 0xFFFE, 0x0000은 사용하지 않음, 0xFFFF는 Broadcasting에 사용
- addressRemote : 0x0001 ~ 0xFFFE, 0x0000은 사용하지 않음, 0xFFFF는 Broadcasting에 사용
- channel : 0 ~ 255(Undetermination)

<br>

---

### DRONE FIGHTER 2017

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. ***Structs***
6. [Structs - Light](06_structs_light.md)

<br>

[Index](index.md)
