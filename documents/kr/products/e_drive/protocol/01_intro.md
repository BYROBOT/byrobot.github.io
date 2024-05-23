**[CODING CAR](index.md)** / **Protocol** / **Intro**

Modified : 2021.6.29

---

* Kramdown table of contents
{:toc .toc}


<br>

# 1. CODING CAR 소개

**CODING CAR**은 코딩 교육용 자동차 로봇입니다.


<br>
<br>
<br>


# 2. 시리얼 통신


## 2.1. 전송 데이터 구조

CODING CAR를 USB와 연결해서 통신하는 경우 송수신 데이터의 구조는 아래와 같습니다.

<table>
    <tr>
        <td><div align="center">0</div></td>
        <td><div align="center">1</div></td>
        <td><div align="center">2</div></td>
        <td><div align="center">3</div></td>
        <td><div align="center">4</div></td>
        <td><div align="center">5</div></td>
        <td><div align="center">...</div></td>
        <td><div align="center">N-1</div></td>
        <td><div align="center">N</div></td>
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="4"><div align="center">Header</div></td>
        <td rowspan="2"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
        <td><div align="center">From</div></td>
        <td><div align="center">To</div></td>
    </tr>
    <tr>
        <td><div align="center">0x0A</div></td>
        <td><div align="center">0x55</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
    </tr>
</table>

<br>

각 항목에 대한 설명은 다음과 같습니다.

<br>

<table>
    <tr>
        <td colspan="2"><div align="center">영역</div></td>
        <td><div align="center">설명</div></td>
    </tr>
    <tr>
        <td colspan="2"><div align="center">Start code</div></td>
        <td><div align="left">데이터 전송 시작을 알림</div></td>
    </tr>
    <tr>
        <td rowspan="4"><div align="center">Header</div></td>
        <td><div align="center">DataType</div></td>
        <td><div align="left">데이터의 형식</div></td>
    </tr>
    <tr>
        <td><div align="center">Length</div></td>
        <td><div align="left">데이터의 길이</div></td>
    </tr>
    <tr>
        <td><div align="center">From</div></td>
        <td><div align="left">데이터를 전송하는 장치의 DeviceType</div></td>
    </tr>
    <tr>
        <td><div align="center">To</div></td>
        <td><div align="left">데이터를 수신 받는 장치의 DeviceType</div></td>
    </tr>
    <tr>
        <td colspan="2"><div align="center">Data</div></td>
        <td><div align="left">전송할 데이터</div></td>
    </tr>
    <tr>
        <td colspan="2"><div align="center">CRC16</div></td>
        <td><div align="left">Header와 Data가 정상적으로 전달되었는지 판별<br><a href="http://www.menie.org/georges/embedded/crc16.html">http://www.menie.org/georges/embedded/crc16.html</a></div></td>
    </tr>
</table>


<br>

Data 영역과 CRC16 영역 모두 Little Endian을 사용하고 있습니다. Little Endian일 때 2바이트 이상의 변수는 하위 바이트가 배열의 앞 부분에 위치합니다. C#에서는 Bitconverter를 사용하시면 편리하게 변경할 수 있습니다.

<table>
    <tr>
        <td><div align="center">16진수 값</div></td>
        <td colspan="2"><div align="center">0x1234</div></td>
    </tr>
    <tr>
        <td><div align="center">배열의 인덱스</div></td>
        <td><div align="center"><b>0</b></div></td>
        <td><div align="center"><b>1</b></div></td>
    </tr>
    <tr>
        <td><div align="center">Big Endian</div></td>
        <td><div align="center">12</div></td>
        <td><div align="center">34</div></td>
    </tr>
    <tr>
        <td><div align="center">Little Endian</div></td>
        <td><div align="center">34</div></td>
        <td><div align="center">12</div></td>
    </tr>
</table>

<br>

<table>
    <tr>
        <td><div align="center">16진수 값</div></td>
        <td colspan="4"><div align="center">0x12345678</div></td>
    </tr>
    <tr>
        <td><div align="center">배열의 인덱스</div></td>
        <td><div align="center"><b>0</b></div></td>
        <td><div align="center"><b>1</b></div></td>
        <td><div align="center"><b>2</b></div></td>
        <td><div align="center"><b>3</b></div></td>
    </tr>
    <tr>
        <td><div align="center">Big Endian</div></td>
        <td><div align="center">12</div></td>
        <td><div align="center">34</div></td>
        <td><div align="center">56</div></td>
        <td><div align="center">78</div></td>
    </tr>
    <tr>
        <td><div align="center">Little Endian</div></td>
        <td><div align="center">78</div></td>
        <td><div align="center">56</div></td>
        <td><div align="center">34</div></td>
        <td><div align="center">12</div></td>
    </tr>
</table>


<br>
<br>


## 2.2. 사용 시 주의사항

- 모든 장치는 데이터를 요청했을 경우에만 관련된 데이터를 응답으로 전송합니다.

