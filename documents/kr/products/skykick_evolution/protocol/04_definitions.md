**[SKYKICK EVOLUTION](index.md)** / **Protocol** / **Definitions**

Modified : 2023.7.1

---

#### SKYKICK EVOLUTION 에서 사용하고 있는 기본 정의들을 소개합니다.

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
            None						= 0x00,		// 이벤트 없음
            
            Stop						= 0x01,		// 정지
            
            ModeControlFlight			= 0x02,		// 비행 제어 모드 설정
            Escape						= 0x03,		// 이스케이프 모드 설정
            ControlSpeed				= 0x04,		// 제어 속도 설정
            
            ClearBias					= 0x05,		// 자이로/엑셀 바이어스 리셋(트림도 같이 초기화 됨)
            ClearTrim					= 0x06,		// 트림 초기화
            
            FlightEvent					= 0x07,		// 비행 이벤트 실행
            
            SetDefault					= 0x08,		// 기본 설정으로 초기화
            ModeController				= 0x0A,		// 조종기 동작 모드(0x10:조종, 0x80:링크)
            Link						= 0x0B,		// 링크 제어(0:Client Mode, 1:Server Mode, 2:Pairing Start)
            LoadDefaultColor			= 0x0C,		// 기본 색상으로 변경
            
            Trim						= 0x0D,		// 트림
            
            ModeTest					= 0xF0,		// 테스트 락(테스트를 완료하기 전까진 사용 불가 / 27:활성화, 11:해제))
            
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

기능에 따른 모델 분류

```cpp
namespace ModelNumber
{
    enum Type
    {
        //                          AAAABBCC, AAAA(Project Number), BB(Device Type), CC(Revision)
        Drone_11_Drone_P0		= 0x000B1000,	// reserve
        Drone_11_Drone_P1		= 0x000B1001,	// 65 no coding
        Drone_11_Drone_P2		= 0x000B1002,	// fixWing
        Drone_11_Drone_P3		= 0x000B1003,	// 65 coding
        Drone_11_Drone_P4		= 0x000B1004,	// 95 battle drone
        Drone_11_Drone_P5		= 0x000B1005,	// skykick evolution drone
        Drone_11_Drone_P6		= 0x000B1006,	// reserve
        Drone_11_Drone_P7		= 0x000B1007,	// reserve
        Drone_11_Drone_P8		= 0x000B1008,	// reserve
        Drone_11_Drone_P9		= 0x000B1009,	// reserve
        
        Drone_11_Controller_P0	= 0x000B2000,	// 65 Drone, No USB, Fixed Wing, Return
        Drone_11_Controller_P1	= 0x000B2001,	// 65 drone, USB
        Drone_11_Controller_P2	= 0x000B2002,	// 65 drone, No USB
        Drone_11_Controller_P3	= 0x000B2003,	// Bird Wing, Fixed Wing, NoReturn
        Drone_11_Controller_P4	= 0x000B2004,	//  Battle drone, USB
        Drone_11_Controller_P5	= 0x000B2005,	// skykick evolution controller
        Drone_11_Controller_P6	= 0x000B2006,	// reserve
        Drone_11_Controller_P7	= 0x000B2007,	// reserve
        Drone_11_Controller_P8	= 0x000B2008,	// reserve
        Drone_11_Controller_P9	= 0x000B2009,	// reserve
        
        Drone_11_Link_P0		= 0x000B3000,	// Drone_11_Link_P0 RoboRobo
        Drone_11_Link_P1		= 0x000B3001,	// reserve
        
        // Drone_12  chip
        Drone_12_Drone_P0		= 0x000C1000,	// coding drone stm32f401rc + xn297
        Drone_12_Drone_P1		= 0x000C1001,	// coding drone STM32F407VE + nrf24l01
        Drone_12_Drone_P2		= 0x000C1002,	// reserve
        
        Drone_12_Controller_P0	= 0x000C2000,	// coding drone stm32f401rc + xn297
        Drone_12_Controller_P1	= 0x000C2001,	// coding drone STM32F407VE + nrf24l01
        Drone_12_Controller_P2	= 0x000C2002,	// reserve
            
        Drone_12_Link_P0		= 0x000C3000,	// Drone_12_Link_P0
        Drone_12_Link_P1		= 0x000C3001,	// 	reserve		
        
        Drone_12_Tester_P0		= 0x000CA000,	// Drone All Tester
        Drone_12_Tester_P1		= 0x000CA001,	// reserve
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
            None        = 0x00,

            Drone       = 0x10,     // 드론(Server)

            Controller  = 0x20,     // 조종기(Client)

            LinkClient  = 0x30,     // 링크 모듈(Client)
            LinkServer  = 0x31,     // 링크 모듈(Server)
            BleClient   = 0x32,     // BLE 클라이언트
            BleServer   = 0x33,     // BLE 서버

            Range       = 0x40,     // 거리 센서 모듈

            Base        = 0x70,     // 베이스

            ByScratch   = 0x80,     // 바이스크래치
            Scratch     = 0x81,     // 스크래치
            Entry       = 0x82,     // 네이버 엔트리

            Tester      = 0xA0,     // 테스터
            Monitor     = 0xA1,     // 모니터
            Updater     = 0xA2,     // 펌웨어 업데이트 도구
            Encrypter   = 0xA3,     // 암호화 도구

            EndOfType,

            Whispering      = 0xFE, // 바로 인접한 장치까지만 전달(받은 장치는 자기 자신에게 보낸 것처럼 처리하고 타 장치에 전달하지 않음)
            Broadcasting    = 0xFF  // 연결된 모든 장치에 전달
        };
    }
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
                None        = 0x00,

                Attitude    = 0x10,     // 자세 - X,Y는 각도(deg)로 입력받음, Z,Yaw는 속도(m/s)로 입력 받음
                Position    = 0x11,     // 위치 - X,Y,Z,Yaw는 속도(m/s)로 입력 받음

                EndOfType
            };
        }
    }
}
```


