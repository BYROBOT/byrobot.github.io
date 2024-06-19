**[CodingDrone](index.md)** / **Protocol** / **Definitions**

Modified : 2024.6.19

---

#### CodingDrone 에서 사용하고 있는 기본 정의들을 소개합니다.

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
                None                    = 0x00,      // 없음

                Stop                    = 0x01,      // 정지

                // 설정
                ModeControlFlight       = 0x02,      // 비행 제어 모드 설정
                Headless                = 0x03,      // 헤드리스 모드 선택
                ControlSpeed            = 0x04,      // 제어 속도 설정

                ClearBias               = 0x05,      // 자이로 바이어스 리셋(트림도 같이 초기화 됨)
                ClearTrim               = 0x06,      // 트림 초기화

                FlightEvent             = 0x07,      // 비행 이벤트 실행

                SetDefault              = 0x08,      // 기본 설정으로 초기화
                Backlight               = 0x09,      // 조종기 백라이트 설정
                ModeController          = 0x0A,      // 조종기 동작 모드(0x10:조종, 0x80:링크)
                Link                    = 0x0B,      // 링크 제어(0:Client Mode, 1:Server Mode, 2:Pairing Start)

                // 관리자
                ClearCounter            = 0xA0,      // 카운터 클리어(관리자 권한을 획득했을 경우에만 동작)


                EndOfType               = 0xEC,
        };
    }
}
```


<br>
<br>


<a name="ModelNumber"></a>
## ModelNumber::Type

모델 번호

CodingDrone(Drone4)부터 DeviceType을 공통으로 사용하기로 하면서, 펌웨어 업데이트 시 DeviceType 이외에 장치를 구분할 번호가 필요하게 되어 추가함.

```cpp
namespace ModelNumber
{
    enum Type
    {
        None                    = 0x00000000,

        //                           AAAABBCC, AAAA(Project Number), BB(Device Type), CC(Revision)
        Drone_3_Drone_P1        = 0x00031001,    // Drone_3_Drone_P1 (Lightrone / GD65 / HW2181 / Keil / 3.7v / barometer / RGB LED / Shaking binding)
        Drone_3_Drone_P2        = 0x00031002,    // Drone_3_Drone_P2 (Soccer Drone / HW2181 / Keil / 7.4v / barometer / RGB LED / Shaking binding)
        Drone_3_Drone_P3        = 0x00031003,    // Drone_3_Drone_P3 (GD240 / HW2181 / Keil / power button / u30 flow / 3.7v / geared motor / barometer)
        Drone_3_Drone_P4        = 0x00031004,    // Drone_3_Drone_P4 (GD50N / HW2181 / Keil / power button / 3.7v / barometer)
        Drone_3_Drone_P5        = 0x00031005,    // Drone_3_Drone_P5 (GD30 / HW2181 / Keil / 3.7v / nomal binding)
        Drone_3_Drone_P6        = 0x00031006,    // Drone_3_Drone_P6 (Soccer Drone 2 / HW2181 / Keil / 7.4v / barometer / RGB LED / Shaking binding)
        Drone_3_Drone_P7        = 0x00031007,    // Drone_3_Drone_P7 (SKYKICKV2 / SPI / HW2181 / Keil / 7.4v / barometer / RGB LED / Shaking binding)
        Drone_3_Drone_P8        = 0x00031008,    // Drone_3_Drone_P8 (GD65 / SPI / HW2181 / Keil / 3.7v / barometer / RGB LED / Shaking binding)
        Drone_3_Drone_P9        = 0x00031009,    // Drone_3_Drone_P9 (GD65 / SPI / HW2181 / Keil / 3.7v / barometer / RGB LED / Shaking binding / BladeType Power Connector)
        Drone_3_Drone_P10       = 0x0003100A,    // Drone_3_Drone_P10 (Battle Drone / SPI / HW2181 / Keil / 3.7v / barometer / RGB LED / Shaking binding)
        
        Drone_3_Controller_P1   = 0x00032001,    // Drone_3_Controller_P1 / GD65 Controller /small size
        Drone_3_Controller_P2   = 0x00032002,    // Drone_3_Controller_P2 / Skykick Controller /large size
        Drone_3_Controller_P3   = 0x00032003,    // Drone_3_Controller_P3 / GD65 Controller USB /small size + USB
        Drone_3_Controller_P4   = 0x00032004,    // Drone_3_Controller_P4 / Battle Drone Controller USB / small size + usb
        Drone_3_Controller_P5   = 0x00032005,    // Drone_3_Controller_P5 / E-Drone 4m Controller / USB / HW2181B / Keil
        