- 데이터를 수신받는 장치를 지정한 경우, 해당 장치는 데이터를 요청받은 경우가 아니라면 Ack를 응답으로 보냅니다.

- Broadcasting으로 데이터를 전송한 경우, 데이터 요청이 아닌 일반적인 명령이었다면 해당 명령을 처리할 수 있는 장치는 받은 명령을 실행합니다.

- Broadcasting으로 데이터를 전송한 경우, 데이터 요청을 전달하였다면 해당 데이터에 대해 응답을 할 수 있는 장치가 응답을 합니다. 이 과정에서 두 개 이상의 장치가 같은 데이터에 대해 응답이 가능하다면 데이터 송수신 간에 충돌이 발생할 수 있습니다. 사용 시 주의하셔야 합니다.

- Broadcasting에 대해서는 Ack를 응답으로 보내지 않습니다.


<br>
<br>


## 2.3. 시리얼 통신 설정


|영역       | 설정값 |
|:---------:|:------:|
| Baud Rate | 57600  |
| Parity    | None   |
| Data Bits | 8      |
| Stop Bits | 1      |


<br>
<br>


## 2.4. 드라이버 설치

CODING CAR는 USB로 PC와 연결할 때 윈도우10인 경우 자동으로 인식합니다. 그 외에 장치를 인식하지 못하는 경우 별도의 드라이버를 설치하셔야 합니다.


<br>
<br>
<br>



# 3. Bluetooth Low Energy(Bluetooth SMART)

**CODING CAR**는 무선 연결에 Bluetooth Low Energy(이하 BLE)를 사용합니다.
<br>
**CODING CAR**에서 사용하는 **Service**와 **Characteristic**은 다음과 같습니다.

<br>

| Service       | Characteristic | UUID                                   | 데이터 이동 방향       |
|:-------------:|:--------------:|:--------------------------------------:|:----------------------:|
| DRONE_SERVICE |                | *C320DF00-7891-11E5-8BCF-FEFF819CDC9F* |                        |
|       ├       | DRONE_DATA     | *C320DF01-7891-11E5-8BCF-FEFF819CDC9F* | 자동차 → 앱 (*Notify*) |
|       └       | DRONE_CONF     | *C320DF02-7891-11E5-8BCF-FEFF819CDC9F* | 앱 → 자동차 (*Write*)  |

<br>
<br>

## 3.1. 전송 데이터 구조

<table>
    <tr>
        <td><div align="center">0</div></td>
        <td><div align="center">1</div></td>
        <td><div align="center">2</div></td>
        <td><div align="center">3</div></td>
        <td><div align="center">...</div></td>
        <td><div align="center">N-1</div></td>
        <td><div align="center">N</div></td>
    </tr>
    <tr>
        <td colspan="4"><div align="center">Header</div></td>
        <td colspan="3" rowspan="2"><div align="center">Data</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
        <td><div align="center">From</div></td>
        <td><div align="center">To</div></td>
    </tr>
    <tr>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
    </tr>
</table>

<br>

각 항목에 대한 설명은 다음과 같습니다.

<br>

<table>
    <tr>
        <td colspan="2"><div align="center">영역</div></td>
        <td><div align="center">설명</div></td>
    </tr>
    <tr>
        <td rowspan="4"><div align="center">Header</div></td>
        <td><div align="center">DataType</div></td>
        <td><div align="left">데이터의 형식</div></td>
    </tr>
    <tr>
        <td><div align="center">Length</div></td>
        <td><div align="left">데이터의 길이</div></td>
    </tr>
    <tr>
        <td><div align="center">From</div></td>
        <td><div align="left">데이터를 전송하는 장치의 DeviceType</div></td>
    </tr>
    <tr>
        <td><div align="center">To</div></td>
        <td><div align="left">데이터를 수신 받는 장치의 DeviceType</div></td>
    </tr>
    <tr>
        <td colspan="2"><div align="center">Data</div></td>
        <td><div align="left">전송할 데이터</div></td>
    </tr>
</table>


전체 길이는 최대 20byte 이하로만 사용 가능합니다.

<br>
<br>

## 3.2. 데이터 송수신 규칙

- 데이터를 전송하는 주기는 **Android**인 경우 *50ms*, **iOS**인 경우 *100ms*를 권장
- CODING CAR에 데이터를 요청한 경우엔 요청한 데이터를 응답으로 보냄. 이외의 경우에는 Ack를 응답. Control 명령은 Ack 및 어떤 응답도 보내지 않음
- **앱**에서 **CODING CAR**에 명령 시에는 *DRONE_CONF*에 전달할 데이터를 **Write**
- **CODING CAR**이 **앱**으로 데이터를 보내는 경우엔 *DRONE_DATA*로 **Notify**를 전송


<br>
<br>

<br>

---

<h3>CODING CAR</H3>

1. **Intro**
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. [Structs](05_structs.md)
6. [Structs - Light](06_structs_light.md)
7. [Structs - Card](07_structs_card.md)

<br>

[Index](index.md)
