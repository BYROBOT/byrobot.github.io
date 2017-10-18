***DRONEFIGHTER2017 / Protocol / Intro***<br>
Modified : 2017.10.18

---

<br>

# 1. DRONE FIGHTER 2017 소개

**DRONE FIGHTER 2017**은 Entry에서 드론파이터를 사용하려고 만든 펌웨어입니다.


<br>
<br>


# 2. 전송 데이터 구조

DRONE FIGHTER 2017은 조종기를 통해 드론과 연결하거나 드론에 직접 USB를 연결하여 PC와 통신을 합니다.

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


# 3. 사용 시 주의사항

- 모든 장치는 데이터를 요청했을 경우에만 관련된 데이터를 응답으로 전송합니다.

- 데이터를 수신받는 장치를 지정한 경우, 해당 장치는 데이터를 요청받은 경우가 아니라면 Ack를 응답으로 보냅니다.

- Broadcasting으로 데이터를 전송한 경우, 데이터 요청이 아닌 일반적인 명령이었다면 해당 명령을 처리할 수 있는 장치는 받은 명령을 실행합니다.

- Broadcasting으로 데이터를 전송한 경우, 데이터 요청을 전달하였다면 해당 데이터에 대해 응답을 할 수 있는 장치가 응답을 합니다. 이 과정에서 두 개 이상의 장치가 같은 데이터에 대해 응답이 가능하다면 데이터 송수신 간에 충돌이 발생할 수 있습니다. 사용 시 주의하셔야 합니다.

- Broadcasting에 대해서는 Ack를 응답으로 보내지 않습니다.


<br>
<br>


# 4. 시리얼 통신 설정


|영역 | 설정값 |
|:---:|:---:|
| Baud Rate | 115200 |
| Parity | None      |
| Data Bits | 8 |
| Stop Bits | 1 |


<br>
<br>


# 5. 드라이버 설치

- 드론파이터 시뮬레이터를 설치하셨다면 추가로 드라이버 설치없이 사용 가능합니다.
- 엔트리 하드웨어 프로그램에서 드라이버를 설치하실 수 있습니다.

<br>

---

### DRONE FIGHTER 2017

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. [Structs](05_structs.md)
6. [Structs - Light](06_structs_light.md)

<br>

[Index](index.md)