<br>
<br>


<a name="Mode_Drone"></a>
## Mode::Drone::Type

드론 모드

```cpp
namespace Mode
{
    namespace Drone
    {
        enum Type
        {
            None,                   // 없음
            
            Flight      = 0x10,     // 비행
            
            Link        = 0x80,     // 중계
            
            Error       = 0xA0,     // 오류(문제로 인해 정상적인 동작을 할 수 없는 경우)
            
            EndOfType
        };
    }
    
}
```


<br>
<br>


<a name="Mode_Controller"></a>
## Mode::Controller::Type

조종기 모드

```cpp
namespace Mode
{
    namespace Controller
    {
        enum Type
        {
            None,                   // 없음
            
            Control     = 0x10,     // 조종
            Setup,                  // 설정
            
            Link        = 0x80,     // 링크
            
            Error       = 0xA0,     // 오류
            
            EndOfType
        };
    }
    
}
```


<br>
<br>


<a name="Mode_Connection"></a>
## Mode::Connection::Type

조종기 모드

```cpp
namespace Mode
{
    namespace Connection
    {
        enum Type
        {
            None,
            
            PairingStart,					// 페어링 시작(주소 초기화 후 대기 // 한쪽에서는 새로운 주소를 생성하여 전송)
            PairingExchange,				// 페어링 데이터 교환
            PairingComplete,				// 드론 페어링 완료
            
            Ready,							// 장치와 연결하지 않은 상태(장치와 연결 전 또는 연결 해제 완료 후 이 상태로 전환됨)
            
            ConnectingStart,				// 장치 연결 시작
            Connecting,						// 장치 연결 확인
            Connected,						// 장치 연결 완료
            
            LostConnection,					// 연결을 잃음(Server-Client간 통신이 되지 않는 상태)
            
            Disconnected,					// 장치 연결 해제 완료
            
            EndOfPairing
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
            None        = 0x00,     // 없음
            
            Ready       = 0x10,     // 준비
            
            Start,                  // 이륙 준비
            Takeoff,                // 이륙 (Flight로 자동전환)
            Flight,                 // 비행
            Landing,                // 착륙
            Flip,                   // 회전
            Reverse,                // 뒤집기
            
            Stop        = 0x20,     // 강제 정지
            
            Accident    = 0x30,     // 사고 (Ready로 자동전환)
            Error,                  // 오류
            
            Test        = 0x40,     // 테스트 모드
            
            EndOfType
        };
    }
    
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
            None            = 0x00,

            Ready           = 0x01,
            Hovering        = 0x02,
            Moving          = 0x03,
            ReturnHome      = 0x04
        };
    }
}
```


