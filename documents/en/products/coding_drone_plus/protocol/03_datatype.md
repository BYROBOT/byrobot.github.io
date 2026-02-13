**[Coding Drone Plus](index.md)** / **Protocol** / **DataType**

Modified : 2026.1.29

---

#### Data type

---

<br>

<a name="Protocol_DataType"></a>
## Protocol::DataType::Type
Data type

```cpp
namespace Protocol
{
    namespace DataType
    {
        enum Type
        {
            // Generic
            None                        = 0x00,     // None
            Ping                        = 0x01,     // Communication check
            Ack                         = 0x02,     // Response acknowledging data reception
            Error                       = 0x03,     // Error
            Request                     = 0x04,     // Request for data of a specified type
            Address                     = 0x06,     // Device address (MAC if available, otherwise UUID)
            Information                 = 0x07,     // Firmware and device information
            Update                      = 0x08,     // Firmware update
            UpdateLocation              = 0x09,     // Firmware update location correction
            Monitor                     = 0x0F,     // Debug value array(1 byte: type, 2 bytes: page)
            Control                     = 0x10,     // Control input
            Command                     = 0x11,     // Command
            Pairing                     = 0x12,     // Pairing
            ResponseRate                = 0x13,     // Response rate configuration
            cpuId                       = 0x1E,     // CPU ID

            // Light
            LED_rainbow                 = 0x24,     // Continuous rainbow color pattern
            LED_flicker                 = 0x25,     // LED flickering(blinking) behavior
            LED_random                  = 0x26,     // Randomly changing colors or patterns
            LED_individual              = 0x27,     // Individual/custom control of each LED

            // Raw Data
            RawMotion                   = 0x30,     // Raw motion sensor data
            RawFlow                     = 0x31,     // Raw flow sensor data

            // State, Sensor
            State                       = 0x40,     // Drone status(flight mode, heading reference, battery level)
            Attitude                    = 0x41,     // Drone attitude(angles)
            Position                    = 0x42,     // Position
            Altitude                    = 0x43,     // Height / altitude
            Motion                      = 0x44,     // Processed motion sensor data(IMU)
            Range                       = 0x45,     // Distance sensor data
            Flow                        = 0x46,     // Optical flow sensor data

            // Setting
            Count                       = 0x50,     // Counter
            Bias                        = 0x51,     // Accelerometer / gyroscope bias
            Trim                        = 0x52,     // Trim
            LostConnection              = 0x53,     // Response time setting after connection loss

            // Device
            Motor                       = 0x60,     // Motor control and current control values
            MotorSingle                 = 0x61,     // Single motor control
            Buzzer                      = 0x62,     // Buzzer control
            Vibrator                    = 0x63,     // Vibration control
            Battery                     = 0x64,     // Battery information

            // Input
            Button                      = 0x70,     // Button data
            Joystick                    = 0x71,     // Joystick data(controller)

            // Information Assembled
            InformationAssembledForController       = 0xA0,     // Aggregated data (for controller)
            InformationAssembledForEntry            = 0xA1,     // Aggregated data (for Entry)
            InformationAssembledForByBlocks         = 0xA2,     // Aggregated data (block-based)

            EndOfType
        };
    }
}
```


<br>
<br>

Link that connects the structures associated with each DataType.

| Category | Data Type | Hex Value | Description |
|:--|:--|:--:|:--|
| Generic | None | 0x00 | None |
| Generic | Ping | 0x01 | Communication check |
| Generic | Ack | 0x02 | Response acknowledging data reception |
| Generic | Error | 0x03 | Error |
| Generic | Request | 0x04 | Request for data of a specified type |
| Generic | Address | 0x06 | Device address (MAC if available, otherwise UUID) |
| Generic | Information | 0x07 | Firmware and device information |
| Generic | Update | 0x08 | Firmware update |
| Generic | UpdateLocation | 0x09 | Firmware update location correction |
| Generic | Monitor | 0x0F | Transmission of value array for debugging (1 byte: type, 2 bytes: page) |
| Generic | Control | 0x10 | Control input |
| Generic | Command | 0x11 | Command |
| Generic | Pairing | 0x12 | Pairing |
| Generic | ResponseRate | 0x13 | Response rate configuration |
| Generic | cpuId | 0x1E | CPU ID |
| Light | LED_rainbow | 0x24 | Controls LEDs with a continuous rainbow color pattern |
| Light | LED_flicker | 0x25 | Controls LED flickering (blinking) behavior |
| Light | LED_random | 0x26 | Controls LEDs with randomly changing colors or patterns |
| Light | LED_individual | 0x27 | Allows individual and custom control of each LED |
| Raw Data | RawMotion | 0x30 | Raw motion sensor data |
| Raw Data | RawFlow | 0x31 | Raw flow sensor data |
| State, Sensor | State | 0x40 | Drone status (flight mode, heading reference, battery level) |
| State, Sensor | Attitude | 0x41 | Drone attitude (angles) |
| State, Sensor | Position | 0x42 | Position |
| State, Sensor | Altitude | 0x43 | Height / altitude |
| State, Sensor | Motion | 0x44 | Processed motion sensor data (IMU) |
| State, Sensor | Range | 0x45 | Distance sensor data |
| State, Sensor | Flow | 0x46 | Optical flow sensor data |
| Setting | Count | 0x50 | Counter |
| Setting | Bias | 0x51 | Accelerometer / gyroscope bias |
| Setting | Trim | 0x52 | Trim |
| Setting | LostConnection | 0x53 | Response time setting after connection loss |
| Device | Motor | 0x60 | Motor control and current control values |
| Device | MotorSingle | 0x61 | Single motor control |
| Device | Buzzer | 0x62 | Buzzer control |
| Device | Vibrator | 0x63 | Vibration control |
| Device | Battery | 0x64 | Battery information |
| Input | Button | 0x70 | Button data |
| Input | Joystick | 0x71 | Joystick data(controller) |
| Information Assembled | InformationAssembledForController | 0xA0 | Aggregated data (for controller) |
| Information Assembled | InformationAssembledForEntry | 0xA1 | Aggregated data (for Entry) |
| Information Assembled | InformationAssembledForByBlocks | 0xA2 | Aggregated data (block-based) |

<br>

---

<h3>Coding Drone Plus</H3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. ***DataType***
4. [Definitions](04_definitions.md)
5. [Structs](05_structs.md)
6. [Structs - Light](06_structs_light.md)
<!-- 7. [Structs - Display](07_structs_display.md) -->

<br>

[Index](index.md)
