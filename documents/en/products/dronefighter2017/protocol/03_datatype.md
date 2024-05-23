***DRONEFIGHTER2017 / Protocol / DataType***<br>
Modified : 2018.02.08

---

#### Introduce data type.

---

<br>

## <a name="Protocol_DataType">Protocol::DataType::Type</a>
Data type

```cpp
namespace Protocol
{
    namespace DataType
    {
        enum Type
        {
            None                        = 0x00,     // none
            Ping                        = 0x01,     // ping
            Ack                         = 0x02,     // ack 
            Error                       = 0x03,     // error
            Request                     = 0x04,     // Request data of the specified type
            Message                     = 0x05,     // String data
            Reserved_1                  = 0x06,     // Reserved_1
            Reserved_2                  = 0x07,     // Reserved_2
            Monitor                     = 0x08,     // Monitoring value for debug
            SystemCounter               = 0x09,     // System counter
            Information                 = 0x0A,     // Firmware information
            UpdateLocation              = 0x0B,     // Firmware update position correction
            Update                      = 0x0C,     // Firmware update
            Encrypt                     = 0x0D,     // Firmware encrypt
            Address                     = 0x0E,     // Device address
            Administrator               = 0x0F,     // Obtain Administrator Permissions
            Control                     = 0x10,     // Control command
    
            Command                     = 0x11,     // Command

            // Light
            LightManual                 = 0x20,     // LED manual control

            LightMode                   = 0x21,     // LED mode
            LightModeCommand            = 0x22,     // LED mode, Command
            LightModeCommandIr          = 0x23,     // LED mode, Command, IR
            LightModeColor              = 0x24,     // LED mode 3 colors
            LightModeColorCommand       = 0x25,     // LED mode 3 colors, Command
            LightModeColorCommandIr     = 0x26,     // LED mode 3 colors, Command, IR
            LightModeColors             = 0x27,     // LED mode palette
            LightModeColorsCommand      = 0x28,     // LED mode palette, Command
            LightModeColorsCommandIr    = 0x29,     // LED mode palette, Command, IR

            LightEvent                  = 0x2A,     // LED event
            LightEventCommand           = 0x2B,     // LED event, Command
            LightEventCommandIr         = 0x2C,     // LED event, Command, IR
            LightEventColor             = 0x2D,     // LED event 3 colors
            LightEventColorCommand      = 0x2E,     // LED event 3 colors, Command
            LightEventColorCommandIr    = 0x2F,     // LED event 3 colors, Command, IR
            LightEventColors            = 0x30,     // LED event palette
            LightEventColorsCommand     = 0x31,     // LED event palette, Command
            LightEventColorsCommandIr   = 0x32,     // LED event palette, Command, IR

            LightModeDefaultColor       = 0x33,     // LED mode default 3 color.
            
            // status, setting
            State                       = 0x40,     // Drone status
            Attitude,                               // Drone attitude
            GyroBias,                               // Drone gyro bias
            TrimAll,                                // Drone trim all
            TrimFlight,                             // Drone trim flight
            TrimDrive,                              // Drone trim drive
            UserInterface,                          // User interface
    
            // Sensor raw data      
            Imu                         = 0x50,     // IMU Raw
            Pressure,                               // Pressure sensor
            Battery,                                // Battery
            Range,                                  // Range sensor
            ImageFlow,                              // Image flow
            CameraImage,                            // Camera Image
                    
            // Input        
            Button                      = 0x70,     // button input
            Joystick,                               // joystick input
                    
            // Devices      
            Motor                       = 0x80,     // Motor control and check current value 
            MotorSingle,                            // Single motor control
            IrMessage,                              // IR data send & recieve
            Buzzer,                                 // Buzzer control
            Vibrator,                               // Vibrator control
    
            // System log       
            CountFlight                 = 0x90,     // count of flight
            CountDrive,                             // count of drive
                    
            // RF       
            Pairing                     = 0xA0,     // pairing
            Rssi,                                   // RSSI

            EndOfType
        };
    }
}
```


