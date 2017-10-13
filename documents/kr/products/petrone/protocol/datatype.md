***PETRONE / BLE / Protocol / DataType***<br>
Modified : 2017.07.11

---

#### 데이터 타입을 소개합니다.

---

<br>

## <a name="DataType">Protocol::DataType::Type</a>
데이터 타입

```cpp
namespace Protocol
{
    namespace DataType
    {
        enum Type
        {
            None = 0,                   // 없음

            // 시스템 정보
            Ping,                       // 통신 확인(reserved)
            Ack,                        // 데이터 수신에 대한 응답
            Error,                      // 오류(reserved)
            Request,                    // 지정한 타입의 데이터 요청
            
            // 조종, 명령 
            Control = 0x10,             // 조종
            Command,                    // 명령
            Command2,                   // 다중 명령(2가지 설정을 동시에 변경)
            Command3,                   // 다중 명령(3가지 설정을 동시에 변경)
            
            // LED
            LightMode = 0x20,           // LED 모드 지정
            LightMode2,                 // LED 모드 2개 지정
            LightModeCommand,           // LED 모드, 커맨드
            LightModeCommandIr,         // LED 모드, 커맨드, IR 데이터 송신
            LightModeColor,             // LED 모드 3색 직접 지정
            LightModeColor2,            // LED 모드 3색 직접 지정 2개
            
            LightEvent,                 // LED 이벤트
            LightEvent2,                // LED 이벤트 2개, 
            LightEventCommand,          // LED 이벤트, 커맨드
            LightEventCommandIr,        // LED 이벤트, 커맨드, IR 데이터 송신
            LightEventColor,            // LED 이벤트 3색 직접 지정
            LightEventColor2,           // LED 이벤트 3색 직접 지정 2개
            
            LightModeDefaultColor,      // LED 초기 모드 3색 직접 지정
            LightModeDefaultColor2,     // LED 초기 모드 3색 직접 지정 2개
            
            // 상태 
            Address = 0x30,             // 장치 주소
            State,                      // 드론의 상태(비행 모드, 방위기준, 배터리량)
            Attitude,                   // 드론의 자세(Vector)
            GyroBias,                   // 자이로 바이어스 값(Vector)
            TrimAll,                    // 전체 트림
            TrimFlight,                 // 비행 트림
            TrimDrive,                  // 주행 트림
            
            CountFlight,                // 비행 관련 카운트 
            CountDrive,                 // 주행 관련 카운트 
            
            // 데이터 송수신
            IrMessage = 0x40,           // IR 데이터 송수신
            
            // 센서 및 제어
            ImuRawAndAngle = 0x50,      // IMU Raw + Angle
            Pressure,                   // 압력 센서 데이터
            ImageFlow,                  // ImageFlow
            Button,                     // 버튼 입력
            Battery,                    // 배터리
            Motor,                      // 모터 제어 및 현재 제어값 확인
            Temperature,                // 온도 데이터
            Range,                      // 거리 센서
        
            // 펌웨어 업데이트
            UpdateLookupTarget = 0x90,	// 업데이트 대상 장치 검색
            UpdateInformation,          // 업데이트 정보
            Update,                     // 업데이트 16바이트 단위
            UpdateLocationCorrect,      // 업데이트 위치 정정
            
            EndOfType
        };
    }
}
```


<br>

---

### PETRONE

1. [Intro](intro.md)
2. [Typedef](typedef.md)
3. ***DataType***
4. [Definitions](definitions.md)
5. [Base Structs](base_structs.md)
6. [Structs](structs.md)
7. [Structs - Light](structs_light.md)
8. [Firmware Update](firmware_update.md)


### PETRONE Link

1. [Intro](link/intro.md)
2. [DataType](link/datatype.md)
3. [Definitions](link/definitions.md)
4. [Structs](link/structs.md)
5. [Examples](link/examples.md)

<br>

[Index](index.md)

<br>

[Home](../../../../README.md)
