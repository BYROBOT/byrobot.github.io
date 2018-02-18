***PETRONE / BLE / Protocol / Definitions***<br>
Modified : 2017.10.18

---

#### Basic definitions being used by PETRONE

---

<br>

## <a name="CommandType">Protocol::CommandType::Type</a>
CommandBase structure use commandType variables.

```cpp
namespace Protocol
{
    namespace CommandType
    {
        enum Type
        {
            None = 0,               //  No event
            
            // 설정
            ModeVehicle = 0x10,     //  Vehicle Mode change
            
            // 제어
            Coordinate = 0x20,      // Vehicle coordinate change
            Trim,                   // Vehicle trim change
            FlightEvent,            // Vehicle flight event
            DriveEvent,             // Vehicle drive event
            Stop,                   // Vehicle stop정지
            
            ResetHeading = 0x50,    // Reset heading for absolute coordinate
            ClearGyroBiasAndTrim,   // Clear gyro bias
            ClearTrim,              // Vehicle trim clear
            
            // 요청
            Request = 0x90,         // Request data.
            
            EndOfType
        };
    }
}
```

<br>
<br>

## <a name="DeviceType">System::DeviceType::Type</a>
Device type.<br>
Used mostly to determine version of device firmware.

```cpp
namespace System
{
    namespace DeviceType
    {
        enum Type
        {
            None,
			
            PetroneMain,
            PetroneSub,
            Link,
			
            EndOfType
        };
    }
}
```

<br>
<br>

## <a name="ModeUpdate">System::ModeUpdate::Type</a>
Firmware update state.

```cpp
namespace System
{
    namespace ModeUpdate
    {
        enum Type
        {
            None,       // Cannot update firmware(Debug mode, etc.)

            Ready,      // Ready for update.
            Update,     // Firmware updating
            Complete,   // Firmware update complete

            Faild,      // Update Faild( Ex: Update has reached completion but firmware data body CRC16 does not match, etc.)

            EndOfType
        };
    }
}
```

<br>
<br>

## <a name="ImageType">System::ImageType::Type</a>
Firmware image type

```cpp
namespace System
{
    namespace ImageType
    {
        enum Type
        {
            None,

            // Used device image
            ImageA,
            ImageB,

            // Firmware image
            RawImageA,
            RawImageB,

            EncryptedImageA,
            EncryptedImageB,

            // Current image
            ImageSingle,

            // Current device image
            RawImageSingle,
            EncryptedImageSingle,

            EndOfType
        };
    }
}
```

<br>
<br>

## <a name="ModeVehicle">System::ModeVehicle::Type</a>
PETRONE Vehicle Mode


```cpp
namespace System
{
    namespace ModeVehicle
    {
        enum Type
        {
            None = 0,           // None
            
            Flight = 0x10,      // Flight with guard
            FlightNoGuard,      // Flight No Guard
            FlightFPV,          // Flight FPV
            
            Drive = 0x20,       // Drive
            DriveFPV,           // Drive FPV
            
            EndOfType
        };
    }
    
}
```

<br>
<br>

## <a name="ModeSystem">System::ModeSystem::Type</a>

System Operating Mode

```cpp
namespace System
{
    namespace ModeSystem
    {
        enum Type
        {
            None = 0,           // None
            
            Boot,               // Booting
            Wait,               // Waiting for connect
            
            Ready,              // Ready
            
            Running,            // Running code
            
            Update,             // Firmware update
            UpdateComplete,     // Firmware update complete
            
            Error,              // Error
                
            EndOfType
        };
    }
    
}
```

<br>
<br>

## <a name="ModeFlight">System::ModeFlight::Type</a>
Flight mode - system operating 

```cpp
namespace System
{
    namespace ModeFlight
    {
        enum Type
        {
            None = 0,           // None
            
            Ready,              // Ready for fly
            
            TakeOff,            // Takeoff (Automatic transition to flight mode)
            Flight,             // Flight
            Flip,               // Flip           
            Stop,               // Force stop
            Landing,            // Landing
            Reverse,            // Reverse
            
            Accident,           // Accident (Automatic transition to Ready)
            Error,              // Error
                        
            EndOfType
        };
    }
    
}
```

