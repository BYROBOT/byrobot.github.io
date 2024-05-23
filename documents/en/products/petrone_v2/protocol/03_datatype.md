**[PETRONE_V2](index.md)** / **Protocol** / **DataType**

Modified : 2018.02.14

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
            Ping                        = 0x01,     // ping device
            Ack                         = 0x02,     // Response to data receive
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
            AccelBias,                              // Drone accelometer bias(Vector)
            GyroBias,                               // Drone gyro bias
            TrimAll,                                // Drone trim all
            TrimFlight,                             // Drone trim flight
            TrimDrive,                              // Drone trim drive
    
            // Sensor raw data      
            Imu                         = 0x50,     // IMU Raw
            Pressure,                               // Pressure sensor
            Battery,                                // Battery
            Range,                                  // Range sensor
            ImageFlow,                              // Image Flow
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
    
            // 카운트       
            CountFlight                 = 0x90,     // count of flight
            CountDrive,                             //count of drive
                    
            // RF       
            Pairing                     = 0xA0,     // pairing
            Rssi,                                   // RSSI

            // Display
            DisplayClear                = 0xB0,     // Display Clear
            DisplayInvert,                          // Invert display 
            DisplayDrawPoint,                       // Display draw point
            DisplayDrawLine,                        // Display draw line
            DisplayDrawRect,                        // Display draw rect
            DisplayDrawCircle,                      // Display draw circle
            DisplayDrawString,                      // Display draw string
            DisplayDrawStringAlign,                 // Display draw string align

            // Information Assembled
            InformationAssembledForController       = 0xD0,     // Assembled information datas(Controller)
            InformationAssembledForEntry            = 0xD1,     // Assembled information datas(Entry)

            EndOfType
        };
    }
}
```


<br>
<br>

Link that connects the structures associated with each DataType.

| Name                      | Value | Target | Description                         | Structure |
|:--------------------------------------|:----:|:----:|:-----------------------------------------------|:--------|
| None                                  | 0x00 | -    | none                                           | &nbsp; |
| Ping                                  | 0x01 | A    | Communication verification             | [Protocol::Ping](05_structs.md#Protocol_Ping) |
| Ack                                   | 0x02 | A    | Response to data receive                | [Protocol::Ack](05_structs.md#Protocol_Ack) |
| Error                                 | 0x03 | -    | Error(reserve, Specify Bit Flag Later)    | [Protocol::Error](05_structs.md#Protocol_Error) |
| Request                               | 0x04 | A    | Request data of the specified type         | [Protocol::Request](05_structs.md#Protocol_Request) |
| Message                               | 0x05 | -    | String data                                 | &nbsp; |
| Reserved_1                            | 0x06 | -    | Reserved_1                                    | &nbsp; |
| Reserved_2                            | 0x07 | -    | Reserved_2                                    | &nbsp; |
| Monitor                               | 0x08 | D    | Send array of values for debugging            | &nbsp; |
| SystemCounter                         | 0x09 | A    | System counter                             | &nbsp; |
| Information                           | 0x0A | A    | Firmware and device information         | [Protocol::Information](05_structs.md#Protocol_Information) |
| UpdateLocation                        | 0x0B | A    | Firmware update position correction          | &nbsp; |
| Update                                | 0x0C | A    | Firmware update                            | &nbsp; |
| Encrypt                               | 0x0D | -    | Firmware encrypt                            | &nbsp; |
| Address                               | 0x0E | A    | Device address                              | [Protocol::Address](05_structs.md#Protocol_Address) |
| Administrator                         | 0x0F | -    | Obtain Administrator Permissions           | &nbsp; |
| Control                               | 0x10 | D    | Control command                              | [Control::Double8](05_structs.md#Control_Double8), [Control::Quad8](05_structs.md#Control_Quad8) |
| Command                               | 0x11 | A    | Command                                     | [Protocol::Command](05_structs.md#Protocol_Command) |
| LightManual                           | 0x20 | A    | LED manual control                           | [Protocol::Light::Manual](06_structs_light.md#Protocol_Light_Manual) |
| LightMode                             | 0x21 | -    | LED mode               | [Protocol::Light::Mode](06_structs_light.md#Protocol_Light_Mode) |
| LightModeCommand                      | 0x22 | -    | LED mode, command           | [Protocol::Light::ModeCommand](06_structs_light.md#Protocol_Light_ModeCommand) |
| LightModeCommandIr                    | 0x23 | -    | LED mode, command, IR           | [Protocol::Light::ModeCommandIr](06_structs_light.md#Protocol_Light_ModeCommandIr) |
| LightModeColor                        | 0x24 | A    | LED mode 3 colors           | [Protocol::Light::ModeColor](06_structs_light.md#Protocol_Light_ModeColor) |
| LightModeColorCommand                 | 0x25 | A    | LED mode 3 colors, command  | [Protocol::Light::ModeColorCommand](06_structs_light.md#Protocol_Light_ModeColorCommand) |
| LightModeColorCommandIr               | 0x26 | A    | LED mode 3 colors, command, IR  | [Protocol::Light::ModeColorCommandIr](06_structs_light.md#Protocol_Light_ModeColorCommandIr) |
| LightModeColors                       | 0x27 | A    | LED mode palette                                | [Protocol::Light::ModeColors](06_structs_light.md#Protocol_Light_ModeColors) |
| LightModeColorsCommand                | 0x28 | A    | LED mode palette, command                        | [Protocol::Light::ModeColorsCommand](06_structs_light.md#Protocol_Light_ModeColorsCommand) |
| LightModeColorsCommandIr              | 0x29 | A    | LED mode palette, command, IR                    | [Protocol::Light::ModeColorsCommandIr](06_structs_light.md#Protocol_Light_ModeColorsCommandIr) |
| LightEvent                            | 0x2A | -    | LED event                                     | [Protocol::Light::Event](06_structs_light.md#Protocol_Light_Event) |
| LightEventCommand                     | 0x2B | -    | LED event, command    | [Protocol::Light::EventCommand](06_structs_light.md#Protocol_Light_EventCommand) |
| LightEventCommandIr                   | 0x2C | -    | LED event, command, IR    | [Protocol::Light::EventCommandIr](06_structs_light.md#Protocol_Light_EventCommandIr) |
| LightEventColor                       | 0x2D | A    | LED event 3 colors | [Protocol::Light::EventColor](06_structs_light.md#Protocol_Light_EventColor) |
| LightEventColorCommand                | 0x2E | A    | LED event 3 colors, command    | [Protocol::Light::EventColorCommand](06_structs_light.md#Protocol_Light_EventColorCommand) |
| LightEventColorCommandIr              | 0x2F | A    | LED event 3 colors, command, IR    | [Protocol::Light::EventColorCommandIr](06_structs_light.md#Protocol_Light_EventColorCommandIr) |
| LightEventColors                      | 0x30 | A    | LED event palette                              | [Protocol::Light::EventColors](06_structs_light.md#Protocol_Light_EventColors) |
| LightEventColorsCommand               | 0x31 | A    | LED event palette, command                      | [Protocol::Light::EventColorsCommand](06_structs_light.md#Protocol_Light_EventColorsCommand) |
| LightEventColorsCommandIr             | 0x32 | A    | LED event palette, command, IR                  | [Protocol::Light::EventColorsCommandIr](06_structs_light.md#Protocol_Light_EventColorsCommandIr) |
| LightModeDefaultColor                 | 0x33 | D    | LED mode default 3 colors                            | [Protocol::Light::ModeColor](06_structs_light.md#Protocol_Light_ModeColor) |
| State                                 | 0x40 | D    | Drone status                                  | [Protocol::State](05_structs.md#Protocol_State) |
| Attitude                              | 0x41 | D    | Drone Attitude(Angle)                       | [Protocol::Attitude](05_structs.md#Protocol_Attitude) |
| AccelBias                             | 0x42 | D    | Drone Accel bias                             | [Protocol::AccelBias](05_structs.md#Protocol_AccelBias) |
| GyroBias                              | 0x43 | D    | Drone gyro bias                              | [Protocol::GyroBias](05_structs.md#Protocol_GyroBias) |
| TrimAll                               | 0x44 | D    | All trim                                      | [Protocol::TrimAll](05_structs.md#Protocol_TrimAll) |
| TrimFlight                            | 0x45 | D    | Flight trim                                       | [Protocol::TrimFlight](05_structs.md#Protocol_TrimFlight) |
| TrimDrive                             | 0x46 | D    | Drive trime                                       | [Protocol::TrimDrive](05_structs.md#Protocol_TrimDrive) |
| Imu                                   | 0x50 | D    | IMU(Accel, Gyro, Angle)                        | [Protocol::Imu](05_structs.md#Protocol_Imu) |
| Pressure                              | 0x51 | D    | Pressure sensor data                             | [Protocol::Pressure](05_structs.md#Protocol_Pressure) |
| Battery                               | 0x52 | D    | Battery                                         | [Protocol::Battery](05_structs.md#Protocol_Battery) |
| Range                                 | 0x53 | D    | Range sensor                                      | [Protocol::Range](05_structs.md#Protocol_Range) |
| ImageFlow                             | 0x54 | D    | ImageFlow                                      | [Protocol::ImageFlow](05_structs.md#Protocol_ImageFlow) |
| CameraImage                           | 0x55 | D    | CameraImage                                    | &nbsp; |
| Button                                | 0x70 | A    | Button input                                   | [Protocol::Button](05_structs.md#Protocol_Button) |
| Joystick                              | 0x71 | C    | Joystick input                                   | [Protocol::Joystick](05_structs.md#Protocol_Joystick) |
| Motor                                 | 0x80 | D    | Motor control and check current value                  | [Protocol::Motor](05_structs.md#Protocol_Motor) |
| MotorSingle                           | 0x81 | D    | Single motor control                            | [Protocol::MotorSingle](05_structs.md#Protocol_MotorSingle) |
| IrMessage                             | 0x82 | D    | IR data send & recieve                              | [Protocol::IrMessage](05_structs.md#Protocol_IrMessage) |
| Buzzer                                | 0x83 | C    | Buzzer control                                     | [Protocol::Buzzer](05_structs.md#Protocol_Buzzer) |
| Vibrator                              | 0x84 | C    | Vibrator control                               | [Protocol::Vibrator](05_structs.md#Protocol_Vibrator) |
| CountFlight                           | 0x90 | D    | count of flight log         | [Protocol::CountFlight](05_structs.md#Protocol_CountFlight) |
| CountDrive                            | 0x91 | D    | count of dirve log          | [Protocol::CountDrive](05_structs.md#Protocol_CountDrive) |
| Pairing                               | 0xA0 | A    | Pairing                                         | [Protocol::Pairing](05_structs.md#Protocol_Pairing) |
| Rssi                                  | 0xA1 | A    | RSSI                                           | [Protocol::Rssi](05_structs.md#Protocol_Rssi) |
| DisplayClear                          | 0xB0 | C    | Clear controller display        | [Protocol::Display::ClearAll](07_structs_display.md#Protocol_Display_ClearAll), [Protocol::Display::Clear](07_structs_display.md#Protocol_Display_Clear)   |
| DisplayInvert                         | 0xB1 | C    | Invert controller display                                     | [Protocol::Display::Invert](07_structs_display.md#Protocol_Display_Invert) |
| DisplayDrawPoint                      | 0xB2 | C    | Display draw point              | [Protocol::Display::DrawPoint](07_structs_display.md#Protocol_Display_DrawPoint) |
| DisplayDrawLine                       | 0xB3 | C    | Display draw line               | [Protocol::Display::DrawLine](07_structs_display.md#Protocol_Display_DrawLine) |
| DisplayDrawRect                       | 0xB4 | C    | Display draw rectangle          | [Protocol::Display::DrawRect](07_structs_display.md#Protocol_Display_DrawRect) |
| DisplayDrawCircle                     | 0xB5 | C    | Display draw circle             | [Protocol::Display::DrawCircle](07_structs_display.md#Protocol_Display_DrawCircle) |
| DisplayDrawString                     | 0xB6 | C    | Display draw string             | [Protocol::Display::DrawString](07_structs_display.md#Protocol_Display_DrawString) |
| DisplayDrawStringAlign                | 0xB7 | C    | Display draw string with align  | [Protocol::Display::DrawStringAlign](07_structs_display.md#Protocol_Display_DrawStringAlign) |
| InformationAssembledForController     | 0xD0 | D    | Assembled information datas(Controller)      | [Protocol::InformationAssembledForController](05_structs.md#Protocol_InformationAssembledForController) |
| InformationAssembledForEntry          | 0xD1 | D    | Assembled information datas(Entry)  | [Protocol::InformationAssembledForEntry](05_structs.md#Protocol_InformationAssembledForEntry) |

<br>

- A: All device
- C: Controller
- D: Drone 

<br>

---

<h3>PETRONE V2</H3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. ***DataType***
4. [Definitions](04_definitions.md)
5. [Structs](05_structs.md)
6. [Structs - Light](06_structs_light.md)
7. [Structs - Display](07_structs_display.md)

<br>

[Index](index.md)
