**[E-DRIVE](index.md)** / **Protocol** / **Definitions**

Modified : 2020.1.13

---

#### E-DRIVE 에서 사용하고 있는 기본 정의들을 소개합니다.

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
            None                    = 0x00,     // 이벤트 없음

            Stop                    = 0x01,     // 정지
            ClearBias               = 0x02,     // 자이로/엑셀 바이어스 리셋(트림도 같이 초기화 됨)
            ClearTrim               = 0x03,     // 트림 초기화
            DriveEvent              = 0x04,     // 주행 이벤트 실행

            SetDefault              = 0x08,     // 기본 설정으로 초기화

            // 통신[Bluetooth]
            BluetoothSystemEvent    = 0xB0,     // 블루투스 시스템 이벤트

            // LINK
            LinkSystemReset         = 0xE0,     // 시스템 재시작
            LinkDiscoverStart       = 0xE1,     // 장치 검색 시작
            LinkDiscoverStop        = 0xE2,     // 장치 검색 중단
            LinkConnect             = 0xE3,     // 지정한 인덱스의 장치 연결
            LinkDisconnect          = 0xE4,     // 연결 해제
            LinkRssiPollingStart    = 0xE5,     // RSSI 수집 시작
            LinkRssiPollingStop     = 0xE6,     // RSSI 수집 중단

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

펌웨어 업데이트 시 제품 구분용 번호.

```cpp
namespace ModelNumber
{
    enum Type
    {
        None = 0,

        //                          AAAABBCC, AAAA(Project Number), BB(Device Type), CC(Revision)
        Drone_3_Drone_P1        = 0x00031001,   // Drone_3_Drone_P1
        Drone_3_Drone_P2        = 0x00031002,   // Drone_3_Drone_P2
        Drone_3_Drone_P3        = 0x00031003,   // Drone_3_Drone_P3
        Drone_3_Drone_P4        = 0x00031004,   // Drone_3_Drone_P4
        Drone_3_Drone_P5        = 0x00031005,   // Drone_3_Drone_P5
        Drone_3_Drone_P6        = 0x00031006,   // Drone_3_Drone_P6
        Drone_3_Drone_P7        = 0x00031007,   // Drone_3_Drone_P7
        Drone_3_Drone_P8        = 0x00031008,   // Drone_3_Drone_P8

        Drone_3_Controller_P1   = 0x00032001,   // Drone_3_Controller_P1 / small size
        Drone_3_Controller_P2   = 0x00032002,   // Drone_3_Controller_P2 / large size
        Drone_3_Controller_P3   = 0x00032003,   // Drone_3_Controller_P3 / small size + USB

        Drone_4_Drone_P5        = 0x00041005,   // Drone_4_Drone_P5

        Drone_4_Controller_P2   = 0x00042002,   // Drone_4_Controller_P2

        Drone_4_Link_P0         = 0x00043000,   // Drone_4_Link_P0

        Drone_4_Tester_P4       = 0x0004A004,   // Drone_4_Tester_P4
        Drone_4_Monitor_P4      = 0x0004A104,   // Drone_4_Monitor_P4

        Drone_7_Drone_P2        = 0x00071002,   // Drone_7_Drone_P2
        Drone_7_BleClient_P0    = 0x00073200,   // Drone_7_BleClient_P0
        Drone_7_BleServer_P2    = 0x00073302,   // Drone_7_BleServer_P2

        Drone_7_Tester_P5       = 0x0007A005,   // Drone_7_Tester_P5
        Drone_7_Monitor_P5      = 0x0007A105,   // Drone_7_Monitor_P5

        Drone_8_Drone_P1        = 0x00081001,   // Drone_8_Drone_P1

        Drone_8_Tester_P4       = 0x0008A004,   // Drone_8_Tester_P4
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

            Whispering      = 0xFE,     // 바로 인접한 장치까지만 전달(받은 장치는 자기 자신에게 보낸 것처럼 처리하고 타 장치에 전달하지 않음)
            Broadcasting    = 0xFF      // 연결된 모든 장치에 전달
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
        None                    = 0x00000000,

        Motion_NoAnswer         = 0x00000001,   // Motion 응답 없음
        Motion_WrongValue       = 0x00000002,   // Motion 잘못된 값
        Motion_NotCalibrated    = 0x00000004,   // Gyro Bias 보정이 완료되지 않음
        Motion_Calibrating      = 0x00000008,   // Gyro Bias 보정 중
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
        None                            = 0x00000000,

        NotRegistered                   = 0x00000001,   // 장치 등록이 안됨
        FlashReadLock_UnLocked          = 0x00000002,   // 플래시 메모리 읽기 Lock이 안 걸림
        BootloaderWriteLock_UnLocked    = 0x00000004,   // 부트로더 영역 쓰기 Lock이 안 걸림
    };
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
            None            = 0,

            Boot            = 0x10,     // 부팅
            Start,                      // 시작 코드 실행
            Running,                    // 메인 코드 동작
            ReadyToReset,               // 리셋 대기(1초 뒤 리셋)
            
            Error           = 0xA0,     // 오류
            
            EndOfType
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
            None,                       // 없음

            Drive           = 0x10,     // 원격 조종
            Card,                       // 카드 코딩
            Motion,                     // 모션 코딩
            Maze,                       // 미로 찾기(미구현)
            Random,                     // 랜덤(미구현)
            HandFollowing,              // 핸드 팔로잉
            LineTracer,                 // 라인 트레이서
            Piano,                      // 피아노 모드

            Link            = 0x80,     // 중계기

            Error           = 0xA0,     // 오류(문제로 인해 정상적인 동작을 할 수 없는 경우)

            EndOfType
        };
    }
}
```


