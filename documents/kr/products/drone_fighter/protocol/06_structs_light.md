***DRONEFIGHTER2017 / Protocol / Structs / Light***<br>
Modified : 2017.10.18

---

#### LED 제어와 관련된 정의 및 구조체들을 소개합니다.

---

<br>
<br>

# Definitions

<br>

## <a name="Light_Drone_Mode">Light::Drone::Mode::Type</a>
드론 LED 모드 또는 이벤트 명령 시 동작 모드를 지정할 때 사용합니다.

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
                EyeManual,              // 수동 제어
                EyeHold,                // 지정한 색상을 계속 켬
                EyeFlicker,             // 깜빡임         
                EyeFlickerDouble,       // 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)            
                EyeDimming,             // 밝기 제어하여 천천히 깜빡임
                
                ArmNone = 0x40,         
                ArmManual,              // 수동 제어
                ArmHold,                // 지정한 색상을 계속 켬
                ArmFlicker,             // 깜빡임         
                ArmFlickerDouble,       // 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)            
                ArmDimming,             // 밝기 제어하여 천천히 깜빡임
                
                EndOfType
            };
        }
    }
}
```

<br>
<br>

## <a name="Light_Drone_Flags">Light::Drone::Flags::Type</a>
드론 LED를 직접 지정하여 제어할 때 사용합니다.

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
조종기 LED 모드 또는 이벤트 명령 시 동작 모드를 지정할 때 사용합니다.

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
                
                Manual,                         ///< 수동 조작
                
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
                
                Team,                           ///< 팀 표시
                
                
                EndOfType
            };
        }
    }
}
```

<br>
<br>

## <a name="Light_Controller_Flags">Light::Controller::Flags::Type</a>
드론 LED를 직접 지정하여 제어할 때 사용합니다.

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
선택한 LED의 밝기를 직접 조정합니다.
```cpp
namespace Protocol
{
    namespace Light
    {
        struct Manual
        {
            u8  flags;         // Flags 열거형을 조합한 값
            u8  brightness;    // 밝기     
        };
    }
}
```
- flags : [Light::Drone::Flags](#Light_Drone_Flags), [Light::Controller::Flags](#Light_Controller_Flags)
- brightness : 0 ~ 255 사이의 값. 값이 클수록 밝음


<br>
<br>


## <a name="Protocol_Light_Mode">Protocol::Light::Mode</a>
LED 모드 변경
```cpp
namespace Protocol
{
    namespace Light
    {
        struct Mode
        {
            u8      mode;       // LED 모드
            u16     interval;   // LED 모드의 갱신 주기
        };
    }
}
```
- mode : [Light::Drone::Mode::Type](#Light_Drone_Mode), [Light::Controller::Mode::Type](#Light_Controller_Mode)
- interval : 0 ~ 65535


<br>
<br>


## <a name="Protocol_Light_ModeCommand">Protocol::Light::ModeCommand</a>
LED 모드 변경과 명령을 전달합니다.
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
LED 모드 변경과 명령, IR 데이터 전송.
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
LED 이벤트 실행
```cpp
namespace Protocol
{
    namespace Light
    {
        struct Event
        {
            u8      event;      // LED 이벤트
            u16     interval;   // LED 이벤트 갱신 주기
            u8      repeat;     // LED 이벤트 반복 횟수
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
LED 이벤트 실행, 명령.
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
LED 이벤트 실행, 명령, IR 데이터 전송.
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