<br>
<br>

## <a name="ModeDrive">System::ModeDrive::Type</a>
Drive mode - system operating

```cpp
namespace System
{
    namespace ModeDrive
    {
        enum Type
        {
            None = 0,           // None
            
            Ready,              // Ready
            
            Start,              // Start
            Drive,              // Drive
            Stop,               // Force stop
            
            Accident,           // Accident (Automatic transition to Ready)
            Error,              // Error
            
            EndOfType
        };
    }
    
}
```

<br>
<br>

## <a name="SensorOrientation">System::SensorOrientation::Type</a>
Sensor Orientation
```cpp
namespace System
{
    namespace SensorOrientation
    {
        enum Type
        {
            None = 0,           // None
            
            Normal,             // Normal
            ReverseStart,       // Reverse Start
            Reversed,           // Reversed
            
            EndOfType
        };
    }
}
```

<br>
<br>

## <a name="Direction">System::Direction::Type</a>
Direction
```cpp
namespace System
{
    namespace Direction
    {
        enum Type
        {
            None = 0,

            Left,
            Front,
            Right,
            Rear,
            
            EndOfType
        };
    }
}
```

<br>
<br>

## <a name="Coordinate">System::Coordinate::Type</a>
PETRONE control coordinate.

- **World** mode : The Absolute mode. The reference directions is fixed in the ***direction of view when the drones are takeoff***.

- **Normal** : Moves on the direction the drone is looking.

```cpp
namespace System
{
    namespace Coordinate
    {
        enum Type
        {
            None = 0,           //None없음
            
            World,              // Absolute axis
            Local,              // Normal axis
            
            EndOfType
        };
    }
}
```

<br>
<br>

## <a name="Trim">System::Trim::Type</a>
If PETRONE flows in one direction. Adjust the orientation to allow hovering. The value changes for each transfer.

```cpp
namespace System
{
    namespace Trim
    {
        enum Type
        {
            None = 0,           // None
 
            RollIncrease,       // Roll Increase
            RollDecrease,       // Roll Decrease              
            PitchIncrease,      // Pitch Increase
            PitchDecrease,      // Pitch Decrease             
            YawIncrease,        // Yaw Increase
            YawDecrease,        // Yaw Decrease               
            ThrottleIncrease,   // Throttle Increase
            ThrottleDecrease,   // Throttle Decrease
            
            EndOfType
        };
    }
}
```

<br>
<br>

## <a name="FlightEvent">System::FlightEvent::Type</a>
Excute PETRONE Flight event 

```cpp
namespace System
{
    namespace FlightEvent
    {
        enum Type
        {
            None = 0,           // none
            
            TakeOff,            // takeoff
            
            FlipFront,          // flip front(Not Yet)
            FlipRear,           // flip rear(Not Yet)
            FlipLeft,           // flip left(Not Yet)
            FlipRight,          // flip right(Not Yet)
            
            Stop,               // Force stop
            Landing,            // landing
            Reverse,            // reverse
            
            Shot,               // IR shot action
            UnderAttack,        // IR shot recieve action
            
            EndOfType   
        };
    }
}
```

<br>
<br>

## <a name="LightMode">Light::Mode::Type</a>

Drone LED mode change or use to specify the action mode for event commands.

```cpp
namespace Light
{
    namespace Mode
    {
        enum Type
        {
            None,
            
            EyeNone = 0x10,
            EyeHold,            // Eye LED color Hold 
            EyeMix,             // Eye LED change color Sequential
            EyeFlicker,         // Eye LED flicker light          
            EyeFlickerDouble,   // Eye LED flicker light (Blinking twice and turning off as much as the blinking time.)
            EyeDimming,         // Eye LED Dimming
            
            ArmNone = 0x40,     
            ArmHold,            // Arm LED color Hold
            ArmMix,             // Arm LED change color Sequential
            ArmFlicker,         // Arm LED flicker light          
            ArmFlickerDouble,   // Arm LED flicker light (Blinking twice and turning off as much as the blinking time.)   
            ArmDimming,         // Arm LED Dimming
            ArmFlow,            // Arm LED flow first to second color      
            ArmFlowReverse,     // Arm LED flow second to first color
            
            EndOfType
        };
    }
}
```