<br>
<br>

Link that connects the structures associated with each DataType.

| 이름                      | 값   | 대상 | 설명                                     | 구조체  |
|:--------------------------|:----:|:-:|:--------------------------------------------|:--------|
| None                      | 0x00 | - | none                                        | &nbsp; |
| Ping                      | 0x01 | A | Communication verification                  | [Protocol::Ping](05_structs.md#Protocol_Ping) |
| Ack                       | 0x02 | A | Response to data receive                    | [Protocol::Ack](05_structs.md#Protocol_Ack) |
| Error                     | 0x03 | - | Error(reserve, Specify Bit Flag Later)      | &nbsp; |
| Request                   | 0x04 | A | Request data of the specified type          | [Protocol::Request](05_structs.md#Protocol_Request) |
| Message                   | 0x05 | - | String data                                 | &nbsp; |
| Reserved_1                | 0x06 | - | Reserved_1                                  | &nbsp; |
| Reserved_2                | 0x07 | - | Reserved_2                                  | &nbsp; |
| Monitor                   | 0x08 | D | Send array of values for debugging          | &nbsp; |
| SystemCounter             | 0x09 | A | System counter                              | &nbsp; |
| Information               | 0x0A | A | Firmware and device information             | &nbsp; |
| UpdateLocation            | 0x0B | A | Firmware update position correction         | &nbsp; |
| Update                    | 0x0C | A | Firmware update                             | &nbsp; |
| Encrypt                   | 0x0D | - | Firmware encrypt                            | &nbsp; |
| Address                   | 0x0E | A | Device address                              | &nbsp; |
| Administrator             | 0x0F | - | Obtain Administrator Permissions            | &nbsp; |
| Control                   | 0x10 | D | Control command                             | [Control::Double8](05_structs.md#Control_Double8), [Control::Quad8](05_structs.md#Control_Quad8) |
| Command                   | 0x11 | A | Command                                     | [Protocol::Command](05_structs.md#Protocol_Command) |
| LightManual               | 0x20 | A | LED manual control                          | [Protocol::Light::Manual](06_structs_light.md#Protocol_Light_Manual) |
| LightMode                 | 0x21 | A | LED mode                                    | [Protocol::Light::Mode](06_structs_light.md#Protocol_Light_Mode) |
| LightModeCommand          | 0x22 | A | LED mode, command                           | [Protocol::Light::ModeCommand](06_structs_light.md#Protocol_Light_ModeCommand) |
| LightModeCommandIr        | 0x23 | A | LED mode, command, IR                       | [Protocol::Light::ModeCommandIr](06_structs_light.md#Protocol_Light_ModeCommandIr) |
| LightModeColor            | 0x24 | - | LED mode 3 colors                           | &nbsp; |
| LightModeColorCommand     | 0x25 | - | LED mode 3 colors, command                  | &nbsp; |
| LightModeColorCommandIr   | 0x26 | - | LED mode 3 colors, command, IR              | &nbsp; |
| LightModeColors           | 0x27 | - | LED mode palette                            | &nbsp; |
| LightModeColorsCommand    | 0x28 | - | LED mode palette, command                   | &nbsp; |
| LightModeColorsCommandIr  | 0x29 | - | LED mode palette, command, IR               | &nbsp; |
| LightEvent                | 0x2A | A | LED event                                   | [Protocol::Light::Event](06_structs_light.md#Protocol_Light_Event) |
| LightEventCommand         | 0x2B | A | LED event, command                          | [Protocol::Light::EventCommand](06_structs_light.md#Protocol_Light_EventCommand) |
| LightEventCommandIr       | 0x2C | A | LED event, command, IR                      | [Protocol::Light::EventCommandIr](06_structs_light.md#Protocol_Light_EventCommandIr) |
| LightEventColor           | 0x2D | - | LED event 3 colors                          | &nbsp; |
| LightEventColorCommand    | 0x2E | - | LED event 3 colors, command                 | &nbsp; |
| LightEventColorCommandIr  | 0x2F | - | LED event 3 colors, 커command드, IR          | &nbsp; |
| LightEventColors          | 0x30 | - | LED event palette                           | &nbsp; |
| LightEventColorsCommand   | 0x31 | - | LED event palette, command                  | &nbsp; |
| LightEventColorsCommandIr | 0x32 | - | LED event palette, command, IR              | &nbsp; |
| LightModeDefaultColor     | 0x33 | - | LED mode default 3 color.                   | [Protocol::Light::ModeColor](06_structs_light.md#Protocol_Light_ModeColor) |
| State                     | 0x40 | D | Drone status                                | [Protocol::State](05_structs.md#Protocol_State) |
| Attitude                  | 0x41 | D | Drone Attitude(Angle)                       | [Protocol::Attitude](05_structs.md#Protocol_Attitude) |
| GyroBias                  | 0x42 | D | Drone gyro bias                             | [Protocol::GyroBias](05_structs.md#Protocol_GyroBias) |
| TrimAll                   | 0x43 | D | All trim                                    | [Protocol::TrimAll](05_structs.md#Protocol_TrimAll) |
| TrimFlight                | 0x44 | D | Flight trim                                 | [Protocol::TrimFlight](05_structs.md#Protocol_TrimFlight) |
| TrimDrive                 | 0x45 | D | Drive trime                                 | [Protocol::TrimDrive](05_structs.md#Protocol_TrimDrive) |
| UserInterface             | 0x46 | C | User interface setting                      | [Protocol::UserInterface](05_structs.md#Protocol_UserInterface) |
| Imu                       | 0x50 | D | IMU(Accel, Gyro, Angle)                     | [Protocol::Imu](05_structs.md#Protocol_Imu) |
| Pressure                  | 0x51 | - | Pressure sensor data                        | &nbsp; |
| Battery                   | 0x52 | - | Battery                                     | &nbsp; |
| Range                     | 0x53 | - | Range sensor                                | &nbsp; |
| ImageFlow                 | 0x54 | - | Image Flow                                  | &nbsp; |
| CameraImage               | 0x55 | - | Camera Image                                | &nbsp; |
| Button                    | 0x70 | A | Button input                                | [Protocol::Button](05_structs.md#Protocol_Button) |
| Joystick                  | 0x71 | C | Joystick input                              | [Protocol::Joystick](05_structs.md#Protocol_Joystick) |
| Motor                     | 0x80 | D | Motor control and check current value       | [Protocol::Motor](05_structs.md#Protocol_Motor) |
| MotorSingle               | 0x81 | D | Single motor control                        | [Protocol::MotorSingle](05_structs.md#Protocol_MotorSingle) |
| IrMessage                 | 0x82 | D | IR data send & recieve                      | [Protocol::IrMessage](05_structs.md#Protocol_IrMessage) |
| Buzzer                    | 0x83 | C | Buzzer control                              | [Protocol::Buzzer](05_structs.md#Protocol_Buzzer) |
| Vibrator                  | 0x84 | C | Vibrator control                            | [Protocol::Vibrator](05_structs.md#Protocol_Vibrator) |
| CountFlight               | 0x90 | D | count of flight log                         | [Protocol::CountFlight](05_structs.md#Protocol_CountFlight) |
| CountDrive                | 0x91 | D | count of dirve log                          | [Protocol::CountDrive](05_structs.md#Protocol_CountDrive) |
| Pairing                   | 0xA0 | A | Pairing                                        | [Protocol::Pairing](05_structs.md#Protocol_Pairing) |
| Rssi                      | 0xA1 | - | RSSI                                        | &nbsp; |

<br>

- A: All device
- C: Controller
- D: Drone 

<br>

---

### DRONE FIGHTER 2017

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. ***DataType***
4. [Definitions](04_definitions.md)
5. [Structs](05_structs.md)
6. [Structs - Light](06_structs_light.md)

<br>

[Index](index.md)
