**[E-DRONE](index.md)** / **Protocol** / **Definitions**

Modified : 2018.7.5

---

#### E-DRONE 에서 사용하고 있는 기본 정의들을 소개합니다.

---

* Kramdown table of contents
{:toc .toc}


<br>


<a name="Protocol_CommandType"></a>
## Protocol::CommandType::Type

명령 타입

```cpp
namespace Protocol
{
    namespace CommandType
    {
        enum Type
        {
            None                        = 0x00,     // 이벤트 없음

            Stop                        = 0x01,     // 정지
            
            ModeControlFlight           = 0x02,     // 비행 제어 모드 설정
            Headless                    = 0x03,     // 헤드리스 모드 설정
            Trim                        = 0x04,     // 트림 변경
            
            ClearBias                   = 0x05,     // 자이로/엑셀 바이어스 리셋(트림도 같이 초기화 됨)
            ClearTrim                   = 0x06,     // 트림 초기화

            FlightEvent                 = 0x07,     // 비행 이벤트 실행

            EndOfType
        };
    }
}
```


<br>
<br>


<a name="ModelNumber"></a>
## ModelNumber::Type

모델 번호

E-DRONE(Drone4)부터 DeviceType을 공통으로 사용하기로 하면서, 펌웨어 업데이트 시 DeviceType 이외에 장치를 구분할 번호가 필요하게 되어 추가함.

```cpp
namespace ModelNumber
{
    enum Type
    {
        //                          PPPPDDII, PPPP(Project Number), DD(Device Type), II(Project Sub Index)
        Drone_4_Drone_P3        = 0x00041003,       // Drone_4_Drone_P3
        Drone_4_Controller_P1   = 0x00042001,       // Drone_4_Controller_P1
        Drone_4_Link_P0         = 0x00043000,       // Drone_4_Link_P0
    };
}
```


<br>
<br>


<a name="Protocol_DeviceType"></a>
## Protocol::DeviceType::Type

장치 타입

```cpp
namespace Protocol
{
    namespace DeviceType
    {
        enum Type
        {
            None = 0,

            Drone       = 0x10,     // 드론(Server)

            Controller  = 0x20,     // 조종기(Client)

            Link        = 0x30,     // 링크 모듈(Client)
            LinkServer  = 0x31,     // 링크 모듈(Server, 링크 모듈이 서버로 동작하는 경우에만 통신 타입을 잠시 바꿈)

            ByScratch   = 0x80,     // 바이스크래치
            Scratch     = 0x81,     // 스크래치
            Entry       = 0x82,     // 네이버 엔트리

            Tester      = 0xA0,     // 테스터
            Monitor     = 0xA1,     // 모니터
            Updater     = 0xA2,     // 펌웨어 업데이트 도구
            Encrypter   = 0xA3,     // 암호화 도구

            EndOfType,

            Broadcasting = 0xFF
        };
    }
}
```


<br>
<br>


<a name="ErrorFlagsForSensor"></a>
## ErrorFlagsForSensor::Type

센서 오류 flag

```cpp
namespace ErrorFlagsForSensor
{
    enum Type
    {
        None                        = 0x00000000,

        Motion_NoAnswer             = 0x00000001,   // Motion 센서 응답 없음
        Motion_WrongValue           = 0x00000002,
        Motion_NotCalibrated        = 0x00000004,   // Gyro Bias 보정이 완료되지 않음
        Motion_Calibrating          = 0x00000008,   // Gyro Bias 보정 중

        Pressure_NoAnswer           = 0x00000010,   // 압력센서 응답 없음
        Pressure_WrongValue         = 0x00000020,

        RangeGround_NoAnswer        = 0x00000100,   // 바닥 거리센서 응답 없음
        RangeGround_WrongValue      = 0x00000200,

        Flow_NoAnswer               = 0x00001000,   // Flow 센서 응답 없음
        Flow_WrongValue             = 0x00002000,

        Battery_NoAnswer            = 0x00010000,   // 배터리 응답 없음
        Battery_WrongValue          = 0x00020000,
        Battery_NotCalibrated       = 0x00040000,   // 배터리 입력값 보정이 완료되지 않음
    };
}
```