        Drone_3_Link_P0         = 0x00033000,    // Drone_3_Link_P0
        
        Drone_3_Tester_P4       = 0x0003A004,    // Drone_3_Tester_P4 (obsolete)
        Drone_3_Tester_P6       = 0x0003A006,    // Drone_3_Tester_P6 - Battle Drone Tester
        
        Drone_4_Drone_P4        = 0x00041004,    // Drone_4_Drone_P4 (obsolete)
        Drone_4_Drone_P5        = 0x00041005,    // Drone_4_Drone_P5 (HW2000, 2m range sensor)
        Drone_4_Drone_P6        = 0x00041006,    // Drone_4_Drone_P6 (HW2000B, 4m range sensor)
        Drone_4_Drone_P7        = 0x00041007,    // Drone_4_Drone_P7 (HW2000B, 4m range sensor, BLDC Motor)
        
        Drone_4_Controller_P1   = 0x00042001,    // Drone_4_Controller_P1 (obsolete)
        Drone_4_Controller_P2   = 0x00042002,    // Drone_4_Controller_P2 (HW2000)
        Drone_4_Controller_P3   = 0x00042003,    // Drone_4_Controller_P3 (HW2000B)
        Drone_4_Controller_P4   = 0x00042004,    // Drone_4_Controller_P4 (HW2000B, Encrypt)
        
        Drone_4_Link_P0         = 0x00043000,    // Drone_4_Link_P0
        
        Drone_4_Tester_P4       = 0x0004A004,    // Drone_4_Tester_P4 (obsolete)
        Drone_4_Tester_P6       = 0x0004A006,    // Drone_4_Tester_P6
        Drone_4_Tester_P7       = 0x0004A007,    // Drone_4_Tester_P7

        Drone_4_Monitor_P4      = 0x0004A104,    // Drone_4_Monitor_P4 (obsolete)
        
        Drone_7_Drone_P1        = 0x00071001,    // Drone_7_Drone_P1
        Drone_7_Drone_P2        = 0x00071002,    // Drone_7_Drone_P2 / Coding Car

        Drone_7_BleClient_P0    = 0x00073200,    // Drone_7_BleClient_P0 / Coding Car Link
        Drone_7_BleClient_P5    = 0x00073205,    // Drone_7_BleClient_P5 / Coding Car Tester BLE

        Drone_7_BleServer_P2    = 0x00073302,    // Drone_7_BleServer_P2 / Coding Car Ble Module
        
        Drone_7_Tester_P4       = 0x0003A004,    // Drone_7_Tester_P4 (obsolete)
        Drone_7_Tester_P5       = 0x0003A005,    // Drone_7_Tester_P5 (obsolete)
        Drone_7_Tester_P6       = 0x0003A006,    // Drone_7_Tester_P6
        
        Drone_7_Monitor_P4      = 0x0003A104,    // Drone_7_Monitor_P4 (obsolete)
        Drone_7_Monitor_P5      = 0x0003A105,    // Drone_7_Monitor_P5
        
        Drone_8_Drone_P0        = 0x00081000,    // Drone_8_Drone_P0 (obsolete)
        Drone_8_Drone_P1        = 0x00081001,    // Drone_8_Drone_P1 / Coding Drone
        
        Drone_8_Tester_P4       = 0x0008A004,    // Drone_8_Tester_P4 (obsolete)
        Drone_8_Tester_P6       = 0x0008A006,    // Drone_8_Tester_P6
        
        Drone_8_Monitor_P6      = 0x0008A106,    // Drone_8_Monitor_P6

        Drone_9_Drone_P0        = 0x00091000,    // Drone_9_Drone_P0
        Drone_9_Drone_P1        = 0x00091001,    // Drone_9_Drone_P1
        Drone_9_Drone_P2        = 0x00091002,    // Drone_9_Drone_P2
        
        Drone_9_Tester_P6       = 0x0009A006,    // Drone_9_Tester_P6
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
            None            = 0x00,

            Drone           = 0x10,      // 드론(Server)

            Controller      = 0x20,      // 조종기(Client)

