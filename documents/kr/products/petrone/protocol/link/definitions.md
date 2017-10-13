***PETRONE / LINK / Protocol / Definitions***<br>
Modified : 2017.07.11

---

#### PETRONE LINK에서 사용하고 있는 기본 정의들을 소개합니다.

---

<br>

## <a name="CommandType">Protocol::CommandType::Type</a>
기존 PETRONE의 명령 타입에 LINK용 명령들을 추가하여 사용합니다.

```cpp
namespace Protocol
{
    namespace CommandType
    {
        enum Type
        {
            // PETRONE LINK
            LinkModeBroadcast = 0xE0,   // LINK 송수신 모드 전환
            LinkSystemReset,            // 시스템 재시작
            LinkDiscoverStart,          // 장치 검색 시작
            LinkDiscoverStop,           // 장치 검색 중단
            LinkConnect,                // 지정한 인덱스의 장치 연결
            LinkDisconnect,             // 연결 해제
            LinkRssiPollingStart,       // RSSI 수집 시작
            LinkRssiPollingStop,        // RSSI 수집 중단
        };
    }
}
```

 - [Protocol::CommandType::Type](../definitions.md#CommandType)

 
<br>
<br>


## <a name="ModeLink">System::ModeLink::Type</a>
LINK의 동작 모드입니다


```cpp
namespace System
{
    namespace ModeLink
    {
        enum Type
        {
            None = 0,       // 없음
            
            Boot,           // 부팅     
            Ready,          // 대기(연결 전)                
            Connecting,     // 장치 연결 중
            Connected,      // 장치 연결 완료(정상 연결 됨)
            Disconnecting,  // 장치 연결 해제 중
                 
            ReadyToReset,   // 리셋 대기(1초 뒤 리셋)
            
            EndOfType
        };
    }
}
```


<br>
<br>


## <a name="ModeLinkBroadcast">System::ModeLinkBroadcast::Type</a>
LINK Broadcast 모드입니다.<br>
LINK에서는 LINK와 연결된 아두이노 장치의 업데이트를 지원하고 있습니다. 이 때 데이터 이동 경로를 구분하기 위해 ModeLinkBroadcast라는 상태를 추가하였습니다.


```cpp
namespace System
{
    namespace ModeLinkBroadcast
    {
        enum Type
        {
            None = 0,       // 없음
            
            Mute,           // 데이터 송신 중단 - LED 노란색 Dimming
            Active,         // 요청 데이터 및 전체 이벤트 데이터 전송
            Passive,        // 요청 데이터 및 중요 이벤트 데이터만 전송
            
            EndOfType
        };
    }
}
```

버튼을 한 번 누를 때마다 ***Mute -> Passive***, ***Passive -> Mute***로 모드가 바뀝니다. 
<br>

버튼을 5초 이상 연속으로 누르고 있으면 초기 모드가 변경됩니다. 초기 모드가 Mute인 경우 Passive로, Passive인 경우 Mute로 변경됩니다. 초기 모드 선택은 플래시 메모리에 저장되어 다음 번 전원 연결시에도 기존에 선택한 모드를 유지합니다.
<br>

초기 상태는 Mute이며, 이 때 아두이노 장치에 펌웨어를 다운로드 할 수 있습니다. Mute 상태일 때 Active모드로 전환하는 명령을 아두이노 장치에서 LINK로 전송하면, LINK 모듈이 Active 모드로 전환되어 페트론과 연결할 수 있는 상태가 됩니다. Active와 Passive는 PETRONE과 통신을 할 수 있는 상태입니다. Active 또는 Passive 상태인 경우 아두이노 장치에 펌웨어 다운로드를 시작하면 처음 전송되는 2바이트를 확인하여 Mute 모드로 자동 전환합니다.


<br>
<br>


## <a name="EventLink">System::EventLink::Type</a>
LINK 모듈 내부에서 BLE 장치와 관련된 이벤트를 전달할 때 사용하는 열거체입니다.


```cpp
namespace System
{
    namespace EventLink
    {
        enum Type
        {
            None = 0,                           // 없음
            
            SystemReset,                        // 시스템 리셋
            
            Initialized,                        // 장치 초기화 완료
            
            Scanning,                           // 장치 검색 시작
            ScanStop,                           // 장치 검색 중단
            
            FoundDroneService,                  // 드론 서비스 검색 완료
            
            Connecting,                         // 장치 연결 시작       
            Connected,                          // 장치 연결
            
            ConnectionFaild,                    // 연결 실패
            ConnectionFaildNoDevices,           // 연결 실패 - 장치가 없음
            ConnectionFaildNotReady,            // 연결 실패 - 대기 상태가 아님
            
            PairingStart,                       // 페어링 시작
            PairingSuccess,                     // 페어링 성공
            PairingFaild,                       // 페어링 실패
            
            BondingSuccess,                     // Bonding 성공
            
            LookupAttribute,                    // 장치 서비스 및 속성 검색(GATT Event 실행)
                 
            RssiPollingStart,                   // RSSI 풀링 시작
            RssiPollingStop,                    // RSSI 풀링 중지

            DiscoverService,                    // 서비스 검색
            DiscoverCharacteristic,             // 속성 검색
            DiscoverCharacteristicDroneData,    // 속성 검색
            DiscoverCharacteristicDroneConfig,  // 속성 검색
            DiscoverCharacteristicUnknown,      // 속성 검색
            DiscoverCCCD,                       // CCCD 검색
            
            ReadyToControl,                     // 제어 준비 완료
            
            Disconnecting,                      // 장치 연결 해제 시작
            Disconnected,                       // 장치 연결 해제 완료
            
            GapLinkParamUpdate,                 // GAP_LINK_PARAM_UPDATE_EVENT
            
            RspReadError,                       // RSP 읽기 오류
            RspReadSuccess,                     // RSP 읽기 성공
            
            RspWriteError,                      // RSP 쓰기 오류
            RspWriteSuccess,                    // RSP 쓰기 성공
            
            SetNotify,                          // Notify 활성화
            
            Write,                              // 데이터 쓰기 이벤트
                 
            EndOfType
        };
    }
}
```


<br>

---

### PETRONE

1. [Intro](../intro.md)
2. [Typedef](../typedef.md)
3. [DataType](../datatype.md)
4. [Definitions](../definitions.md)
5. [Base Structs](../base_structs.md)
6. [Structs](../structs.md)
7. [Structs - Light](../structs_light.md)
8. [Firmware Update](../firmware_update.md)


### PETRONE Link

1. [Intro](intro.md)
2. [DataType](datatype.md)
3. ***Definitions***
4. [Structs](structs.md)
5. [Examples](examples.md)

<br>

[Index](../index.md)

<br>

[Home](../../../../../README.md)

