***DRONEFIGHTER2017 / Protocol / Definitions***<br>
Modified : 2017.10.18

---

#### Drone Fighter에서 사용하고 있는 기본 정의들을 소개합니다.

---

<br>

## <a name="Protocol_CommandType">Protocol::CommandType::Type</a>
CommandBase 구조체에서 commandType 변수에 사용합니다.

```cpp
namespace Protocol
{
    namespace CommandType
    {
        enum Type
        {
            None = 0,                       // 이벤트 없음

            // 설정
            ModeVehicle = 0x10,             // Vehicle 동작 모드 전환

            // 제어
            Coordinate = 0x20,              // 방위 기준 변경
            Trim,                           // 트림 변경
            FlightEvent,                    // 비행 이벤트 실행
            DriveEvent,                     // 주행 이벤트 실행
            Stop,                           // 정지
            
            ClearTrim = 0x50,               // 트림 초기화
            GyroBiasAndTrimReset,           // 자이로 바이어스와 트림 리셋
            
            UserInterfacePreset = 0x80,     // 사용자 인터페이스 설정
            DataStorageWrite,               // 변경사항이 있는 경우 데이터 저장소에 기록

            // 관리자
            ClearCounter = 0xA0,            // 카운터 클리어(관리자 권한을 획득했을 경우에만 동작)

            EndOfType
        };
    }
}
```

<br>
<br>

## <a name="Mode_Vehicle">Mode::Vehicle::Type</a>
Drone Fighter 동작 모드를 선택합니다.

```cpp
namespace Mode
{
    namespace Vehicle
    {
        enum Type
        {
            None = 0,           // 없음
            
            Flight = 0x10,      // 비행(가드 포함)
            FlightNoGuard,      // 비행(가드 없음)
            FlightFPV,          // 비행(FPV)
            
            Drive = 0x20,       // 주행
            DriveFPV,           // 주행(FPV)
            
            Test = 0x30,        // 테스트
            
            EndOfType
        };
    }
}
```

<br>
<br>

## <a name="Mode_System">Mode::System::Type</a>
시스템 동작 상태를 나타냅니다.

```cpp
namespace Mode
{
    namespace System
    {
        enum Type
        {
            None = 0,           // 없음
            
            Boot,               // 부팅
            Start,              // 시작 코드 실행
            Running,            // 메인 코드 동작
            ReadyToReset,       // 리셋 대기(1초 뒤 리셋)
            Error,              // 오류
                    
            EndOfType
        };
    }
    
}
```

<br>
<br>

## <a name="Mode_Flight">Mode::Flight::Type</a>
비행 제어기 동작 상태를 나타냅니다.

```cpp
namespace Mode
{
    namespace Flight
    {
        enum Type
        {
            None = 0,           // 없음
            
            Ready = 0x10,       // 준비
            
            TakeOff,            // 이륙 (Flight로 자동전환)
            Flight,             // 비행
            Landing,            // 착륙
            Flip,               // 회전         
            Reverse,            // 뒤집기
            
            Stop = 0x20,        // 강제 정지
            
            Accident = 0x30,    // 사고 (Ready로 자동전환)
            Error,              // 오류
            
            Test = 0x40,        // 테스트 모드
            
            EndOfType
        };
    }
    
}
```

<br>
<br>

## <a name="Mode_Drive">Mode::Drive::Type</a>
자동차 제어기 동작 상태를 나타냅니다.

```cpp
namespace Mode
{
    namespace Drive
    {
        enum Type
        {
            None = 0,           // 없음
            
            Ready = 0x10,       // 준비
            
            Start,              // 출발
            Drive,              // 주행
            
            Stop = 0x20,        // 강제 정지
            
            Accident = 0x30,    // 사고 (Ready로 자동전환)
            Error,              // 오류
            
            Test = 0x40,        // 테스트 모드

            EndOfType
        };
    }
    
}
```

<br>
<br>

## <a name="SensorOrientation">SensorOrientation::Type</a>
센서 방향을 나타냅니다.
```cpp
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
```

<br>
<br>

## <a name="Direction">Direction::Type</a>
방향을 나타냅니다.
```cpp
namespace Direction
{
    enum Type
    {
        None = 0,

        Left,
        Front,
        Right,
        Rear,
        
        Top,
        Bottom,
        
        EndOfType
    };
}
```

<br>
<br>

## <a name="Coordinate">Coordinate::Type</a>
조종기 방향 기준을 선택합니다. World는 앱솔루트 모드입니다. 드론 외부 세계를 중심으로 좌표를 판단합니다. Local은 일반모드입니다. 드론을 중심으로 좌표를 판단합니다.

