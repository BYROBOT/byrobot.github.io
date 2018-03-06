***PETRONE / BLE / Protocol / Definitions***<br>
Modified : 2018.3.6

---

#### Petrone에서 사용하고 있는 기본 정의들을 소개합니다.

---

* Kramdown table of contents
{:toc .toc}


<br>

## <a name="CommandType">Protocol::CommandType::Type</a>
CommandBase 구조체에서 commandType 변수에 사용합니다.

```cpp
namespace Protocol
{
    namespace CommandType
    {
        enum Type
        {
            None = 0,               // 없음
            
            // 설정
            ModeVehicle = 0x10,     // 동작 모드 전환
            
            // 제어
            Coordinate = 0x20,      // 좌표 기준 변경
            Trim,                   // 트림 변경
            FlightEvent,            // 비행 이벤트 실행
            DriveEvent,             // 주행 이벤트 실행
            Stop,                   // 정지
            
            ResetHeading = 0x50,    // 방향 초기화
            ClearGyroBiasAndTrim,   // 자이로 바이어스와 트림 설정 초기화
            ClearTrim,              // 트림 초기화
            
            // 요청
            Request = 0x90,         // 지정한 타입의 데이터 요청
            
            EndOfType
        };
    }
}
```

<br>
<br>

## <a name="DeviceType">System::DeviceType::Type</a>
장치 타입.<br>
펌웨어 정보를 요청할 때 사용합니다.

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
펌웨어 업데이트 동작 상태.

```cpp
namespace System
{
    namespace ModeUpdate
    {
        enum Type
        {
            None,       // 업데이트 불가능 상태(Debug 모드 등)

            Ready,      // 업데이트 가능 상태
            Update,     // 업데이트 중
            Complete,   // 업데이트 완료

            Faild,      // 업데이트 실패(업데이트 완료까지 갔으나 body의 CRC16이 일치하지 않는 경우)

            EndOfType
        };
    }
}
```

<br>
<br>

## <a name="ImageType">System::ImageType::Type</a>
펌웨어 이미지 타입.

```cpp
namespace System
{
    namespace ImageType
    {
        enum Type
        {
            None,

            // 현재 장치의 이미지
            ImageA,
            ImageB,

            // 펌웨어 이미지
            RawImageA,
            RawImageB,

            EncryptedImageA,
            EncryptedImageB,

            // 현재 장치의 이미지
            ImageSingle,

            // 현재 장치의 이미지
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
페트론 동작 모드를 선택합니다.

```cpp
namespace System
{
    namespace ModeVehicle
    {
        enum Type
        {
            None = 0,           // 없음
            
            Flight = 0x10,      // 비행(가드 포함)
            FlightNoGuard,      // 비행(가드 없음)
            FlightFPV,          // 비행(FPV)
            
            Drive = 0x20,       // 주행
            DriveFPV,           // 주행(FPV)
            
            EndOfType
        };
    }
    
}
```

<br>
<br>

## <a name="ModeSystem">System::ModeSystem::Type</a>
시스템 동작 상태를 나타냅니다.

```cpp
namespace System
{
    namespace ModeSystem
    {
        enum Type
        {
            None = 0,           // 없음
            
            Boot,               // 부팅
            Wait,               // 연결 대기 상태
            
            Ready,              // 대기 상태
            
            Running,            // 메인 코드 동작
            
            Update,             // 펌웨어 업데이트
            UpdateComplete,     // 펌웨어 업데이트 완료
            
            Error,              // 오류
                
            EndOfType
        };
    }
    
}
```

<br>
<br>

## <a name="ModeFlight">System::ModeFlight::Type</a>
비행 제어기 동작 상태를 나타냅니다.

```cpp
namespace System
{
    namespace ModeFlight
    {
        enum Type
        {
            None = 0,           // 없음
            
            Ready,              // 비행 준비
            
            TakeOff,            // 이륙 (Flight로 자동전환)
            Flight,             // 비행
            Flip,               // 회전           
            Stop,               // 강제 정지
            Landing,            // 착륙
            Reverse,            // 뒤집기
            
            Accident,           // 사고 (Ready로 자동전환)
            Error,              // 오류
                        
            EndOfType
        };
    }
    
}
```

<br>
<br>

## <a name="ModeDrive">System::ModeDrive::Type</a>
자동차 제어기 동작 상태를 나타냅니다.

```cpp
namespace System
{
    namespace ModeDrive
    {
        enum Type
        {
            None = 0,           // 없음
            
