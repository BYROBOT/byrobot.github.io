**[E-DRONE](/documents/kr/products/e_drone/) update log**

Modified : 2022.1.4

---

* Kramdown table of contents
{:toc .toc}


<br>


# 2022.1.3

- Drone: 21.8.1
- Drone(4m): 21.9.1
- **Controller: 22.1.1**
> - 드론 이외의 장치에서 LED 제어 명령을 전송하면 LED 외부 제어 모드로 변경되고, 드론에서 전송하는 LED 제어 명령과 내부에서 발생하는 LED 제어 명령을 무시함. 재시작 시 원래 상태로 복귀(파이썬, 엔트리 등에서 LED 조작 명령을 내렸을 때 내부 LED 제어 명령 때문에 원하는 동작이 되지 않는 경우를 막기 위해 수정함)



[Download](https://drive.google.com/file/d/1lSOF1ro_jGrwLt4BLirGc6k9uzYmGE-V/view?usp=sharing)


<br>

---


# 2021.12.9

- Drone: 21.8.1
- Drone(4m): 21.9.1
- **Controller: 21.12.3**
> - E-DRONE 조종기 통신 문제 수정



[Download](https://drive.google.com/file/d/19P9mzzhSsGklYN4qO06KTCx7J9rY9d4B/view?usp=sharing)


<br>

---


# 2021.9.1

- Drone: 21.8.1
- **Drone(4m): 21.9.1**
> - 드론 외부 연결 UART의 속도를 Drone4Link 프로그램에서 변경할 수 있게 함
- Controller: 21.8.1



[Download](https://drive.google.com/file/d/1l_zuPRWYpwJX83lwizzxs05m7hsXHcGe/view?usp=sharing)


<br>

---


# 2021.8.3

- **Drone: 21.8.1**
- **Drone(4m): 21.8.1**
- **Controller: 21.8.1**
> - 페어링 시 조종기가 페어링 데이터에 대해 응답만 하던 것을 일정한 주기로 전송하도록 변경



[Download](https://drive.google.com/file/d/1KAM4_VVC3r3njiZWqNGQ5YS_thLdAagm/view?usp=sharing)


<br>

---


# 2021.7.20

- Drone: 21.3.2
- Drone(4m): 21.3.3
- **Controller: 21.7.1**
> - 드론 배터리가 15% 이하이거나 Low Battry 오류가 활성화 된 경우 조종기에서 드론 배터리 잔량 경고를 표시하게 함



[Download](https://drive.google.com/file/d/1Xv0jNkbaAVosx1SOOOfmZSEO0VhBtRy6/view?usp=sharing)


<br>

---


# 2021.3.26

- Drone: 21.3.2
- **Drone(4m): 21.3.3**
> - 클럭 설정 수정
- **Controller: 21.3.1**
> - 버저 주파수 오류 수정



[Download](https://drive.google.com/file/d/1XqAkc3gxe6HrqKQh8uQREdvZm23YRYbl/view?usp=sharing)


<br>

---


# 2021.3.22

- **Drone: 21.3.2**
> - 페어링 대기 모드에서 본체 RGB LED를 노란색으로 깜빡이게 함
> - 바닥 센서 응답이 없을 경우 빨간색, 바닥 이미지가 인식이 안되는 경우 노란색으로 짧게 켜졌다가 길게 꺼지는 동작을 반복하게 함
- **Drone(4m): 21.3.2**
> - 페어링 대기 모드에서 본체 RGB LED를 노란색으로 깜빡이게 함
> - 바닥 센서 응답이 없을 경우 빨간색, 바닥 이미지가 인식이 안되는 경우 노란색으로 짧게 켜졌다가 길게 꺼지는 동작을 반복하게 함
- Controller: 21.2.1


[Download](https://drive.google.com/file/d/1E4qLXTYTwGTx3JovVU_SnttY32gyEr7z/view?usp=sharing)


<br>

---


# 2021.2.9

- **Drone: 21.2.1**
> - RF 수신율 개선
> - FHSS 성능 개선
- **Drone(4m): 21.2.1**
> - RF 수신율 개선
> - FHSS 성능 개선
- **Controller: 21.2.1**
> - RF 수신율 개선
> - FHSS 성능 개선
> - RF 통신 상태 화면 배치 조정, 우측 하단에 응답률 그래프 추가


[Download](https://drive.google.com/file/d/1Qgec4M5pz7yFIb0LES2fhZg9dlXwF2Fe/view?usp=sharing)


<br>

---


# 2021.1.4

- **Drone: 20.12.2**
> - 버튼 입력중이거나 페어링 동작 중에는 알람 작동을 멈추게 함
> - LIGHT C 제어가 Body에 연동됨에 따라 관련 코드를 제거
- **Drone(4m): 21.1.1**
> - 버튼 입력중이거나 페어링 동작 중에는 알람 작동을 멈추게 함
> - LIGHT C 제어가 Body에 연동됨에 따라 관련 코드를 제거
> - 외부 RGB LED 핀 순서 변경
> - 거리 센서 라이브러리 업데이트
> - Range 센서와 관련된 제어부 수정
- **Controller: 20.12.2**
> - 거리 센서 그래프 표시할 때 2미터 센서를 사용하는 드론과 4미터 거리 센서를 사용하는 드론의 최대 표시 범위를 다르게 함
> - 거리 센서 값을 조종기 화면에 표시할 때 4m 센서에서 2.55m 범위를 넘어서는 경우 정상적으로 값을 표시하지 못하던 문제를 수정


[Download](https://drive.google.com/file/d/1_wL9nbSL6jYS2OZiopOePfgRiQ-DJb3H/view?usp=sharing)


<br>

---


# 2020.12.21

- Drone: 20.11.2
- **Controller: 20.12.1**

> - 조종기 LED 동작하지 않는 오류 수정
> - 조종기 설정 메뉴 중 LIGHT 설정이 동작하지 않는 오류 수정


[Download](https://drive.google.com/file/d/1r61wgTJP1pW8himwoWaae7jK7-9fHL_m/view?usp=sharing)


<br>

---


# 2020.11.9

- **Drone: 20.11.2**
- **Controller: 20.11.3**

> - 코딩 드론과 연결 시 fhss 설정 안되는 오류 수정


[Download](https://drive.google.com/file/d/1R9zJHUYHRD7rsI3CNPQsLllReDDWvhiN/view?usp=sharing)


<br>

---


# 2020.11.5

- **Drone: 20.11.1**
- **Controller: 20.11.2**

> - FHSS 성능 개선
> - E-Drone 4M 버전 비행 튜닝


[Download](https://drive.google.com/file/d/1qLk9_bzUfS7wz8TKu-smCD13x5vbdsjn/view?usp=sharing)


<br>

---


# 2020.10.23

- **Drone: 20.10.10**
- **Controller: 20.10.2**

> - RF 송수신 코드 수정
> - E-Drone 4M 버전에서 거리 센서 데이터를 600ms 이상 읽지 못하는 경우 장치 초기화. 장치 초기화는 드론이 대기 상태일 때만 작동


[Download](https://drive.google.com/file/d/19b1W4lwS7jh-OxddRczdcqWlHQZZVk6R/view?usp=sharing)


<br>

---


# 2020.10.22

- **Drone: 20.10.6**
- **Controller: 20.10.1**

> - RSSI 확인 코드 수정
> - Low Battery 경고 시 LED를 흰색으로 짧게 켜지고 길게 꺼지는 동작을 반복하게 함
> - 조종기에서 의도하지 않는 상황에서 FHSS 켜지는 문제 수정


[Download](https://drive.google.com/file/d/12D9urenw4go5l0IC5By95jxcxaa4JKd5/view?usp=sharing)


<br>

---


# 2020.9.18

- **Drone: 20.9.1**
- Controller: 20.8.4

> - 몸체 RGB LED 와 외부 RGB LED를 연동


[Download](https://drive.google.com/file/d/1Fc88sMx8qlwm8hrJbK-RKKyEmVN9g6JP/view?usp=sharing)


<br>

---


# 2020.8.27

- Drone: 20.7.2
- **Controller: 20.8.4**

> - 페어링 동작 시 페어링 이외의 데이터 전송 차단


[Download](https://drive.google.com/file/d/1MuDs2D2BXMRhCa9VdTC_WrRIm0YV2TVO/view?usp=sharing)


<br>

---


# 2020.7.8

- **Drone: 20.7.2**
- **Controller: 20.7.2**

> - 드론에 Low Battery 경고 LED 동작 추가
> - 데이터 전송 중인 동안 다른 데이터 전송을 차단
> - 조이스틱 캘리브레이션 수정
> - 조종기에서 드론 Low Battery 경고는 ErrorFlagsForState::LowBattery 플래그가 활성화 된 경우에만 동작하게 함(드론마다 Low Battery 기준이 다르기 때문)


[Download](https://drive.google.com/file/d/1LFs3qp4KSw8ibRO9fEW4D32BXdS5yNPI/view?usp=sharing)


<br>

---


# 2020.2.21

- Drone: 20.1.5
- **Controller: 20.2.3**

> - 조종기 Light 모드 설정 시 Body*의 시작을 **0x10**에서 **0x20**으로 변경함. 이유는 E-Drone 이후 장치들의 메인 LED를 **0x20**으로 고정하기로 했기 때문
> - [Light::Controller::Mode::Type](http://dev.byrobot.co.kr/documents/kr/products/e_drone/protocol/06_structs_light/#heading-lightcontrollermodetype)
> - 통신으로 조종기의 Light 설정 변경 시 상위 4비트의 값을 무시하고 무조건 Body 설정을 변경하게 함(0x10을 사용하는 기존 코드와의 호환 문제)


[Download](https://drive.google.com/open?id=1XGGLOtHK6IWEacHwPjnZZggVdvRKoAU1)


<br>

---


# 2020.1.16

- **Drone: 20.1.5**
- **Controller: 20.1.4**

> - E-Drone의 펌웨어 버전도 Year.Month.BuildNumber 형식으로 변경
> - LED 색 변경 순서를 [빨강 -> 노랑 -> 녹색 -> 하늘 -> 파랑 -> 자홍 -> 흰색 -> 무지개색] 순서로 변경
> - 위에서 변경한 LED 색 변경 순서는 다른 프로젝트에서도 통일할 예정
> - [StateController](http://dev.byrobot.co.kr/documents/kr/products/e_drone/protocol/05_structs/#heading-protocolstatecontroller) 추가
> - 조종기에 CommandType::Link 명령에 대한 처리 추가
> - "Drone4AutoSetup.exe" 프로그램 추가
>   - 한 대 또는 여러 대의 장치 설정을 일괄적으로 변경할 때 사용
>   - 대상 장치와 명령을 선택 후 USB에 장치를 연결하면 자동으로 해당 장치에 연결하여 명령 전달
> - Count 화면에 누적 비행 시간 실시간 반영


[Download](https://drive.google.com/open?id=1r9yixqL4fQOcHhPcaMo82XLKRxsG-ycU)


<br>

---


# 2019.11.12

- **Drone: 1.1.24**
- **Controller: 1.1.25**

> - 리턴 홈에서 착륙 기능 제거
> - 조종 화면에서 Version 화면도 ON/OFF 선택 가능하게 함
> - 조종 화면에 Count 화면 추가
> - 조종 화면에 Card 화면 추가(카드 코딩이 가능한 코딩 드론용)
> - 색상 변화 타입을 21가지에서 7가지로 변경
> - 생명게임 동작 모드 제거
> - 축구 드론 조종 시 착륙 상태에서만 색상 변경하게 함
> - 비행 제어에 Manual 모드 선택 기능 추가(축구드론 용)


[Download](https://drive.google.com/open?id=1yap7IGBC3BWZFCwXfZolURP5CUHIZS2w)


<br>

---


# 2019.4.26

- **Drone: 1.1.17**
- **Controller: 1.1.16**

> - 조종기에 드론 외부 LED 설정 모드 추가
> - 조종기와 드론 모두 LED 설정 모드에서 선택할 수 있는 동작 모드에 Rainbow, Rainbow2를 추가함
> - 이륙전 모터가 천천히 돌 때 모터의 불량을 판별하여 모터를 정지시키고 조종기에 경고 메세지 출력
> - 외부 RGB LED 설정을 내부 플래시 메모리에 저장하게 함


[Download](https://drive.google.com/open?id=1V_ls69gItraiXnH2Aeun7qFl7Qzcj2yd)


<br>

---


# 2019.2.27

- Drone: 1.1.14
- **Controller: 1.1.14**

> - 조종기 사용 편의성 개선 작업
> - 조종 모드에서 속도 설정 변경 시 설정이 적용될 때까지 반복 전송(FHSS 모드에서 속도 변경이 무시되는 경우가 없어짐)
> - 조종 모드에서 속도 설정 변경 시 Speed 1, 2, 3에 따라 각각 다른 소리가 나게 함
> - 조종 모드에서 LED 색상 변경 시 5회 반복 전송(FHSS 모드에서 LED 색 변경이 무시되는 경우가 줄어듦)
> - 트림 변경 시 중앙 위치와 좌우 끝 위치일 때를 구분할 수 있도록 다른 소리가 나게 함
> - 전원을 켤 때 "도미솔", 전원 끌 때 "솔미도" 소리가 나게 함


[Download](https://drive.google.com/open?id=18Q3nRRqmCTlZG8WtzxMGhNUfHtcfiRaE)


<br>

---


# 2019.2.25

- **Drone: 1.1.14**
- **Controller: 1.1.13**

> - [Protocol::Count](http://dev.byrobot.co.kr/documents/kr/products/e_drone/protocol/05_structs/#heading-protocolcount) 구조체의 timeFlight(u64, ms) 변수를 timeSystem(u32, sec), timeFlight(u32, sec) 로 변경함
> - 조종기에 Protocol::Count 데이터를 요청하는 경우, timeSystem 변수에 현재까지의 동작시간을 초 단위로 반환. 나머지 값들은 0.


[Download](https://drive.google.com/open?id=15F2jmq6gBaBC-JHWj30VC6_8ysGWVZsR)


<br>

---


# 2019.2.20

- **Drone: 1.1.13**
- Controller: 1.1.12

> - 작은 상승 스로틀 값에 하강하는 현상 수정
> - 배터리 레벨 수정


[Download](https://drive.google.com/open?id=1dxxks9QnZLSWKYimyIlwqNZngWcGBUPg)


<br>

---


# 2019.2.13

- Drone: 1.1.12
- **Controller: 1.1.12**

> - 조종기 LINK 모드의 USB 데이터 송수신 상태 표시 수정


[Download](https://drive.google.com/open?id=1CH5I231H2Vx36VajtI9xc9COILmKfcnh)


<br>

---


# 2019.2.12

- **Drone: 1.1.12**
- **Controller: 1.1.11**

> - 배터리 레벨 수정
> - [Protocol::InformationAssembledForByBlocks](/documents/kr/products/e_drone/protocol/05_structs/#heading-protocolinformationassembledforbyblocks) 추가
> - USB 장치를 조종기에 연결 시 FHSS를 끔
> - 동작 중 LCD 초기화 시 백라이트를 끄는 버그 수정


[Download](https://drive.google.com/open?id=1Nn86H8nojuHVXttusGU6h6RqxQE8suqT)


<br>

---


# 2019.1.31

- **Drone: 1.1.10**
- Controller: 1.1.10

> - 호버링 안정화
> - 속도 조절
> - 드론 컴파일 최적화 옵션 OFF


[Download](https://drive.google.com/open?id=1NknvySgNCq4HtWd7OKkjGEuEfOiakFuG)


<br>

---


# 2019.1.30

- **Drone: 1.1.9**
- **Controller: 1.1.10**

> - RF 데이터 송수신 설정 및 CRC 확인 부분을 수정하여 이전 버전의 드론, 조종기와 혼용 불가
> - 페어링 방법 변경(드론이 새로운 페어링 주소를 송출)
> - 페어링을 하는 동안 RF 출력을 낮춤(멀리 떨어진 다른 장치와의 연결 확률이 낮아짐)
> - 펌웨어 자동 업데이트 프로그램을 **Drone4AutoUpdater**에서 **Drone4AutoUpdaterLight**로 변경
> - 'Control::Quad8'과 'Control::Position'을 혼용해서 사용할 경우 조작이 의도대로 되지 않는 문제 수정
> - 블록 코딩 시 Position 위치 값을 0으로 설정하면 드론 정지
> - FHSS 선택 추가('ON -> OFF'는 조종기에서 설정 변경 후 전원을 껐다가 켜야 함)
> - 비행 중 이륙 명령 시 정지되는 문제 수정
> - 장치 주소 표시 방법 변경
> - 와치독 사용
> - 속도 조절 설정을 드론에 저장
> - 고도 안정화
> - [Protocol::State](/documents/kr/products/e_drone/protocol/05_structs/#heading-protocolstate) 구조체 수정(controlSpeed 추가)


[Download](https://drive.google.com/open?id=1ggsL65s91iuSwE8XrM8op1gLdOFy8Xvt)


<br>

---


# 2018.12.12

- **Drone: 1.0.6**
- **Controller: 1.0.7**

> - 리턴 홈 안정화
> - 회전 안정화
> - 제품 생산 관련 문제로 12월 11일 버전에서 변경했던 RF 데이터 송수신부 처리 방법과 페어링 변경 사항을 이전 상태로 되돌림(추후 다시 적용할 예정)
> - DeviceType::Tester, DeviceType::Monitor 장치가 조종기와 USB로 연결된 경우 전원 버튼으로 [Link] <-> [조종] 모드 전환을 못하게 막음


[Download](https://drive.google.com/open?id=1bfUo0DlxnkkrpQMV0S6yIWEDJCGH4_yL)


<br>

---


# 2018.12.11

- **Drone: 1.0.5**
- **Controller: 1.0.6**

> - 무게 150g에서 호버링 안정화
> - 리턴 홈 기능 안정화
> - RF 통신 데이터 송수신부분 수정(업데이트 이후에는 이전 조종기 또는 드론과 통신이 안됨)
> - 드론과 조종기 페어링 시 드론이 새로운 주소를 생성하게 함(여러 드론이 하나의 조종기와 페어링되는 현상을 막기 위함)
> - USB에 PC가 연결된 상태일 때 전원 버튼으로 조종 <-> 링크 모드 전환 가능하게 함


[Download](https://drive.google.com/open?id=1SO7FqX1txobr0dopoVJavsJf6rgjI5sB)


<br>

---


# 2018.12.4

- **Drone: 1.0.4**
- **Controller: 1.0.5**

> - Reverse 경고 활성화(이륙 실패 시에만 표시)
> - 바이블럭에서 10% 조종기값 적용 안되는 현상 수정
> - 이륙 속도를 0.7m/s로 변경
> - 모드 1, 3, 4에서 수동 이륙 가능하게 함


[Download](https://drive.google.com/open?id=1-TvDtzoEYvBLOGVrtsiwF4hcQWuIZz2g)


<br>

---


# 2018.11.29

- **Drone: 1.0.3**
- **Controller: 1.0.4**

> - 고도 안정화
> - 호버링 안정화
> - RF 동일 채널을 사용하는 조종기가 있을 때의 조종 안정성 향상
> - 조종 화면 중 조이스틱 화면에 실제 드론에 전달하는 조종 값을 표시(모드에 따라 R, P, Y, T의 위치가 바뀜)
> - 조종 화면 중 RF 화면 중앙 그래프 내부의 폰트를 10x16으로 변경
> - 조종 화면 중 RF 화면 우측 하단에 응답 수신률의 평균 값을 표시


[Download](https://drive.google.com/open?id=1z55A8It5IpabF8iPVIUSqAdGvA86qIE-)


<br>

---


# 2018.11.28

- Drone: 1.0.2
- **Controller: 1.0.3**

> - 이착륙 버튼을 사용 중 낮은 확률로 조종이 중단되는 문제 수정
> - 이착륙 버튼 아래의 버튼을 눌렀을 때 Link 모드로 전환되는 문제 수정
> - LINK 모드에서도 주기적으로 드론의 데이터 요청(배터리 잔량 업데이트 등에 사용)
> - LINK 모드에서 처음 PC에서 데이터를 받기 전까지 조이스틱과 버튼을 조작할 수 없었던 문제 수정
> - LINK 모드일 때 특정 장치로부터 데이터를 받은 후 부터 조이스틱과 버튼 입력을 PC에 전송하게 함(Tester, Monitor, Scratch, Entry, ByScratch)
> - LINK 모드에서 전원 버튼을 짧게 눌렀다가 떼면 조종 모드로 전환(드론에 문제가 생긴 경우 사용, 다시 LINK 모드로 전환하려면 USB를 분리했다 다시 연결해야 함)


[Download](https://drive.google.com/open?id=16KZXNAf9SRyKWoXe7c6Uim_2tzBm428e)


<br>

---


# 2018.11.27

- **Drone: 1.0.2**
- **Controller: 1.0.2**

> - RF 연결과 관련된 Light 이벤트 수정
> - 고도 튀는 현상 수정


[Download](https://drive.google.com/open?id=1N6DntJUG3G6K3NXd8F02Uiu7ub6ykaWv)


<br>

---


# 2018.11.26

- **Drone: 1.0.1**
- **Controller: 1.0.1**

> - 고도, 회번, 자세, 플립 비행 안정화
> - 드론 비행 시간을 시:분:초 로 표시하게 함. 이전에는 ms로 표시
> - 배터리가 30% 미만이거나 기체가 무거울 때 플립을 할 수 없음
> - 충돌 시 모터가 정지하지 않는 문제 수정
> - 백라이트 ON/OFF 설정을 플래시 메모리에 저장
> - 드론과 조종기의 모든 LED 동작 모드에 Sunrise, Sunset 추가
> - 조종기 설정 화면 Light 메뉴에 SUNRISE, SUNSET 모드를 추가
> - 조종기 전면 좌측 위의 버튼을 짧게 누르면 속도 변경
> - 조종기 전면 우측 위의 버튼을 짧게 누르면 LED 기본 색상 변경(R, G, B, C, M, Y, W 순서로 바뀜)
> - 데이터 저장 블럭의 크기를 512바이트에서 256바이트로 줄임
> - RF 데이터 송수신 구조 수정
> - 조종기에서 페어링 시 페어링에 필요한 데이터 이외에는 전송 차단
> - 동작 중 RF 칩이 리셋되면 RF 칩 초기화
> - **Control::Position** 내부 변수 중 **heading**과 **rotationalVelocity**의 변수형을 **float**에서 **int16_t**로 변경
> - InformationAssembledForController의 angleRoll, anglePitch 크기를 1바이트에서 2바이트로 변경


[Download](https://drive.google.com/open?id=13q17lFeyqPS8W_RzjMmsjY2iCOL7-Vmb)


<br>

---


# 2018.11.2

- **Drone: 1.0.0**
- **Controller: 1.0.0**

> - 정식 제품 출시


<br>

---


# 2018.10.31 - 2

- **Drone: 0.2.19**
- Controller: 0.2.15

> - 바이스크래치 블럭 코딩에서 오른쪽으로 회전하지 않는 현상 수정


[Download](https://drive.google.com/open?id=12laWDx2UjLTwVd3jOeRJuYEWvmkY6vx6)


<br>

---


# 2018.10.31

- **Drone: 0.2.18**
- Controller: 0.2.15

> - 드론에서 외부 Range 센서 모듈의 데이터를 수집
> - 드론에 'DataType::Range'를 요청 시 외부 Range 센서의 데이터를 통합하여 전달(센서가 연결되지 않은 경우 -1, 연결되었으나 감지할 수 있는 거리를 벗어난 경우 8000이 넘는 값을 출력함. 값의 단위는 mm)
> - 호버링 안정화


[Download](https://drive.google.com/open?id=1pcdTc3TwpIynK6D0kJO_ugnlO5ZFFSTj)


<br>

---


# 2018.10.26

- **Drone: 0.2.17**
- **Controller: 0.2.15**

> - Control::Position16에서 x, y, z에 대한 각각의 속도를 하나의 속도 값으로 사용하도록 변경함
> - yaw 회전 방향 수정(+값 입력 시 반시계 방향으로 회전)
> - RF 송수신 중단 시 주기적으로 Ping 전송
> - 고도, 속도 안정화
> - 리턴 홈 안정화
> - CommandType에 조종기 백라이트 제어 추가
> - Range 센서 데이터 구조체 추가
> - 조종기를 USB에 연결하여 전원이 켜지는 경우 로고를 표시하지 않게 함


[Download](https://drive.google.com/open?id=1sBZC7AsoRa8H6IQDhcsT9CMiU8919anL)


<br>

---


# 2018.10.16

- **Drone: 0.2.16**
- Controller: 0.2.14

> - 비행 제어 설정이 Position 모드일 때에만 바닥 이미지 경고 활성화
> - 비행 제어 설정이 Attitude 모드일 때에만 트림 값 적용
> - Flow 센서 설정 변경

[Download](https://drive.google.com/open?id=1EOwzym4Ncf7neTeluddCu6258EufrfwV)


<br>

---


# 2018.10.15

- **Drone: 0.2.15**
- **Controller: 0.2.14**

> - Flow 센서 설정 변경
> - 회전 명령 시에 계속 도는 문제 수정
> - Attitude Mode 일 때 최대 각도 40에서 35도로 줄임
> - Trim 설정값을 무시하게 함(Trim 적용 방법 변경 예정)

[Download](https://drive.google.com/open?id=1frTwqh9EYkJAiVj9LugHLo02DE3VCvBl)


<br>

---


# 2018.10.12

- **Drone: 0.2.14**
- **Controller: 0.2.13**

> - Flow 센서와 관련된 설정 변경
> - Attitude 모드에서만 조이스틱 Yaw 조작 시 속도 변경 적용, Position 모드에서는 속도 변경과 상관없이 고정(180deg/s)
> - 조종기 설정 메뉴에서 Weight 설정 제거
> - 드론이 연결되지 않은 경우 Version, Address, CRC 표시창에서 조종기의 정보만 표시

[Download](https://drive.google.com/open?id=1xe-Qdtrq0MugPBwr8ihBoZrAaZ2QJXB3)


<br>

---


# 2018.10.11

- **Drone: 0.2.13**
- **Controller: 0.2.12**

> - 드론이 비행중일 때 Control, Mode, Headless, Function 메뉴에 진입할 수 없게 막음
> - 프로펠러 진동 경고
> - 스피드 설정 변경 시 회전 속도도 변함
> - 고도 유지 안정화
> - 호버링 안정화
> - 이륙 안정화
> - Information에 RF 항목 추가

[Download](https://drive.google.com/open?id=1Ns7FeEJifz3UG3OXGHZ--GhBcn3YCoZ_)


<br>

---


# 2018.10.8

- **Drone: 0.2.12**
- **Controller: 0.2.11**

> - 드론 고도 제어 안정화
> - X, Y 위치 안정화
> - Weight 설정 변경 없이 작동할 수 있도록 제어 변경(현재는 Weight 설정을 무시)
> - 에러 플래그 이름 수정
> - 프로펠러, 모터 문제로 이륙이 안되는 경우 오류 메세지 출력
> - 모든 UART, USB 시리얼 통신의 Baudrate를 57600으로 변경
> - 배터리 경고 이외에 무선 연결 끊어짐, 프로펠러-모터 문제로 이륙 불가, 바닥 이미지 인식 불가, Motion 센서 캘리브레이션 진동 알림 추가

[Download](https://drive.google.com/open?id=1Jefp48LHR00dRrWSEIMVFJNOrADs0K59)


<br>

---


# 2018.10.5

- **Drone: 0.2.11**
- **Controller: 0.2.10**

> - 드론 고도 제어 안정화
> - 바닥 이미지를 인식할 수 없을 때의 제어 처리 및 조종기에 상태 알림 추가
> - 드론, 조종기 앱 동작 시 UART의 Baudrate를 57600으로 변경함. 부트로더에서는 아직 115200 사용 중
> - 드론 UART 통신 안정화
> - 비행 중 컨트롤 모드 변경 불가능하게 막음
> - 드론, 조종기의 RF 주소가 0, 0, 0인 경우 RF 데이터 송수신을 차단

[Download](https://drive.google.com/open?id=1n3gUKYbTCdR6DowdWxySC_OZWJIB4xDl)


<br>

---


# 2018.10.2

- **Drone: 0.2.10**
- **Controller: 0.2.9**

> - 드론 부팅 시 각 센서를 초기화 할 때 정상적으로 연결되지 않는 경우 관련 ERROR 플래그를 활성화하게 함
> - 조종기의 드론 오류와 관련된 메세지 출력 부분 수정
> - 조종기에서 "SET DEFAULT" 선택 시 weight, trim이 초기화되지 않는 문제 수정
> - 조종기 Function 메뉴에서도 드론의 상태 데이터 요청("SET DEFAULT"를 실행했을때 상단 상태 표시줄의 값이 바뀌지 않는 문제가 있었음)
> - 조종기 Information 메뉴의 Altitude, Position 값 소수점 표시 위치를 일치시킴
> - 화면 상단 상태 표시줄의 텍스트 간격을 3에서 4로 변경

[Download](https://drive.google.com/open?id=1Z4ObTvkYi-pkSR1zpvyTJyI3o3vmYYLW)


<br>

---


# 2018.10.1

- **Drone: 0.2.9**
- **Controller: 0.2.8**

> - 드론, 조종기 기본 색을 Green으로 변경
> - 드론을 UART 또는 USB로 연결해서 이륙했을 때 바로 멈추는 문제 수정
> - 고도 제어 안정화
> - 비행 안정화

[Download](https://drive.google.com/open?id=12P5_t1x8C8ePndzkB1kkVVcQQmiAVgC_)


<br>

---


# 2018.9.28

- **Drone: 0.2.8**
- **Controller: 0.2.7**

> - 드론, 조종기 기본 색을 White로 변경
> - DataType에 LostConnection을 추가. 마지막으로 조종 명령을 전송한 장치와의 연결이 끊어진 후, 여기에서 설정한 시간이 지나면 설정된 동작(조종 중립, 착륙, 강제 정지)을 실행. 시간 값을 0으로 설정할 경우 해당 동작은 실행하지 않음. 현재는 수정한 값을 플래시에 저장하지 않음. 그래서 매번 드론을 새로 부팅할 때마다 지정해야 함. 기본 연결 장치는 RF.
> - 조종기 USB를 제거하면 RF와 LCD를 리셋(화면 반전 및 RF 연결 끊어짐 문제 해결)
> - Trim  화면에 Height(Range 센서의 값) 대신 Z(고도)를 표시
> - 비행 안정화

[Download](https://drive.google.com/open?id=13YRVPrqF1b_TGNp4kB4Uzw2rtD0BU82r)


<br>

---


# 2018.9.21 - 3

- **Drone: 0.2.7**
- Controller: 0.2.6

> - RF를 통해 드론 제어 중 RF 연결이 끊기면 10초 후 착륙 시작, 2분 후 강제 정지
> - 착륙 시 조종 중립, 목표 위치 초기화

[Download](https://drive.google.com/open?id=1hcrZP4-3Cyx9UXgjHJz2oz_ofnEIXitH)


<br>

---


# 2018.9.21 - 2

- Drone: 0.2.6
- **Controller: 0.2.6**

> - 페어링 성공/실패 시 조종기 Buzzer 소리 알림 활성화


<br>

---


# 2018.9.21

- **Drone: 0.2.6**
- **Controller: 0.2.5**

> - 드론 이륙을 전면 왼쪽 상단 버튼을 길게 눌러서 하는 것으로 변경. 조이스틱 Throttle 조작으로 이륙하는 것은 막음
> - 조종기 배터리가 5% 이하로 남았을 때에만 경고 창이 나타나고 진동이 발생하도록 수정
> - 트림 최대값 변경
> - 배터리 잔량 계산부 수정
> - 배터리 진동 경고 활성화
> - 전원 버튼을 짧게 누르면 LCD를 초기화 하게 함(화면이 위아래로 뒤집히는 경우 사용)
> - 기본 화면에 트림 화면을 추가
> - 드론과 조종기의 설정을 기본 값으로 바꾸는 명령을 추가(CommandType::SetDefault)
> - 조종기 설정 메뉴 중 'FUNCTION'에 'SET DEFAULT'를 추가. 실행 시 연결된 드론이 있는 경우 드론의 설정값까지 같이 초기화 됨(트림, 조종 화면 설정, LED 기본 색상, 무게 설정, 속도, 헤드리스, 모드 등)
> - 위치 기반 이동 명령 성능 개선
> - 드론이 뒤집히면 정지


<br>

---


# 2018.9.18 - 2

- **Drone: 0.2.4**
- **Controller: 0.2.4**

> - 화면 상단의 상태 표시줄에 Control과 Headless 정보를 한 문자로 표시하게 함
> - 조종 입력값 범위를 30, 70, 100%로 변경
> - RSSI 안테나 표시 기준 변경
> - 야외 비행 시 고도 제어 안정화

<br>

---


# 2018.9.18

- **Drone: 0.2.3**
- **Controller: 0.2.3**

> - 조종 모드에서 조종기 전원 버튼을 짧게 누르면 LCD를 리셋함.(화면이 반전된 경우에 사용)
> - 센서의 RAW 데이터를 읽는데 사용하는 RawFlow, RawMotion 구조체를 추가
> - 조종기 부트로더 진입 시 진동 발생하는 문제 수정
> - Motion 구조체로 전달하는 Accel과 Gyro값을 지정한 단위에 맞추어 계산한 값으로 변경
> - Control::Position16, Control::Position 명령 추가함(위치와 속도로 이동 명령을 내릴 때 사용)
> - 비행 안정화

<br>

---


# 2018.9.14

- **Drone: 0.2.2**
- **Controller: 0.2.2**

> - LED 초기 설정 저장 버그 수정
> - RF 이외의 장치로 조종 명령을 받았을 때, RF 연결 중단에 의해 드론이 멈추는 현상이 발생하지 않게 함(아두이노 등의 장치로 드론에 직접 연결해서 제어하는 경우 RF가 끊어진 상태이기 때문에 강제 착륙 명령이 들어가서 이륙을 할 수 없는 문제가 있었음)
> - RF 이외의 장치로 조종 명령을 받았을 때, RF 연결 이벤트 발생 시 후면 LED를 제어하지 않게 함(아두이노 등의 장치로 드론에 직접 연결해서 제어하는 경우 해당 장치가 후면 LED를 제어할 수 있게 하고, RF 연결 이벤트에 의해 LED 설정이 바뀌지 않게 함)
> - 조종 화면 설정 내용을 플래시 메모리에 저장하여 조종기를 다시 부팅했을 때 이전 설정이 유지되도록 함

<br>

---


# 2018.9.10

- **Drone: 0.2.1**
- **Controller: 0.2.1**

> - 장치 등록 절차 변경
> - 여러 형태로 나누어져 있던 LED 설정 변경을 LightMode, LightEvent, LightDefault로 통합
> - Protocol의 DataType의 순서를 다시 정리(기존의 펌웨어 업데이트, 모니터 등의 프로그램을 사용할 수 없음)
> - 조종기, 드론의 기본색 설정 변경 가능

<br>

---


# 2018.7.10

- Drone: 0.1.2
- **Controller: 0.1.3**

> - 조종기 화면 전환 부분 구조 개선 및 버튼을 짧게 눌렀을 때 전환 화면이 계속 남아있는 문제 수정
> - 조종기 좌상단 버튼을 길게 눌러서 백라이트 ON/OFF 할 때 화면에 표시하게 함

<br>

---


# 2018.7.9

- **Drone: 0.1.2**
- **Controller: 0.1.2**

> - PC에서 드론에 데이터 요청 시 응답으로 돌아오는 데이터의 CRC 값이 0으로 초기화 되어 있는 문제 수정

<br>

---


# 2018.7.5

- **Drone: 0.1.1**
- **Controller: 0.1.1**

> - 펌웨어 릴리즈

<br>
