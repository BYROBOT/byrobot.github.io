**[CODING DRONE](/documents/kr/products/coding_drone/) update log**

Modified : 2022.7.6

---

- Kramdown table of contents
  {:toc .toc}

<br>

# 2022.7.22

- **Drone: 22.7.2**

> - 바닥 버튼 4번 눌러 호버링 테스트 기능 추가.

- **Controller: 22.7.2**

> - 조종모드 3 / 4 오류 수정.

[Download](https://drive.byrobot.co.kr/d/s/pbCElfe4xVQpkTkwdkIZmhnSO8XD0Ihl/2VSCR4R3YmVF3Al_4dv7rr8GbOM6R966-fb5gGQCesQk)

<br>

---

<br>

# 2022.7.6

- **Drone: 22.7.1**

> - 드론의 안정/비안정 상태 관계없이 카드 읽기 동작으로 변경

[Download](https://drive.byrobot.co.kr/d/s/pO3R0R37cegS0IBLWKhtyiJpO7ZTCdFZ/l_thhyElfe8Ccb5MjM2Ax6-kLi1J_Ch3-XLwg5D5spwk)

<br>

---

<br>

# 2022.1.4

- **Drone: 22.1.2**

> - 드론에 USB 연결된 상태일 때 '시동', '이륙' 차단
> - 시동, 이륙 시 자세 조건 변경하여 지나치게 기울어지거나 뒤집힌 상태에서 '시동', '이륙' 동작을 차단.(roll, pitch 모두 -20 ~ 20 사이이고, accel.z 값이 70 이상일 때 이륙 가능)
> - 드론이 안정된 상태일 때 카드 읽기 동작, 비안정 상태로 바뀐 뒤 3초가 지나면 거리 센서 동작, 버튼을 누르는 경우 카드 읽기 동작 3초 연장
> - 조종기 이외의 장치에서 LED 제어 명령을 전송하면 LED 외부 제어 모드로 변경되고, 조종기에서 전송하는 LED 제어 명령과 내부에서 발생하는 LED 제어 명령을 무시함. 재시작 시 원래 상태로 복귀(파이썬, 엔트리 등에서 LED 조작 명령을 내렸을 때 내부 LED 제어 명령 때문에 원하는 동작이 되지 않는 경우를 막기 위해 수정함)

<br>

---

# 2021.12.13

- **Drone: 21.12.1**

> - 코딩 드론의 'CONTROL' 항목에서 'MANUAL' 선택 시 'ATTITUDE'가 선택되게 함(코딩 드론에는 MANUAL 모드가 없음)

[Download](https://drive.google.com/file/d/1ttvauYvkOiejqBgYqvTuqxlFHvEpU3XI/view?usp=sharing)

<br>

---

# 2021.12.9

- Drone: 21.8.2

> - E-DRONE 조종기 통신 문제 수정

[Download](https://drive.google.com/file/d/19P9mzzhSsGklYN4qO06KTCx7J9rY9d4B/view?usp=sharing)

<br>

---

# 2021.8.24

- **Drone: 21.8.2**

> - 드론 재부팅 문제 수정

[Download](https://drive.google.com/file/d/1l_zuPRWYpwJX83lwizzxs05m7hsXHcGe/view?usp=sharing)

<br>

---

# 2021.7.20

- **Drone: 21.7.2**

> - 배터리 레벨 조정

[Download](https://drive.google.com/file/d/1Xv0jNkbaAVosx1SOOOfmZSEO0VhBtRy6/view?usp=sharing)

<br>

---

# 2021.6.24

- **Drone: 21.6.4**

> - 정면 거리 센서와 바닥 거리 센서 오류를 분리함

[Download](https://drive.google.com/file/d/1XqAkc3gxe6HrqKQh8uQREdvZm23YRYbl/view?usp=sharing)

<br>

---

# 2021.3.26

- **Drone: 21.3.1**

> - 버저 주파수 오류 수정

[Download](https://drive.google.com/file/d/1XqAkc3gxe6HrqKQh8uQREdvZm23YRYbl/view?usp=sharing)

<br>

---

# 2021.2.19

- **Drone: 21.2.2**

> - 모드 버튼으로 모드 변경 시 모드 변경음이 나오게 함

[Download](https://drive.google.com/file/d/1TFGJloAjPyw0Nd05oAOSHgJjuw_4wiQS/view?usp=sharing)

<br>

---

# 2021.2.9

- **Drone: 21.2.1**

> - RF 수신율 개선
> - FHSS 성능 개선
> - 카드 코딩, 모션 코딩 시작 시 비행 제어 포지션, 헤드리스 노멀 모드로 전환

[Download](https://drive.google.com/file/d/1Qgec4M5pz7yFIb0LES2fhZg9dlXwF2Fe/view?usp=sharing)

<br>

---

# 2021.1.22

- **Drone: 21.1.10**

> - 자세, 착륙, 회전 안정화
> - 기본 회전 속도 변경

[Download](https://drive.google.com/file/d/1CoWv12wrqrryNECuEPV4OMiHbt6RZhFa/view?usp=sharing)

<br>

---

# 2021.1.14

- **Drone: 21.1.2**

> - 캘리브레이션 시 에러가 30%가 넘으면(Hue 범위 벗어남) 캘리브레이션을 중단하고 경고음으로 알림(카드에 문제가 없는 경우 대체로 LED 밝기와 관련한 문제로 오류가 발생함)

[Download](https://drive.google.com/file/d/1K_4VxCIx_D6ehzc1O_rloqTwmVKKFqkY/view?usp=sharing)

<br>

---

# 2020.11.9

- **Drone: 20.11.3**

> - FHSS 설정 안되는 오류 수정
> - 상승할 때 높이 차가 생기면(고도에 장애물이 생기면) 급격히 상승하는 문제 수정

[Download](https://drive.google.com/file/d/1xLSc3XtjJAsG4d5MzjAX_L6QjH-TD1JB/view?usp=sharing)

<br>

---

# 2020.11.6

- **Drone: 20.11.1**

> - FHSS 성능 개선
> - 이륙 후 고도가 1미터 이상 상승하는 문제 수정
> - 상승 시 위아래로 떨리는 문제 수정
> - 특정 드론에서 상승하는 문제 수정

[Download](https://drive.google.com/file/d/1qLk9_bzUfS7wz8TKu-smCD13x5vbdsjn/view?usp=sharing)

<br>

---

# 2020.10.13

- **Drone: 20.10.3**

> - 카드 코딩, 모션 코딩 시 코딩 끝 카드 실행이 끝나는 시점에 종료음이 나게 함
> - 바닥 거리 센서 데이터 오류 수정
> - 거리 센서 범위가 넘어가면 9.999미터를 출력하게 함
> - 속도 1 단계에서 수동 이륙 안되는 문제 수정

[Download](https://drive.google.com/file/d/1fycphLDtQTevxQAifxrRYTigD7XmoCem/view?usp=sharing)

<br>

---

# 2020.8.31

- **Drone: 20.8.17**

> - 페어링 대기 상태 표시 오류 수정

[Download](https://drive.google.com/file/d/1MuDs2D2BXMRhCa9VdTC_WrRIm0YV2TVO/view?usp=sharing)

<br>

---

# 2020.4.8

- **Drone: 20.4.1**

> - 제어주기를 4ms로 변경

<br>

---

# 2019.11.7

- **Drone: 19.11.1**

> - RF칩을 HW2000B로 변경

<br>