<br>
<br>

## <a name="LightColors">Light::Colors::Type</a>
LED Color palette index

Colour index of the palette defined inside the drones and the controls.
Please recommend using it after testing. May differ from the color intended.

```cpp
namespace Light
{
    namespace Colors
    {
        enum Type
        {
            AliceBlue,
            AntiqueWhite,
            Aqua,
            Aquamarine,
            Azure,
            Beige,
            Bisque,
            Black,
            BlanchedAlmond,
            Blue,
            BlueViolet,
            Brown,
            BurlyWood,
            CadetBlue,
            Chartreuse,
            Chocolate,sss
            Coral,
            CornflowerBlue,
            Cornsilk,
            Crimson,
            Cyan,
            DarkBlue,
            DarkCyan,
            DarkGoldenRod,
            DarkGray,
            DarkGreen,
            DarkKhaki,
            DarkMagenta,
            DarkOliveGreen,
            DarkOrange,
            DarkOrchid,
            DarkRed,
            DarkSalmon,
            DarkSeaGreen,
            DarkSlateBlue,
            DarkSlateGray,
            DarkTurquoise,
            DarkViolet,
            DeepPink,
            DeepSkyBlue,
            DimGray,
            DodgerBlue,
            FireBrick,
            FloralWhite,
            ForestGreen,
            Fuchsia,
            Gainsboro,
            GhostWhite,
            Gold,
            GoldenRod,
            Gray,
            Green,
            GreenYellow,
            HoneyDew,
            HotPink,
            IndianRed,
            Indigo,
            Ivory,
            Khaki,
            Lavender,
            LavenderBlush,
            LawnGreen,
            LemonChiffon,
            LightBlue,
            LightCoral,
            LightCyan,
            LightGoldenRodYellow,
            LightGray,
            LightGreen,
            LightPink,
            LightSalmon,
            LightSeaGreen,
            LightSkyBlue,
            LightSlateGray,
            LightSteelBlue,
            LightYellow,
            Lime,
            LimeGreen,
            Linen,
            Magenta,
            Maroon,
            MediumAquaMarine,
            MediumBlue,
            MediumOrchid,
            MediumPurple,
            MediumSeaGreen,
            MediumSlateBlue,
            MediumSpringGreen,
            MediumTurquoise,
            MediumVioletRed,
            MidnightBlue,
            MintCream,
            MistyRose,
            Moccasin,
            NavajoWhite,
            Navy,
            OldLace,
            Olive,
            OliveDrab,
            Orange,
            OrangeRed,
            Orchid,
            PaleGoldenRod,
            PaleGreen,
            PaleTurquoise,
            PaleVioletRed,
            PapayaWhip,
            PeachPuff,
            Peru,
            Pink,
            Plum,
            PowderBlue,
            Purple,
            RebeccaPurple,
            Red,
            RosyBrown,
            RoyalBlue,
            SaddleBrown,
            Salmon,
            SandyBrown,
            SeaGreen,
            SeaShell,
            Sienna,
            Silver,
            SkyBlue,
            SlateBlue,
            SlateGray,
            Snow,
            SpringGreen,
            SteelBlue,
            Tan,
            Teal,
            Thistle,
            Tomato,
            Turquoise,
            Violet,
            Wheat,
            White,
            WhiteSmoke,
            Yellow,
            YellowGreen,
            
            EndOfColor
        };
    }
}
```


<br>

---

### PETRONE

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. ***Definitions***
5. [Base Structs](05_base_structs.md)
6. [Structs](06_structs.md)
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

