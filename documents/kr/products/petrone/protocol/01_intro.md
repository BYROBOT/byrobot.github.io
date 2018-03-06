***PETRONE / BLE / Protocol / Intro***<br>
Modified : 2018.3.6

---

* Kramdown table of contents
{:toc .toc}


<br>

# 1. Bluetooth Low Energy(Bluetooth SMART)

**PETRONE**은 무선 연결에 Bluetooth Low Energy(이하 BLE)를 사용합니다.
<br>
**PETRONE**에서 사용하는 **Service**와 **Characteristic**은 다음과 같습니다.

| Service | Characteristic | UUID | 데이터 이동 방향 |
|:---:|:---:|:---:|:---:|
| DRONE_SERVICE | | *C320DF00-7891-11E5-8BCF-FEFF819CDC9F* | |
| ├ | DRONE_DATA | *C320DF01-7891-11E5-8BCF-FEFF819CDC9F* | 드론 → 앱 (*Notify*) |
| └ | DRONE_CONF | *C320DF02-7891-11E5-8BCF-FEFF819CDC9F* | 앱 → 드론 (*Write*) |

<br>
<br>

# 2. 전송 데이터 구조
<table>
    <tr>
        <td><div align="center">0</div></td>
        <td><div align="center">1</div></td>
        <td><div align="center">2</div></td>
        <td><div align="center">...</div></td>
        <td><div align="center">N-1</div></td>
        <td><div align="center">N</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td colspan="5"><div align="center">Data</div></td>
    </tr>
</table>

- 첫 번째 바이트는 데이터 타입을 의미
- 두 번째 바이트부터는 첫 번째 바이트(데이터의 타입)에서 정의한 데이터 전달
- 전체 길이는 최대 20byte

<br>
<br>

# 3. 데이터 송수신 규칙

- 데이터를 전송하는 주기는 **Android**인 경우 *50ms*, **iOS**인 경우 *100ms*를 권장
- PETRONE에 데이터를 요청한 경우엔 요청한 데이터를 응답으로 보냄. 이외의 경우에는 Ack를 응답. Control 명령은 Ack 및 어떤 응답도 보내지 않음
- 앱에서 드론에 명령 시에는 *DRONE_CONF*에 전달할 데이터를 **Write**
- 드론이 앱으로 데이터를 보내는 경우엔 *DRONE_DATA*로 **Notify**를 전송


<br>

---

### PETRONE

1. ***Intro***
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. [Base Structs](05_base_structs.md)
6. [Structs](06_structs.md)
7. [Structs - Light](07_structs_light.md)
8. [Firmware Update](08_firmware_update.md)


### PETRONE Link

1. [Intro](link/01_intro.md)
2. [DataType](link/02_datatype.md)
3. [Definitions](link/03_definitions.md)
4. [Structs](link/04_structs.md)
5. [Examples](link/05_examples.md)

<br>

[Index](index.md)

<br>