            Link            = 0x30,      // 링크 모듈(Client)
            LinkServer      = 0x31,      // 링크 모듈(Server, 링크 모듈이 서버로 동작하는 경우에만 통신 타입을 잠시 바꿈)
            BleClient       = 0x32,      // BLE 클라이언트
            BleServer       = 0x33,      // BLE 서버

            Range           = 0x40,      // 거리 센서 모듈

            Base            = 0x70,      // 베이스

            ByScratch       = 0x80,      // 바이스크래치
            Scratch         = 0x81,      // 스크래치
            Entry           = 0x82,      // 네이버 엔트리

            Tester          = 0xA0,      // 테스터
            Monitor         = 0xA1,      // 모니터
            Updater         = 0xA2,      // 펌웨어 업데이트 도구
            Encrypter       = 0xA3,      // 암호화 도구

            Whispering      = 0xFE,      // 바로 인접한 장치까지만 전달(받은 장치는 자기 자신에게 보낸 것처럼 처리하고 타 장치에 전달하지 않음)
            Broadcasting    = 0xFF,
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
        None                                    = 0x00000000,

        Motion_NoAnswer                         = 0x00000001,    // Motion 센서 응답 없음
        Motion_WrongValue                       = 0x00000002,    // Motion 센서 잘못된 값
        Motion_NotCalibrated                    = 0x00000004,    // Gyro Bias 보정이 완료되지 않음
        Motion_Calibrating                      = 0x00000008,    // Gyro Bias 보정 중

        Pressure_NoAnswer                       = 0x00000010,    // 압력 센서 응답 없음
        Pressure_WrongValue                     = 0x00000020,    // 압력 센서 잘못된 값

        RangeGround_NoAnswer                    = 0x00000100,    // 바닥 거리 센서 응답 없음
        RangeGround_WrongValue                  = 0x00000200,    // 바닥 거리 센서 잘못된 값

        Flow_NoAnswer                           = 0x00001000,    // Flow 센서 응답 없음
        Flow_WrongValue                         = 0x00002000,    // Flow 잘못된 값
        Flow_CannotRecognizeGroundImage         = 0x00004000,    // 바닥 이미지를 인식할 수 없음
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
        None                                    = 0x00000000,

        NotRegistered                           = 0x00000001,    // 장치 등록이 안됨
        FlashReadLock_UnLocked                  = 0x00000002,    // 플래시 메모리 읽기 Lock이 안 걸림
        BootloaderWriteLock_UnLocked            = 0x00000004,    // 부트로더 영역 쓰기 Lock이 안 걸림
        LowBattery                              = 0x00000008,    // Low Battery
        
        TakeoffFailure_CheckPropellerAndMotor   = 0x00000010,    // 이륙 실패
        CheckPropellerVibration                 = 0x00000020,    // 프로펠러 진동발생
        Attitude_NotStable                      = 0x00000040,    // 자세가 많이 기울어져 있거나 뒤집어져 있을때
        
        CanNotFlip_LowBattery                   = 0x00000100,    // 배터리가 30이하
        CanNotFlip_TooHeavy                     = 0x00000200,    // 기체가 무거움
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
                None        = 0x00,

                Attitude    = 0x10,     // 자세 - X,Y는 각도(deg)로 입력받음, Z,Yaw는 속도(m/s)로 입력 받음
                Position    = 0x11,     // 위치 - X,Y,Z,Yaw는 속도(m/s)로 입력 받음
                Manual      = 0x12,     // 고도를 수동으로 조종함
                Rate        = 0x13,     // Rate - X,Y는 각속도(deg/s)로 입력받음, Z,Yaw는 속도(m/s)로 입력 받음
                Function    = 0x14,     // 기능 - X,Y,Z,Yaw는 속도(m/s)로 입력 받음

                EndOfType   = 0x15,
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
            None_               = 0x00,

            Boot                = 0x10,
            Start               = 0x11,
            Running             = 0x12,
            ReadyToReset        = 0x13,

            Error               = 0xA0,

            EndOfType           = 0x06,
        };
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
            Card,                   // 카드 코딩
            Motion,                 // 모션 코딩
            Piano,                  // 피아노 모드
            
            Link        = 0x80,     // 중계
            Calibration,            // 컬러 캘리브레이션 모드
            
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
            None                = 0x00,

            Ready               = 0x10,