<br>
<br>


<a name="Escape"></a>
## Escape::Type

방위 기준

조종 시 방향의 기준을 선택합니다.

Escape 드론이 어느 방향을 바라보더라도 <b><i>이륙할 때의 방향</i></b> 또는 <b><i>사용자가 지정한 방향</i></b>을 기준으로 움직입니다.

Normal은 <b><i>드론이 현재 향하는 방향</i></b>을 기준으로 움직입니다. 기본 설정은 Normal입니다.

```cpp
namespace Escape
{
    enum Type
    {
        None = 0,

        Escape,     // 사용자 중심 좌표
        Normal,     // 드론 중심 좌표

        EndOfType
    };
}
```


<br>
<br>
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
            M1,     // Front Left
            M2,     // Front Right
            M3,     // Rear Right
            M4,     // Rear Left

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
        None            = 0x00,     // 없음
        
        Stop            = 0x10,     // 정지
        Takeoff,                    // 이륙
        Landing,                    // 착륙
        
        Reverse,                    // 뒤집기
        
        FlipFront,                  // 회전
        FlipRear,                   // 회전
        FlipLeft,                   // 회전
        FlipRight,                  // 회전
        
        Return,                     // Return
        
        ResetHeading    = 0xA0,     // 헤딩 리셋(Escape 모드 일 때 현재 heading을 0도로 변경)
        
        EndOfType
    };
}
```


<br>
<br>


<a name="Button_Controller_ButtonType"></a>
## Button::Controller::ButtonType::Type

조종기 버튼 플래그

```cpp
namespace Button
{
    namespace Controller
    {
        namespace ButtonType
        {
            enum Type
            {
                None				= 0x0000,
                
                // 버튼
                FrontLeft			= 0x0001,
                FrontRight			= 0x0002,
                
                MidUpLeft			= 0x0004,
                MidUpRight			= 0x0008,
                
                MidUp				= 0x0010,
                MidLeft				= 0x0020,
                MidRight			= 0x0040,
                MidDown				= 0x0080,
                
                BottomLeft			= 0x0100,
                BottomRight			= 0x0200,
            };
        }
    }
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
    namespace Direction
    {
        enum Type
        {
            None    = 0x00,     // 정의하지 않은 영역(무시함)

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

            MuteInstantly       = 1,    // 묵음 즉시 적용
            MuteContinually     = 2,    // 묵음 예약

            ScaleInstantly      = 3,    // 음계 즉시 적용
            ScaleContinually    = 4,    // 음계 예약

            HzInstantly         = 5,    // 주파수 즉시 적용
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


<a name="Buzzer_Melody"></a>
## Buzzer::Melody::Type

버저 멜로디

```cpp
namespace Buzzer
{
    namespace Melody
    {
        enum Type
        {
            DoMiSol,		// 도미솔
            SolMiDo,		// 솔미도
            LaLa,			// 라라
            SiRaSiRa,		// 시라시라
            
            Warning1,		// 경고 1
            Warning2,		// 경고 2
            Warning3,		// 경고 3
            Warning4,		// 경고 4
            
            Du,				// Trim -
            DuDu,			// Trim - End
            DiDic,			// Trim Center
            DiDic2,			// Trim Center 2
            Di,				// Trim +
            DiDi,			// Trim + End
            
            BuzzSound1,
            BuzzSound2,
            BuzzSound3,
            BuzzSound4,
            
            Button,
            Shot,
            
            EndOfType
        };
    }
}
```


<br>


---

<h3>SKYKICK EVOLUTION</H3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. ***Definitions***
5. [Structs](05_structs.md)
6. [Structs - Light](06_structs_light.md)

<br>

[Index](index.md)