<br>
<br>


<a name="ErrorFlagsForState"></a>
## ErrorFlagsForState::Type

상태 오류 flag

```cpp
namespace ErrorFlagsForState
{
    enum Type
    {
        None                        = 0x00000000,

        NotTested                   = 0x00000001,   // 테스트하지 않음
    };
}
```


<br>
<br>


<a name="Mode_Control_Flight"></a>
## Mode::Control::Flight::Type

비행 제어 모드

```cpp
namespace Mode
{
    namespace Control
    {
        namespace Flight
        {
            enum Type
            {
                None = 0,
            
                Attitude    = 0x10, // 자세 - X,Y는 각도(deg)로 입력받음, Z,Yaw는 속도(m/s)로 입력 받음
                Position    = 0x11, // 위치 - X,Y,Z,Yaw는 속도(m/s)로 입력 받음
                Function    = 0x12, // 기능 - X,Y,Z,Yaw는 속도(m/s)로 입력 받음
                Rate        = 0x13, // Rate - X,Y는 각속도(deg/s)로 입력받음, Z,Yaw는 속도(m/s)로 입력 받음e
                
                EndOfType
            };
        }
    }
}
```


<br>
<br>


<a name="Mode_System"></a>
## Mode::System::Type

시스템 동작 상태

```cpp
namespace Mode
{
    namespace System
    {
        enum Type
        {
            None = 0,
            
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


<a name="Mode_Flight"></a>
## Mode::Flight::Type

비행 제어기 동작 상태

```cpp
namespace Mode
{
    namespace Flight
    {
        enum Type
        {
            None = 0,
            
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


<a name="Mode_Update"></a>
## Mode::Update::Type

업데이트 상태

```cpp
namespace Mode
{
    namespace Update
    {
        enum Type
        {
            None,

            Ready,              // 업데이트 가능 상태
            Update,             // 업데이트 중
            Complete,           // 업데이트 완료
                
            Faild,              // 업데이트 실패(업데이트 완료까지 갔으나 body의 CRC16이 일치하지 않는 경우 등)

            NotAvailable,       // 업데이트 불가능 상태(Debug 모드 등)
            RunApplication,     // 어플리케이션 동작 중

            EndOfType
        };
    }
}
```


<br>
<br>


<a name="SensorOrientation"></a>
## SensorOrientation::Type

센서 방향

```cpp
namespace SensorOrientation
{
    enum Type
    {
        None = 0,
        
        Normal,             // 정상
        ReverseStart,       // 뒤집히기 시작
        Reversed,           // 뒤집힘
        
        EndOfType
    };
}
```


<br>
<br>


<a name="Direction"></a>
## Direction::Type

방향

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
        
        Center,
        
        EndOfType
    };
}
```


<br>
<br>


<a name="Mode_Movement"></a>
## Mode::Movement::Type

이동 상태

```cpp
namespace Mode
{
    namespace Movement
    {
        enum Type
        {
            None        = 0x00,
            Hovering    = 0x01,     // 호버링
            Moving      = 0x02      // 이동 중
        };
    }
}
```


<br>
<br>


<a name="Headless"></a>
## Headless::Type

방위 기준

조종 시 방향의 기준을 선택합니다.

Headless는 드론이 어느 방향을 바라보더라도 <b><i>이륙할 때의 방향</i></b> 또는 <b><i>사용자가 지정한 방향</i></b>을 기준으로 움직입니다.

Normal은 <b><i>드론이 현재 향하는 방향</i></b>을 기준으로 움직입니다.

조종기 상에서는 Headless를 'Headless ON', Normal을 'Headless OFF'로 표현하고 있습니다. 기본 설정은 Normal입니다.

```cpp
namespace Headless
{
    enum Type
    {
        None = 0,
        
        Headless,   // 사용자 중심 좌표
        Normal,     // 드론 중심 좌표
        