            Start               = 0x11,
            TakeOff             = 0x12,
            Flight              = 0x13,
            Landing             = 0x14,
            Flip                = 0x15,
            Reverse             = 0x16,

            Stop                = 0x20,

            Accident            = 0x30,
            Error               = 0x31,

            Test                = 0x40,

            EndOfType           = 0x41,
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
            None                = 0x00,

            Ready               = 0x01,      // 업데이트 가능 상태
            Update              = 0x02,      // 업데이트 중
            Complete            = 0x03,      // 업데이트 완료

            Failed              = 0x04,      // 업데이트 실패(업데이트 완료까지 갔으나 body의 CRC16이 일치하지 않는 경우 등)

            NotAvailable        = 0x05,      // 업데이트 불가능 상태(Debug 모드 등)
            RunApplication      = 0x06,      // 어플리케이션 동작 중
            NotRegistered       = 0x07,      // 등록되지 않음

            EndOfType           = 0x08,
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
        None                = 0x00,

        Normal              = 0x01,
        ReverseStart        = 0x02,
        Reversed            = 0x03,

        EndOfType           = 0x04,
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
        None                = 0x00,

        Left                = 0x01,
        Front               = 0x02,
        Right               = 0x03,
        Rear                = 0x04,

        Top                 = 0x05,
        Bottom              = 0x06,

        Center              = 0x07,

        EndOfType           = 0x08,
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
            None                = 0x00,

            Ready               = 0x01,      // Ready
            Hovering            = 0x02,      // Hovering
            Moving              = 0x03,      // Moving
            ReturnHome          = 0x04,      // Return Home

            EndOfType           = 0x05,
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


<a name="Rotation"></a>
## Rotation::Type

모터 회전 방향

CodingDrone에는 총 4개의 모터가 있으며, 왼쪽 앞 모터부터 각각 0, 1, 2, 3번으로 번호가 부여되어 있습니다.

드론 비행 시에 0번과 2번 모터는 시계 방향(Clockwise), 1번과 3번 모터는 반시계 방향(Counterclockwise)으로 회전합니다.

CodingDrone의 모터는 정해진 한 방향으로만 회전합니다.

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
        
        ResetHeading    = 0xA0,     // 헤딩 리셋(Headless 모드 일 때 현재 heading을 0도로 변경)
        
        EndOfType
    };
}
```


<br>
<br>


<a name="Button_Drone_ButtonType"></a>
## Button::Drone::ButtonType::Type

드론 버튼 플래그

```cpp
namespace Button
{
    namespace Drone
    {
        namespace ButtonType
        {
            enum Type
            {
                None        = 0x0000,

                // 버튼
                Reset       = 0x0001
            };
        }
    }
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
                None                = 0x0000,

                // 버튼
                FrontLeftTop        = 0x0001,
                FrontLeftBottom     = 0x0002,
                FrontRightTop       = 0x0004,
                FrontRightBottom    = 0x0008,

                TopLeft             = 0x0010,
                TopRight            = 0x0020,   // POWER ON/OFF

                MidUp               = 0x0040,
                MidLeft             = 0x0080,
                MidRight            = 0x0100,
                MidDown             = 0x0200,

                BottomLeft          = 0x0400,
                BottomRight         = 0x0800,
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


<a name="Joystick_Event"></a>
## Joystick::Event::Type

조이스틱 이벤트

```cpp
namespace Joystick
{
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
            Stop                = 0     // 정지(Mode에서의 Stop은 통신에서 받았을 때 Buzzer를 끄는 용도로 사용, set으로만 호출)

            Mute                = 1     // 묵음 즉시 적용
            MuteReserve         = 2     // 묵음 예약

            Scale               = 3     // 음계 즉시 적용
            ScaleReserve        = 4     // 음계 예약

            Hz                  = 5     // 주파수 즉시 적용
            HzReserve           = 6     // 주파수 예약

            EndOfType           = 7
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

            Instantly       = 1,    // 즉시 적용
            Continually     = 2,    // 예약

            EndOfType
        };
    }
}
```


<br>


---

<h3>CodingDrone</H3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. ***Definitions***
5. [Structs](05_structs.md)
6. [Structs - Light](06_structs_light.md)
7. [Structs - Display](07_structs_display.md)
8. [Structs - Card](08_structs_card.md)

<br>

[Index](index.md)
