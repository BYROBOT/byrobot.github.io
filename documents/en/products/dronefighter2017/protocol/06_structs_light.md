***DRONEFIGHTER2017 / Protocol / Structs / Light***<br>
Modified : 2018.02.12

---

#### Introduce the definitions and structures involved in LED control.

---

<br>
<br>

# Definitions

<br>

## <a name="Light_Drone_Mode">Light::Drone::Mode::Type</a>
Used to specify the Drone LED mode or event commands. 

```cpp
namespace Light
{
    namespace Drone
    {
        namespace Mode
        {
            enum Type
            {
                None,
                
                EyeNone = 0x10,
                EyeManual,              // Eye LED color Manual control
                EyeHold,                // Eye LED color Hold 
                EyeFlicker,             // Eye LED flicker light        
                EyeFlickerDouble,       // Eye LED flicker light (Blinking twice and turning off as much as the blinking time.)            
                EyeDimming,             // Eye LED Dimming
                
                ArmNone = 0x40,         
                ArmManual,              // Arm LED color Manual control
                ArmHold,                // Arm LED color Hold 
                ArmFlicker,             // Arm LED flicker light        
                ArmFlickerDouble,       // Arm LED flicker light (Blinking twice and turning off as much as the blinking time.)               
                ArmDimming,             // Arm LED Dimming
                
                EndOfType
            };
        }
    }
}
```

<br>
<br>

## <a name="Light_Drone_Flags">Light::Drone::Flags::Type</a>
Used to control the drone LED directly.

```cpp
namespace Light
{
    namespace Drone
    {
        namespace Flags
        {
            enum Type
            {
                None        = 0x00,

                FrontOut    = 0x80,
                FrontIn     = 0x40,

                RearIn      = 0x20,
                RearOut     = 0x10,

                Blue        = 0x08,
                Red         = 0x04
            };
        }
    }
}
```

<br>
<br>

## <a name="Light_Controller_Mode">Light::Controller::Mode::Type</a>
Used to specify the mode of controller LED or Operation for event command.

```cpp
namespace Light
{
    namespace Controller
    {
        namespace Mode
        {
            enum Type
            {
                None,
                
                Manual,                         ///<  Manual control
                
                // Team
                TeamNone = 0x10,
                
                TeamHoldRed,
                TeamHoldBlue,
                TeamHoldAll,
                
                TeamFlickerRed,
                TeamFlickerBlue,
                TeamFlickerAll,
                TeamFlickerSeesaw,
                
                TeamFlickerDoubleRed,
                TeamFlickerDoubleBlue,
                TeamFlickerDoubleAll,
                
                TeamDimmingRed,
                TeamDimmingBlue,
                TeamDimmingAll,
                TeamDimmingSeesaw,
                
                Team,                           ///< Team display
                
                
                EndOfType
            };
        }
    }
}
```

<br>
<br>

## <a name="Light_Controller_Flags">Light::Controller::Flags::Type</a>
Manually control for the selected LED.

```cpp
namespace Light
{
    namespace Controller
    {
        namespace Flags
        {
            enum Type
            {
                None        = 0x00,

                Yellow0     = 0x80,
                Yellow1     = 0x40,
                Green0      = 0x20,
                Green1      = 0x10,
                White0      = 0x08,
                White1      = 0x04,

                Blue        = 0x02,
                Red         = 0x01
            };
        }
    }
}
```

<br>
<br>

# Structs

<br>
<br>


## <a name="Protocol_Light_Manual">Protocol::Light::Manual</a>
Manually adjust the brightness of the selected LED.

```cpp
namespace Protocol
{
    namespace Light
    {
        struct Manual
        {
            u8  flags;         // Flags enumeration value
            u8  brightness;    // brightness     
        };
    }
}
```
- flags : [Light::Drone::Flags](#Light_Drone_Flags), [Light::Controller::Flags](#Light_Controller_Flags)
- brightness : 0 ~ 255 사이의 값. 값이 클수록 밝음


<br>
<br>


## <a name="Protocol_Light_Mode">Protocol::Light::Mode</a>
LED mode change
```cpp
namespace Protocol
{
    namespace Light
    {
        struct Mode
        {
            u8      mode;       // LED mode
            u16     interval;   // LED mode interval
        };
    }
}
```
- mode : [Light::Drone::Mode::Type](#Light_Drone_Mode), [Light::Controller::Mode::Type](#Light_Controller_Mode)
- interval : 0 ~ 65535


<br>
<br>


## <a name="Protocol_Light_ModeCommand">Protocol::Light::ModeCommand</a>
LED mode change and event execution,
```cpp
namespace Protocol
{
    namespace Light
    {
        struct ModeCommand
        {
            Protocol::Light::Mode   mode;
            Protocol::Command       command;
        };
    }
}
```
- mode : [Protocol::Light::Mode](#Protocol_Light_Mode)
- command : [Protocol::Command](05_structs.md#Protocol_Command)


<br>
<br>


## <a name="Protocol_Light_ModeCommandIr">Protocol::Light::ModeCommandIr</a>
LED mode change and event execution, IR data transfer.
```cpp
namespace Protocol
{
    namespace Light
    {
        struct ModeCommandIr
        {
            Protocol::Light::Mode   mode;
            Protocol::Command       command;
            u32                     irData;
        };
    }
}
```
- mode : [Protocol::Light::Mode](#Protocol_Light_Mode)
- command : [Protocol::Command](05_structs.md#Protocol_Command)


<br>
<br>


## <a name="Protocol_Light_Event">Protocol::Light::Event</a>
LED event execution
```cpp
namespace Protocol
{
    namespace Light
    {
        struct Event
        {
            u8      event;      // LED event
            u16     interval;   // LED event interval
            u8      repeat;     // LED event repeat count
        };
    }
}
```
- event : [Light::Drone::Mode::Type](#Light_Drone_Mode), [Light::Controller::Mode::Type](#Light_Controller_Mode)
- interval : 0 ~ 65535
- repeat : 0 ~ 255


<br>
<br>


## <a name="Protocol_Light_EventCommand">Protocol::Light::EventCommand</a>
LED event execution, command.
```cpp
namespace Protocol
{
    namespace Light
    {
        struct EventCommand
        {
            Protocol::Light::Event  event;
            Protocol::Command       command;
        };
    }
}
```
- event : [Protocol::Light::Event](#Protocol_Light_Event)
- command : [Protocol::Command](05_structs.md#Protocol_Command)


<br>
<br>


## <a name="Protocol_Light_EventCommandIr">Protocol::Light::EventCommandIr</a>
LED event execution, command, and IR data transfer.
```cpp
namespace Protocol
{
    namespace Light
    {
        struct EventCommandIr
        {
            Protocol::Light::Event  event;
            Protocol::Command       command;
            u32                     irData;
        };
    }
}
```
- event : [Protocol::Light::Event](#Protocol_Light_Event)
- command : [Protocol::Command](05_structs.md#Protocol_Command)


<br>
<br>


---

### DRONE FIGHTER 2017

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. [Structs](05_structs.md)
6. ***Structs - Light***

<br>

[Index](index.md)
