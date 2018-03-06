***PETRONE / BLE / Protocol / FirmwareUpdate***<br>
Modified : 2018.3.6

---

#### 페트론 펌웨어 업데이트 방법을 소개합니다.

---

* Kramdown table of contents
{:toc .toc}


<br>

## 페트론 펌웨어 구성

페트론은 **제어 펌웨어**와 **통신 펌웨어**의 두 가지 펌웨어로 구성되어 있습니다. 그리고 각각의 펌웨어는 내부 플래시 공간을 두 개의 영역으로 나누어 **ImageA** 영역과 **ImageB** 영역으로 분리되어 있습니다. 펌웨어 업데이트 시에는 **ImageA**에서 **ImageB**, **ImageB**에서 **ImageA**로 업데이트를 진행합니다. 따라서 현재 구동중인 드론 메인펌웨어가 **ImageA**라면 **ImageB**를 전송해야합니다.

<br>
<br>

## 펌웨어 파일 헤더 구조

펌웨어 파일의 처음 16바이트는 아래와 같이 구성되어 있습니다. 이 부분을 읽어서 펌웨어 파일에 대한 정보를 확인할 수 있습니다.<br>
### <a name="UpdaterHeader">Updater::Header</a>
```cpp
namespace Updater
{
    struct Header
    {
        u16     reserve;        // 예약 [2byte]

        u32     length;         // 펌웨어 길이(헤더 16바이트 제외한 실제 펌웨어의 길이)[4byte]

        u8      year;           // 펌웨어 배포일[년 2byte]
        u8      month;          // 펌웨어 배포일[월 1byte]
        u8      day;            // 펌웨어 배포일[일 1byte

        u16     version;        // 펌웨어 버젼[2byte]
        u8      imageType;      // 펌웨어 이미지 타입[1byte]
        u32     deviceType;     // 업데이트 대상 장치[4byte]
    };
}
```
- imageType : [System::ImageType::Type](04_definitions.md#ImageType)
- deviceType : [System::DeviceType::Type](04_definitions.md#DeviceType)

<br>
<br>

## 펌웨어 업데이트 절차

1. 펌웨어 업데이트를 시작하기 전에 서버로부터 펌웨어 파일 4개(제어 펌웨어 A, B, 통신 펌웨어 A, B)를 받습니다.

2. 펌웨어 파일 앞 부분 16바이트를 읽어 각각의 파일에 대한 정보를 확인합니다. ([Updater::Header](#UpdaterHeader))

3. 페트론에 현재 실행중인 펌웨어의 정보를 요청합니다. ([Protocol::UpdateLookupTarget](06_structs.md#UpdateLookupTarget))

4. 각각의 요청에 대해 드론은 [Protocol::UpdateInformation](06_structs.md#UpdateInformation) 구조체를 응답으로 보냅니다.

5. 드론의 펌웨어와 서버로부터 받은 펌웨어의 정보를 비교하여 적절한 펌웨어를 전송합니다. ([Protocol::Update](06_structs.md#Update))
    - 펌웨어 업데이트 시에는 파일에서 16바이트씩 데이터를 잘라서 전송합니다. 1블럭은 16바이트입니다.
    - 드론에서 실행중인 펌웨어 이미지 타입이 **ImageA**인 경우 이미지 타입이 **RawImageB** 또는 **EncryptedImageB**인 펌웨어를 전송합니다. 반대로 실행중인 펌웨어 이미지 타입이 **ImageB**인 경우 이미지 타입이 **RawImageA** 또는 **EncryptedImageA**인 펌웨어를 전송하면 됩니다.
    - BLE를 통해 펌웨어 데이터 전송 시 별다른 문제가 없다면 드론은 응답을 하지 않습니다. 만약 전송하는 데이터를 잃어버리거나하는 문제가 발생하면 펌웨어 업데이트 위치 정정을([Protocol::UpdateLocationCorrect](06_structs.md#UpdateLocationCorrect)) 응답으로 전송합니다. 이 구조체를 받은 경우 해당 위치부터 다시 전송을 시작해야 합니다.
    - 유선 시리얼 통신으로 펌웨어 데이터를 전송하면, 매번 블럭 전송 시 응답으로 펌웨어 업데이트 위치 정정을([Protocol::UpdateLocationCorrect](06_structs.md#UpdateLocationCorrect)) 전송합니다.

6. 페트론 펌웨어 업데이트 완료 처리
    - 펌웨어 업데이트가 정상적으로 완료된 경우에만 새로운 이미지로 부팅을 합니다. 만약 중간에 실패하더라도 이전 펌웨어를 보존하고 있기 때문에 대부분의 경우 펌웨어 업데이트를 실패해도 큰 문제가 발생하지는 않습니다.
    - 제어 펌웨어를 업데이트 한 경우엔 펌웨어 업데이트가 완료되면 바로 제어 프로그램을 재시작합니다. 통신 펌웨어를 업데이트 한 경우엔 BLE 연결을 끊은 이후에 통신 프로그램을 재시작합니다.

<br>
<br>

## 펌웨어 업데이트와 관련된 주의 사항

- 펌웨어 업데이트 시 이전 펌웨어로 돌리는 것은 권장하지 않습니다. 대부분의 업데이트는 이전 펌웨어에서 발생한 문제를 해결하기 위해 제공되므로, 이전 펌웨어로 변경하는 경우 예상하지 못하는 문제가 발생할 수 있습니다. 또한 일부 업데이트의 경우 새로운 하드웨어 지원을 추가하는 경우가 있습니다. 이런 경우엔 이전 펌웨어로 변경하면 해당 하드웨어가 동작하지 않을 수 있습니다.

- 펌웨어 업데이트와 함께 프로토콜이 변경되는 경우 변경 사항이 현재 문서에도 반영됩니다. 만약 기존 펌웨어로 변경할 경우 프로토콜이 문서와 일치하지 않는 문제가 발생할 수 있고, 그로인해 원하는 동작이 실행되지 않거나 위험한 오동작이 발생할 수 있습니다.

- 펌웨어 업데이트는 바이로봇에서 제공하는 앱 또는 PC 프로그램을 통해 진행하는 것을 권장합니다.


<br>
<br>

## 데이터 요청 예제

- 제어 펌웨어 정보 요청 패킷(시리얼 통신)

<table>
    <tr>
        <td><div align="center">0</div></td>
        <td><div align="center">1</div></td>
        <td><div align="center">2</div></td>
        <td><div align="center">3</div></td>
        <td><div align="center">4</div></td>
        <td><div align="center">5</div></td>
        <td><div align="center">6</div></td>
        <td><div align="center">7</div></td>
        <td><div align="center">8</div></td>
        <td><div align="center">9</div></td>
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="4"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">90</div></td>
        <td><div align="center">04</div></td>
        <td><div align="center">01</div></td>
        <td><div align="center">00</div></td>
        <td><div align="center">00</div></td>
        <td><div align="center">00</div></td>
        <td><div align="center">16</div></td>
        <td><div align="center">31</div></td>
    </tr>
</table>

- 통신 펌웨어 정보 요청 패킷(시리얼 통신)

<table>
    <tr>
        <td><div align="center">0</div></td>
        <td><div align="center">1</div></td>
        <td><div align="center">2</div></td>
        <td><div align="center">3</div></td>
        <td><div align="center">4</div></td>
        <td><div align="center">5</div></td>
        <td><div align="center">6</div></td>
        <td><div align="center">7</div></td>
        <td><div align="center">8</div></td>
        <td><div align="center">9</div></td>
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="4"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">90</div></td>
        <td><div align="center">04</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">00</div></td>
        <td><div align="center">00</div></td>
        <td><div align="center">00</div></td>
        <td><div align="center">CA</div></td>
        <td><div align="center">AA</div></td>
    </tr>
</table>

<br>

---

### PETRONE

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. [Base Structs](05_base_structs.md)
6. [Structs](06_structs.md)
7. [Structs - Light](07_structs_light.md)
8. **Firmware Update**


### PETRONE Link

1. [Intro](link/01_intro.md)
2. [DataType](link/02_datatype.md)
3. [Definitions](link/03_definitions.md)
4. [Structs](link/04_structs.md)
5. [Examples](link/05_examples.md)

<br>

[Index](index.md)

<br>

