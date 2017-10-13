***PETRONE / LINK / Protocol / Structs***<br>
Modified : 2017.07.11

---

#### 송신 데이터 예제

---

<br>

## <a name="LinkModeBroadcast_Active">LinkModeBroadcast - Active</a>
LINK를 Active 모드로 변경할 때 사용하는 명령입니다. PC 또는 아두이노 보드에서 LINK 모듈과 통신을 할 때 가장 먼저 이 명령을 전송하면 LINK 모듈의 버튼을 두 번 누르지 않고도 페트론 연결 모드로 전환됩니다. Active 모드일 때 아두이노 펌웨어를 업데이트하면 Mute모드로 자동 전환되므로 모드 전환은 이 명령만 사용하시면 됩니다.
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="2"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">11</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">E0</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">83</div></td>
        <td><div align="center">33</div></td>
    </tr>
</table>

<br>
<br>

## <a name="LinkSystemReset">LinkSystemReset</a>
LINK를 Soft Reset 할 때 사용하는 명령입니다. 동작 중 문제가 발생하였으나 시리얼 통신은 가능할 때 이 명령을 보내면 모듈을 리셋합니다.
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="2"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">11</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">E1</div></td>
        <td><div align="center">00</div></td>
        <td><div align="center">F0</div></td>
        <td><div align="center">20</div></td>
    </tr>
</table>

<br>
<br>

## <a name="LinkState">LinkState</a>
LINK 모듈의 현재 상태를 확인하고자 할 때 해당 데이터를 요청하는 명령입니다.
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="2"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">11</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">90</div></td>
        <td><div align="center">E0</div></td>
        <td><div align="center">B6</div></td>
        <td><div align="center">E6</div></td>
    </tr>
</table>

<br>
<br>

## <a name="LinkDiscoverStart">LinkDiscoverStart</a>
BLE 장치를 검색할 때 사용하는 명령입니다.
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="2"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">11</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">E2</div></td>
        <td><div align="center">00</div></td>
        <td><div align="center">A3</div></td>
        <td><div align="center">75</div></td>
    </tr>
</table>

<br>
<br>

## <a name="Connect_0">Connect 0</a>
Discover Start를 통해 검색된 장치 중 0번 장치에 연결할 때 사용합니다. 6번째 바이트는 연결할 장치의 인덱스를 의미합니다.
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="2"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">11</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">E4</div></td>
        <td><div align="center">00</div></td>
        <td><div align="center">05</div></td>
        <td><div align="center">DF</div></td>
    </tr>
</table>

<br>
<br>

## <a name="Connect_1">Connect 1</a>
Discover Start를 통해 검색된 장치 중 1번 장치에 연결할 때 사용합니다.
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="2"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">11</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">E4</div></td>
        <td><div align="center">01</div></td>
        <td><div align="center">24</div></td>
        <td><div align="center">CF</div></td>
    </tr>
</table>

<br>
<br>

## <a name="Connect_2">Connect 2</a>
Discover Start를 통해 검색된 장치 중 2번 장치에 연결할 때 사용합니다.
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="2"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">11</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">E4</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">47</div></td>
        <td><div align="center">FF</div></td>
    </tr>
</table>

<br>
<br>

## <a name="Connect_1">Disconnect</a>
연결을 해제할 때 사용하는 명령입니다.
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="2"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">11</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">E5</div></td>
        <td><div align="center">00</div></td>
        <td><div align="center">34</div></td>
        <td><div align="center">EC</div></td>
    </tr>
</table>

<br>
<br>

## <a name="RSSI_polling_start">RSSI polling start</a>
현재 연결된 장치의 RSSI 값 스캔을 시작할 때 사용하는 명령입니다. 여기에서는 6번째 바이트의 값을 02로 지정하였습니다. 이때에는 이 값에 100을 곱한 200ms 주기로 RSSI 값을 스캔합니다.
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="2"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">11</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">E6</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">25</div></td>
        <td><div align="center">99</div></td>
    </tr>
</table>

<br>
<br>

## <a name="RSSI_polling_stop">RSSI polling stop</a>
현재 연결된 장치의 RSSI 값 스캔을 중단할 때 사용하는 명령입니다.
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="2"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">11</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">E7</div></td>
        <td><div align="center">00</div></td>
        <td><div align="center">56</div></td>
        <td><div align="center">8A</div></td>
    </tr>
</table>

<br>
<br>

## <a name="Address">Address</a>
LINK 모듈과 연결된 PETRONE의 장치 주소를 요청하는 명령입니다.
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="2"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">11</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">90</div></td>
        <td><div align="center">30</div></td>
        <td><div align="center">CB</div></td>
        <td><div align="center">2D</div></td>
    </tr>
</table>

<br>
<br>

## <a name="LED_Dimming_Yellow">LED Dimming - Yellow</a>
PETRONE과 연결된 경우, 아래의 명령을 보내면 프로펠러 쪽 LED들이 노란색으로 밝아졌다가 어두워지는 동작을 반복합니다.
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="3"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">20</div></td>
        <td><div align="center">03</div></td>
        <td><div align="center">45</div></td>
        <td><div align="center">8B</div></td>
        <td><div align="center">07</div></td>
        <td><div align="center">B0</div></td>
        <td><div align="center">D2</div></td>
    </tr>
</table>

<br>
<br>

## <a name="LED_Dimming_Cyan">LED Dimming - Cyan</a>
PETRONE과 연결된 경우, 아래의 명령을 보내면 프로펠러 쪽 LED들이 하늘색으로 밝아졌다가 어두워지는 동작을 반복합니다.
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="3"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">20</div></td>
        <td><div align="center">03</div></td>
        <td><div align="center">45</div></td>
        <td><div align="center">14</div></td>
        <td><div align="center">07</div></td>
        <td><div align="center">65</div></td>
        <td><div align="center">DA</div></td>
    </tr>
</table>

<br>
<br>

## <a name="LED_Dimming_Red">LED Dimming - Red</a>
PETRONE과 연결된 경우, 아래의 명령을 보내면 프로펠러 쪽 LED들이 빨간색으로 밝아졌다가 어두워지는 동작을 반복합니다.
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="3"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">20</div></td>
        <td><div align="center">03</div></td>
        <td><div align="center">45</div></td>
        <td><div align="center">72</div></td>
        <td><div align="center">07</div></td>
        <td><div align="center">E9</div></td>
        <td><div align="center">7B</div></td>
    </tr>
</table>







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
3. [Definitions](definitions.md)
4. [Structs](structs.md)
5. ***Examples***

<br>

[Index](../index.md)

<br>

[Home](../../../../../README.md)