        EndOfType
    };
}
```


<br>
<br>


<a name="Trim"></a>
## Trim::Type

Trim

페트론이 한쪽 방향으로 흐를 때 반대 방향을 입력하여 호버링을 할 수 있게 조정합니다. 한 번 전송할 때마다 일정하게 값이 변합니다.

```cpp
namespace Trim
{
    enum Type
    {
        None = 0,

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


<a name="Rotation"></a>
## Rotation::Type

모터 회전 방향

E-DRONE에는 총 4개의 모터가 있으며, 왼쪽 앞 모터부터 각각 0, 1, 2, 3번으로 번호가 부여되어 있습니다.

드론 비행 시에 0번과 2번 모터는 시계방향(Clockwise), 1번과 3번 모터는 반시계방향(Counterclockwise)으로 회전합니다.

```cpp
namespace Rotation
{
    enum Type
    {
        None = 0,
        
        Clockwise,              // 시계 방향
        Counterclockwise,       // 반시계 방향
        
        EndOfType
    };
}
```


<br>
<br>


<a name="Motor_Part"></a>
## Motor::Part::Type

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


<a name="FlightEvent"></a>
## FlightEvent::Type

페트론 비행 이벤트

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
        
        ResetHeading = 0xA0,    // 헤딩 리셋(앱솔루트 모드 일 때 현재 heading을 0도로 변경)
        
        EndOfType
    };
}
```


<br>
<br>


<a name="Button_Event"></a>
## Button::Event::Type

버튼 이벤트

```cpp
namespace Button
{
    namespace Event
    {
        enum Type
        {
            None,

            Down,               // 누르기 시작
            Press,              // 누르는 중
            Up,                 // 뗌

            EndContinuePress    // 연속 입력 종료
        };
    }
}
```


<br>
<br>


<a name="Joystick_Direction"></a>
## Joystick::Direction::Type

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


<a name="Joystick_Event"></a>
## Joystick::Event::Type

조이스틱 이벤트

```cpp
namespace Joystick
{
    // 조이스틱 이벤트
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


<a name="Buzzer_Mode"></a>
## Buzzer::Mode::Type

버저 모드

```cpp
namespace Buzzer
{
    namespace Mode
    {
        enum Type
        {
            Stop                = 0,    // 정지(Mode에서의 Stop은 통신에서 받았을 때 Buzzer를 끄는 용도로 사용, set으로만 호출)

            MuteInstantally     = 1,    // 묵음 즉시 적용
            MuteContinually     = 2,    // 묵음 예약

            ScaleInstantally    = 3,    // 음계 즉시 적용
            ScaleContinually    = 4,    // 음계 예약

            HzInstantally       = 5,    // 주파수 즉시 적용
            HzContinually       = 6,    // 주파수 예약

            EndOfType
        };
    }
}
```


<br>
<br>


<a name="Buzzer_Scale"></a>
## Buzzer::Scale::Type

버저 음계

```cpp
namespace Buzzer
{
    namespace Scale
    {
        enum Type
        {
            C1, CS1, D1, DS1, E1, F1, FS1, G1, GS1, A1, AS1, B1,
            C2, CS2, D2, DS2, E2, F2, FS2, G2, GS2, A2, AS2, B2,
            C3, CS3, D3, DS3, E3, F3, FS3, G3, GS3, A3, AS3, B3,
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


<a name="Vibrator_Mode"></a>
## Vibrator::Mode::Type

진동 모드

```cpp
namespace Vibrator
{
    namespace Mode
    {
        enum Type
        {
            Stop            = 0,    // 정지
            
            Instantally     = 1,    // 즉시 적용
            Continually     = 2,    // 예약
            
            EndOfType
        };
    }
}
```


<br>


---

<h3>E-DRONE</H3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. ***Definitions***
5. [Structs](05_structs.md)
6. [Structs - Light](06_structs_light.md)
7. [Structs - Display](07_structs_display.md)

<br>

[Index](index.md)