```cpp
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
```


<br>
<br>


## <a name="Trim">Trim::Type</a>
드론이 한쪽 방향으로 흐를 때 반대 방향을 입력하여 호버링을 할 수 있게 조정합니다. 한 번 전송할 때마다 일정하게 값이 변합니다.

```cpp
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
        
        Reset,              // 전체 트림 리셋
        
        EndOfType
    };
}
```


<br>
<br>


## <a name="Motor_Direction">Motor::Direction::Type</a>
모터 회전 방향

```cpp
namespace Motor
{
    namespace Direction
    {
        enum Type
        {
            None = 0,           // 입력값을 적용하지 않음

            Forward,            // 정방향
            Reverse,            // 역방향

            EndOfType
        };
    }
}
```

<br>
<br>


## <a name="Motor_Part">Motor::Part::Type</a>
모터 번호

```cpp
namespace Rotation
{
    namespace Part
    {
        enum Type
        {
            M1,		// Front Left
            M2,		// Front Right
            M3,		// Rear Right
            M4,		// Rear Left
            
            EndOfPart,
            
            All
        };
    }
}
```


<br>
<br>


## <a name="FlightEvent">FlightEvent::Type</a>
비행 이벤트를 실행합니다.

```cpp
namespace FlightEvent
{
    enum Type
    {
        None = 0,               // 없음
        
        Stop = 0x10,            // 정지
        TakeOff,                // 이륙
        Landing,                // 착륙
        
        Reverse,                // 뒤집기
        
        FlipFront,              // 회전
        FlipRear,               // 회전
        FlipLeft,               // 회전
        FlipRight,              // 회전
        
        Shot,                   // 미사일 쏠때 움직임
        UnderAttack,            // 미사일 맞을때 움직임
        
        ResetHeading = 0xA0,    // 헤딩 리셋(앱솔루트 모드 일 때 현재 heading을 0도로 변경)
        
        EndOfType   
    };
}
```


<br>
<br>


## <a name="Joystick_Direction">Joystick::Direction::Type</a>
조이스틱 방향

```cpp
namespace Joystick
{
    // 조이스틱 방향
    namespace Direction
    {
        enum Type
        {
            None    = 0,        // 정의하지 않은 영역(무시함)
            
            VT      = 0x10,     //   위(세로)
            VM      = 0x20,     // 중앙(세로)
            VB      = 0x40,     // 아래(세로)
            
            HL      = 0x01,     //   왼쪽(가로)
            HM      = 0x02,     //   중앙(가로)
            HR      = 0x04,     // 오른쪽(가로)
            
            TL = 0x11,  TM = 0x12,  TR = 0x14,
            ML = 0x21,  CN = 0x22,  MR = 0x24,
            BL = 0x41,  BM = 0x42,  BR = 0x44
        };
    }
}
```

<br>
<br>


## <a name="Joystick_Event">Joystick::Event::Type</a>
조이스틱 방향

```cpp
namespace Joystick
{
    // 조이스틱 방향
    namespace Event
    {
        enum Type
        {
            None    = 0,        // 이벤트 없음
            
            In,                 // 특정 영역에 진입
            Stay,               // 특정 영역에서 상태 유지
            Out,                // 특정 영역에서 벗어남
            
            EndOfType
        };
    }
}
```


<br>
<br>


## <a name="Joystick_Command">Joystick::Command::Type</a>
조이스틱 방향

```cpp
namespace Joystick
{
    // 조이스틱 커맨드
    namespace Command
    {
        enum Type
        {
            None,

            UpDownUpDown,       // 위-아래-위-아래
            LeftRightLeftRight, // 좌-우-좌-우
            TurnLeft,           // 좌회전
            TurnRight,          // 우회전

            EndOfType
        };
    }
}
```


<br>
<br>



## <a name="Buzzer_Mode">Buzzer::Mode::Type</a>
버저 모드

```cpp
namespace Buzzer
{
    namespace Mode
    {
        enum Type
        {
            Stop                = 0,    // 정지(Mode에서의 Stop은 통신에서 받았을 때 Buzzer를 끄는 용도로 사용, set으로만 호출)

            MuteInstantly     = 1,    // 묵음 즉시 적용
            MuteContinually     = 2,    // 묵음 예약

            ScaleInstantly    = 3,    // 음계 즉시 적용
            ScaleContinually    = 4,    // 음계 예약

            HzInstantly       = 5,    // 주파수 즉시 적용
            HzContinually       = 6,    // 주파수 예약

            EndOfType
        };
    }
}
```