<br>
<br>


<a name="Mode_Drive"></a>
## Mode::Drive::Type

주행 모드

```cpp
namespace Mode
{
    namespace Drive
    {
        enum Type
        {
            None        = 0x00,     // 없음

            Ready       = 0x10,     // 준비

            Start,                  // 출발
            Drive,                  // 주행

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

            Failed,             // 업데이트 실패(업데이트 완료까지 갔으나 body의 CRC16이 일치하지 않는 경우 등)

            NotAvailable,       // 업데이트 불가능 상태(Debug 모드 등)
            RunApplication,     // 어플리케이션 동작 중
            NotRegistered,      // 등록되지 않은 장치

            EndOfType
        };
    }
}
```


<br>
<br>


<a name="ImageType"></a>
## ImageType::Type

펌웨어 이미지 타입(BLE 통신칩에만 사용)

```cpp
namespace ImageType
{
    enum Type
    {
        None,
        
        // 현재 장치의 이미지
        ImageSingle             = 0x10,     // 실행 이미지
        ImageA                  = 0x11,
        ImageB                  = 0x12,
        
        // 펌웨어 이미지
        RawImageSingle          = 0x20,     // 업데이트 이미지, 헤더 포함
        RawImageA               = 0x21,
        RawImageB               = 0x22,
        
        // 암호화 된 이미지
        EncryptedImageSingle    = 0x30,     // 업데이트 이미지, 헤더 포함
        EncryptedImageA         = 0x31,
        EncryptedImageB         = 0x32,
        
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
            None            = 0x00,

            Ready           = 0x01,
            Moving          = 0x02,
            Stop            = 0x03
        };
    }
}
```


<br>
<br>


<a name="Rotation"></a>
## Rotation::Type

모터 회전 방향

E-DRONE에는 총 4개의 모터가 있으며, 왼쪽 앞 모터부터 각각 0, 1, 2, 3번으로 번호가 부여되어 있습니다.

드론 비행 시에 0번과 2번 모터는 시계 방향(Clockwise), 1번과 3번 모터는 반시계 방향(Counterclockwise)으로 회전합니다.

E-DRONE의 모터는 정해진 한 방향으로만 회전합니다.

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
namespace Motor
{
    namespace Part
    {
        enum Type
        {
            Left,   // Left
            Right,  // Right

            EndOfPart,

            All
        };
    }
}
```


<br>
<br>


<a name="DriveEvent"></a>
## DriveEvent::Type

주행 이벤트

```cpp
namespace DriveEvent
{
    enum Type
    {
        None = 0,               // 없음

        Stop = 0x10,            // 정지

        Zigzag,
        Wave,
        LeftTornado,
        RightTornado,
        LeftCircle,
        RightCircle,

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
            Null,           // 무음(100ms)
            
            Melody1,        // 카드 코딩용 멜로디 1
            Melody2,        // 카드 코딩용 멜로디 2
            Melody3,        // 카드 코딩용 멜로디 3
            Melody4,        // 카드 코딩용 멜로디 4
            Melody5,        // 카드 코딩용 멜로디 5
            Melody6,        // 카드 코딩용 멜로디 6
            Melody7,        // 카드 코딩용 멜로디 7
            Melody8,        // 카드 코딩용 멜로디 8
            
            DoReMi,         // 도레미
            DoMiSol,        // 도미솔
            SolMiDo,        // 솔미도
            LaLa,           // 라라
            SiRaSiRa,       // 시라시라
            Do5Sol5Do6,     // 도5솔5도6도5솔5도6
            Do6Sol5Do5,     // 도6솔5도5도6솔5도5
            
            Warning1,       // 경고 1
            Warning2,       // 경고 2
            Warning3,       // 경고 3
            Warning4,       // 경고 4
            
            Du,             // Trim -
            DuDu,           // Trim - End
            DiDic,          // Trim Center
            DiDic2,         // Trim Center 2
            Di,             // Trim +
            DiDi,           // Trim + End
            
            BuzzSound1,     // C6
            BuzzSound2,     // C6, D6
            BuzzSound3,     // C6, D6, E6
            
            Button,
            Shot,
            
            Mode1,
            Mode2,
            Mode3,
            Mode4,
            Mode5,
            Mode6,
            Mode7,
            Mode8,
            
            EndOfType
        };
    }
}
```


<br>


---

<h3>E-DRIVE</H3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. ***Definitions***
5. [Structs](05_structs.md)
6. [Structs - Light](06_structs_light.md)
7. [Structs - Card](07_structs_card.md)

<br>

[Index](index.md)