            Ready,              // 준비
            
            Start,              // 출발
            Drive,              // 주행
            Stop,               // 강제 정지
            
            Accident,           // 사고 (Ready로 자동전환)
            Error,              // 오류
            
            EndOfType
        };
    }
    
}
```

<br>
<br>

## <a name="SensorOrientation">System::SensorOrientation::Type</a>
센서 방향을 나타냅니다.
```cpp
namespace System
{
    namespace SensorOrientation
    {
        enum Type
        {
            None = 0,           // 없음
            
            Normal,             // 정상
            ReverseStart,       // 뒤집히기 시작
            Reversed,           // 뒤집힘
            
            EndOfType
        };
    }
}
```

<br>
<br>

## <a name="Direction">System::Direction::Type</a>
방향을 나타냅니다.
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
페트론 조종기 방향 기준을 선택합니다. World는 앱솔루트 모드입니다. 드론 외부 세계를 중심으로 좌표를 판단합니다. Local은 일반모드입니다. 드론을 중심으로 좌표를 판단합니다.

```cpp
namespace System
{
    namespace Coordinate
    {
        enum Type
        {
            None = 0,           // 없음
            
            World,              // 고정 좌표계(Absolute)
            Local,              // 상대 좌표계(일반)
            
            EndOfType
        };
    }
}
```

<br>
<br>

## <a name="Trim">System::Trim::Type</a>
페트론이 한쪽 방향으로 흐를 때 반대 방향을 입력하여 호버링을 할 수 있게 조정합니다. 한 번 전송할 때마다 일정하게 값이 변합니다.

```cpp
namespace System
{
    namespace Trim
    {
        enum Type
        {
            None = 0,           // 없음
 
            RollIncrease,       // Roll 증가
            RollDecrease,       // Roll 감소              
            PitchIncrease,      // Pitch 증가
            PitchDecrease,      // Pitch 감소             
            YawIncrease,        // Yaw 증가
            YawDecrease,        // Yaw 감소               
            ThrottleIncrease,   // Throttle 증가
            ThrottleDecrease,   // Throttle 감소
            
            EndOfType
        };
    }
}
```

<br>
<br>

## <a name="FlightEvent">System::FlightEvent::Type</a>
페트론 비행 이벤트를 실행합니다.

```cpp
namespace System
{
    namespace FlightEvent
    {
        enum Type
        {
            None = 0,           // 없음
            
            TakeOff,            // 이륙
            
            FlipFront,          // 회전(Not Yet)
            FlipRear,           // 회전(Not Yet)
            FlipLeft,           // 회전(Not Yet)
            FlipRight,          // 회전(Not Yet)
            
            Stop,               // 정지
            Landing,            // 착륙
            Reverse,            // 뒤집기
            
            Shot,               // 미사일 쏠때 움직임
            UnderAttack,        // 미사일 맞을때 움직임
            
            EndOfType   
        };
    }
}
```

<br>
<br>

## <a name="LightMode">Light::Mode::Type</a>
LED 모드 또는 이벤트 명령 시 동작 모드를 지정할 때 사용합니다.

```cpp
namespace Light
{
    namespace Mode
    {
        enum Type
        {
            None,
            
            EyeNone = 0x10,
            EyeHold,            // 지정한 색상을 계속 켬
            EyeMix,             // 순차적으로 LED 색 변경
            EyeFlicker,         // 깜빡임         
            EyeFlickerDouble,   // 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)
            EyeDimming,         // 밝기 제어하여 천천히 깜빡임
            
            ArmNone = 0x40,     
            ArmHold,            // 지정한 색상을 계속 켬
            ArmMix,             // 순차적으로 LED 색 변경
            ArmFlicker,         // 깜빡임         
            ArmFlickerDouble,   // 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)
            ArmDimming,         // 밝기 제어하여 천천히 깜빡임
            ArmFlow,            // 앞에서 뒤로 흐름           
            ArmFlowReverse,     // 뒤에서 앞으로 흐름 
            
            EndOfType
        };
    }
}
```

<br>
<br>

## <a name="LightColors">Light::Colors::Type</a>
LED 색상을 지정할 때 사용합니다.

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
            Chocolate,
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