<br>
<br>


## <a name="Buzzer_Scale">Buzzer::Scale::Type</a>
버저 음계

```cpp
namespace Buzzer
{
    namespace Scale
    {
        enum Type
        {
            /* 1, 2, 3 옥타브는 Timer tick 사용(소리에 잡음이 섞임) */
            C1, CS1, D1, DS1, E1, F1, FS1, G1, GS1, A1, AS1, B1,
            C2, CS2, D2, DS2, E2, F2, FS2, G2, GS2, A2, AS2, B2,
            C3, CS3, D3, DS3, E3, F3, FS3, G3, GS3, A3, AS3, B3,

            /* 4, 5, 6, 7, 8 옥타브는 PWM 사용(정상적인 소리) */
            C4, CS4, D4, DS4, E4, F4, FS4, G4, GS4, A4, AS4, B4,
            C5, CS5, D5, DS5, E5, F5, FS5, G5, GS5, A5, AS5, B5,
            C6, CS6, D6, DS6, E6, F6, FS6, G6, GS6, A6, AS6, B6,
            C7, CS7, D7, DS7, E7, F7, FS7, G7, GS7, A7, AS7, B7,
            C8, CS8, D8, DS8, E8, F8, FS8, G8, GS8, A8, AS8, B8,
        
            EndOfType,
            
            Mute    = 0xEE,     // 묵음
            Fin     = 0xFF      // 악보의 끝
        };
    }
}
```

<br>
<br>


## <a name="Vibrator_Mode">Vibrator::Mode::Type</a>
진동 모드

```cpp
namespace Vibrator
{
    namespace Mode
    {
        enum Type
        {
            Stop            = 0,    // 정지
            
            Instantly     = 1,    // 즉시 적용
            Continually     = 2,    // 예약
            
            EndOfType
        };
    }
}
```

<br>
<br>


## <a name="UserInterface_Commands">UserInterface::Commands::Type</a>
사용자 인터페이스 입력

```cpp
namespace UserInterface
{
    namespace Commands
    {
        enum Type
        {
            None,
            
            Setup_Button_FrontLeft_Down,
            Setup_Button_FrontRight_Down,
            Setup_Button_MidTurnLeft_Down,
            Setup_Button_MidTurnRight_Down,
            Setup_Button_MidUp_Down,
            Setup_Button_MidLeft_Down,
            Setup_Button_MidRight_Down,
            Setup_Button_MidDown_Down,
            
            Setup_Joystick_Left_Up_In,
            Setup_Joystick_Left_Left_In,
            Setup_Joystick_Left_Right_In,
            Setup_Joystick_Left_Down_In,
            
            Setup_Joystick_Right_Up_In,
            Setup_Joystick_Right_Left_In,
            Setup_Joystick_Right_Right_In,
            Setup_Joystick_Right_Down_In,
            
            EndOfType
        };
    }
}
```


<br>
<br>


## <a name="UserInterface_Functions">UserInterface::Functions::Type</a>
사용자 인터페이스 기능

```cpp
namespace UserInterface
{
    namespace Functions
    {
        enum Type
        {
            None,
            
            JoystickCalibration_Reset,
            
            Change_Team_Red,
            Change_Team_Blue,
            
            Change_Mode_Vehicle_Flight,
            Change_Mode_Vehicle_FlightNoGuard,
            Change_Mode_Vehicle_Drive,
            
            Change_Coordinate_Local,                // Normal
            Change_Coordinate_World,                // Absolute
            
            Change_Mode_Control_Mode1,
            Change_Mode_Control_Mode2,
            Change_Mode_Control_Mode3,
            Change_Mode_Control_Mode4,
                            
            GyroBias_Reset,
            
            Change_Mode_USB_CDC,
            Change_Mode_USB_HID,
            
            EndOfType
        };
    }
}
```


<br>
<br>


## <a name="UserInterface_Preset">UserInterface::Preset::Type</a>
사용자 인터페이스 프리셋

```cpp
namespace UserInterface
{
    namespace Preset
    {
        enum Type
        {
            None,
            
            Clear,              // 초기화
            Custom,             // 사용자 설정(기본 설정에서 변경된 상태)
            
            Drone2017,          // 기본 설정
            Education,          // 교육용 설정
            
            EndOfType
        };
    }
}
```


<br>


---

### DRONE FIGHTER 2017

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. ***Definitions***
5. [Structs](05_structs.md)
6. [Structs - Light](06_structs_light.md)

<br>

[Index](index.md)
