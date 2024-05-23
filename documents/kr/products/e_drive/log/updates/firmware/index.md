**[GO CAR](/documents/kr/products/e_drive/) update log**

Modified : 2021.4.13

---

- Kramdown table of contents
  {:toc .toc}

<br>

# 2024.3.26

- **Go Car: 24.3.1**

> - 이동거리 설정 (5.5cm / 10cm / 13cm) 기능 추가 (애플리케이션 내에서 설정 - 기본 10cm)

[Download](https://alux1004-my.sharepoint.com/:u:/g/personal/skji_aluxonline_com/EY6mRpbqKPVNvQ8-xAoIg0gBfuYtM183y1L2GLJ6Qqkgjg?e=ri1EXP)

<br>

# 2022.7.6

- **Go Car: 22.7.1**

> - [카드코딩] 계속 전진 / 계속 후진 동작 안되는 오류 수정

[Download](https://drive.byrobot.co.kr/d/s/pO3OoEiH34gTSwGxsxkCcJ11UCcmtTMy/YPZtBREV0QYhOArgKVBpAqL5_5zOmWdS-zruANiJspwk)

<br>

---

<br>

# 2021.3.26

- **Go Car: 21.3.1**
- Go Car BleServer: 19.10.16

> - 버저 주파수 오류 수정

[Download](https://drive.google.com/file/d/1XqAkc3gxe6HrqKQh8uQREdvZm23YRYbl/view?usp=sharing)

<br>

---

# 2021.2.16

- **Go Car: 21.2.1**
- Go Car BleServer: 19.10.16

> - 라인 코딩 모드에서 컬러 캘리브레이션을 실행할 경우 라인 코딩용 컬러 캘리브레이션 데이터만 변경되었으나 이번 버전부터는 자동차의 현재 모드와 상관없이 항상 전체 컬러 캘리브레이션 데이터가 변경됨
> - 위의 변경으로 라인 코딩용 컬러 캘리브레이션만 변경하는 기능에 대한 접근 방법이 사라져서 대신 뒤집어서 버튼을 9번 누르는 것을 라인 컬러 캘리브레이션으로 변경함(원래 9회는 시스템 초기화였으나 11회로 변경)
> - 자동차를 뒤집은 상태에서 버튼을 눌러 동작하는 기능의 버튼 누름 횟수 변경
>   - 7번: 전체 컬러 캘리브레이션
>   - 9번: 라인 컬러 캘리브레이션
>   - 11번: 시스템 초기화

[Download](https://drive.google.com/file/d/10cLiTKseLVerNOcG3KxDSsDG2pNLQfd7/view?usp=sharing)

<br>

---

# 2021.1.22

- **Go Car: 21.1.7**
- Go Car BleServer: 19.10.16

> - 자동차의 앞 부분이 위를 향하도록 세운 상태에서 버튼을 누른 횟수에 따라 모드 변경
>   - 1번: 라인 코딩 모드
>   - 2번: 핸드팔로잉 모드
>   - 3번: 모션 코딩 모드
>   - 4번: 카드 코딩 모드
>   - 5번: 피아노 모드
> - 자동차를 세우거나 뒤집었을 때 '삐빅'하는 소리가 나게 함

[Download](https://drive.google.com/file/d/1CoWv12wrqrryNECuEPV4OMiHbt6RZhFa/view?usp=sharing)

<br>

---

# 2020.9.28

- **Go Car: 20.9.4**
- Go Car BleServer: 19.10.16

> - 버튼 입력 방법 변경(20.9.3 이전 상태로 복원)
>   - 자동차를 뒤집은 상태에서 5번 버튼을 누르면 모션 캘리브레이션
>   - 자동차를 뒤집은 상태에서 6번 버튼을 누르면 거리 센서 캘리브레이션
>   - 자동차를 뒤집은 상태에서 7번 버튼을 누르면 수동 컬러 캘리브레이션
>   - 자동차를 뒤집은 상태에서 9번 버튼을 누르면 초기화
> - 자동차를 뒤집으면 '삐빅'하는 소리가 나게 함

[Download](https://drive.google.com/file/d/19K9bd4jZ42m0EY82WhzmL6cpE_0p9Peo/view?usp=sharing)

<br>

---

# 2020.9.15

- **Go Car: 20.9.3**
- Go Car BleServer: 19.10.16

> - 버튼 입력 방법 변경
>   - 정상 상태에서 버튼을 1회 누르면 카드 읽기(길게 누르는 경우에도 카드 읽기로 처리)
>   - 정상 상태에서 버튼을 2회 이상 여러번 누르는 경우 모두 실행 동작으로 처리
>   - 자동차를 뒤집은 상태에서 3번 버튼을 누르면 수동 컬러 캘리브레이션
>   - 자동차를 뒤집은 상태에서 4번 버튼을 누르면 모션 캘리브레이션
>   - 자동차를 뒤집은 상태에서 5번 버튼을 누르면 거리 센서 캘리브레이션
>   - 자동차를 뒤집은 상태에서 6번 버튼을 누르면 초기화
> - 자동차 초기화 실행 후 원래 모드 색상으로 돌아가지 않는 버그 수정이
> - 초기화 시작음 변경
> - 모션 캘리브레이션 시작음 변경

[Download](https://drive.google.com/file/d/1FhMP3Oae6wE9PsWiUpd2cd46wresmdW6/view?usp=sharing)

<br>

---

# 2020.7.8

- **Go Car: 20.7.1**
- Go Car BleServer: 19.10.16

> - 데이터 전송 중인 동안 다른 데이터 전송을 차단
> - LED 제어 내부 구조 변경

[Download](https://drive.google.com/file/d/1MuDs2D2BXMRhCa9VdTC_WrRIm0YV2TVO/view?usp=sharing)

<br>

---

# 2020.5.13

- **Go Car: 20.5.1**
- Go Car BleServer: 19.10.16

> - 버튼을 3번 눌러 Black, White 색 캘리브레이션을 하던 기능을 제거
> - 라인 코딩에서 U턴을 만나면 150도 이상 회전한 이후에 발견하는 선을 따라 이동하도록 수정
> - 버튼을 9회 눌러 초기화 할 때 설정값까지 초기화

[Download](https://drive.google.com/open?id=1XaHhTInP9TDSz6qSEkhxto6Monh8TJw7)

<br>

---

# 2020.3.31

- **Go Car: 20.3.19**
- Go Car BleServer: 19.10.16
- Go Car Tester: 19.9.1

> - 길을 잃어버렸을 때의 효과음 제거
> - 핸드팔로잉, 라인코딩 조향 제어 수정
> - 라인 코딩 규칙 변경
>   - 파란색(부스터), 하늘색(우회전) 마커 제거
>   - 노란색 마커를 만나면 바로 우회전 하도록 변경
>   - 녹색 마커를 만나면 바로 좌회전 하도록 변경
> - Hue 영역을 -60 ~ 60에서 -120 ~ 120으로 확장함(일부 색상이 다른 색 경계를 넘어서 나타나는 경우가 있어 수정)

[Download](https://drive.google.com/open?id=1tKKKJtc1dzD8Sd26GdTpwWeOhwG9ruIE)

<br>

---

# 2020.2.27

- **Go Car: 20.2.4**
- Go Car BleServer: 19.10.16
- Go Car Tester: 19.9.1

> - **펌웨어 업데이트 후 반드시 '컬러 캘리브레이션'을 하시기 바랍니다. 하지 않으면 카드를 정상적으로 읽지 못합니다**
>   - 기존에는 컬러 캘리브레이션 원본 데이터를 저장하고 읽은 다음 색 판별 시 Margin을 적용하여 색을 판별하였으나, 현재는 캘리브레이션 후 Margin을 적용한 값을 저장하고 읽어서 색 판별 시 바로 사용합니다.
>   - 위의 변경은 색 판별 기준값을 사용자가 변경할 수 있게 만드는 과정에서 수정이 필요했던 것으로 이 부분의 변경 때문에 컬러 캘리브레이션을 다시 하셔야합니다.
>   - 컬러캘리브레이션 시 saturation 최솟값은 20, 최댓값은 100, lightness의 최솟값은 20, 최댓값은 100으로 설정하였습니다.
> - Drone7Card 프로그램에서 RGB 색상 범위 및 색 분류 값의 설정 범위를 수정할 수 있습니다.
>   - 마우스를 범위 그래프 위로 가져가면 그래프 상단에 목표값 그래프가 겹쳐서 표시됩니다.
>   - 자동차가 연결된 경우 목푯값의 양 끝부분을 클릭한 상태로 드래그하면 변경한 값이 자동차에 전달됩니다.
>   - 그래프 최소, 최댓값 좌우의 빈 곳을 클릭하면 최대, 최솟값이 1씩 바뀝니다.
>   - 프로그램 크기가 고정되어있었던 것을 크기를 자유롭게 변경할 수 있도록 수정하였습니다.
> - Drone7Setup 프로그램에서 라인 코딩과 관련된 설정값을 변경하실 수 있습니다.
>   - 색상 마커 발견 시 해당 색으로 판별하는 기준값을 색상별로 다르게 설정할 수 있게 하였습니다.

[Download](https://drive.google.com/open?id=1sOJpW6DScZTGItZk_xZDwOluepM1duXh)

<br>

---

# 2020.2.14

- **Go Car: 20.2.2**
- Go Car BleServer: 19.10.16
- Go Car Tester: 19.9.1

> - 드론 설정 변경 프로그램 대응

[Download](https://drive.google.com/open?id=1I1n23MPRObF4FIt9mso1CB6zKdg3Ssd6)

<br>

---

# 2020.2.13

- **Go Car: 20.2.1**
- Go Car BleServer: 19.10.16
- Go Car Tester: 19.9.1

> - 라인코딩 동작 튜닝

[Download](https://drive.google.com/open?id=1YteEWNgSr8Sxl5UjFOINCoETIDBLRais)

<br>

---

# 2020.1.2

- **Go Car: 20.1.2**
- Go Car BleServer: 19.10.16
- Go Car Tester: 19.9.1

> - **펌웨어 업데이트 후 '데이터 초기화'를 하는 경우, 반드시 '컬러 캘리브레이션'을 하시기 바랍니다. 하지 않으면 카드를 정상적으로 읽지 못합니다**
> - 버튼 연속 입력 시 동작하는 특수 기능 수정
>   - 3번 : White/Black 캘리브레이션
>   - 4번 : 바닥 색에 따라 특수 기능 실행
>     - White/White : 자동 컬러 캘리브레이션(흰색 바탕에서 시작해야 하기 때문)
>     - White/Black : 자동 거리 센서 캘리브레이션
>     - Black/White : 모션 센서 캘리브레이션(자이로 바이어스 초기화)
>     - Black/Black : 수동 컬러 캘리브레이션
>   - 5번 : 모션 센서 캘리브레이션(자이로 바이어스 초기화)
>   - 6번 : 자동 거리 센서 캘리브레이션
>   - 7번 : 수동 컬러 캘리브레이션
>   - 8번 : 자동 컬러 캘리브레이션
>   - 9번 : 데이터 초기화
> - 거리 센서 캘리브레이션이 되지 않은 상태에서 핸드팔로잉을 시작하면 경고음 출력. 핸드팔로잉은 작동

[Download](https://drive.google.com/open?id=1mOKWhJ9oUCj1C14aO3CuIpph-YWxiJUR)

<br>

---

# 2019.12.31

- **Go Car: 19.12.53**
- Go Car BleServer: 19.10.16
- Go Car Tester: 19.9.1

> - 카드 색상을 읽는 시간을 변경
> - 거리 센서 캘리브레이션 변경
> - 수동 컬러 캘리브레이션 변경
>   - 시작, 종료음 변경
>   - 흰색, 검정, 빨강, 노랑, 초록, 하늘, 파랑, 자홍 순서로 진행
>   - 버튼을 눌러서 캘리브레이션을 진행. 완료되면 소리와 함께 다음 캘리브레이션 색을 표시
>   - 캘리브레이션이 정상적으로 완료되면 이전에 사용하던 모드로 돌아감
>   - 캘리브레이션 중 자동차를 기울여서 캘리브레이션을 중단하는 기능을 없앰
>   - 중간에 취소하려면 자동차를 껐다가 켜야 함
> - 초기화 기능 사용 시 카드 색상 구분값도 초기화 함
> - 버튼 연속 입력 시 동작하는 특수 기능 수정
>   - 3번 : White/Black 캘리브레이션
>   - 4번 : 바닥 색에 따라 특수 기능 실행
>     - White/White : 자동 컬러 캘리브레이션(흰색 바탕에서 시작해야하기 때문)
>     - White/Black : 자동 거리 센서 캘리브레이션
>     - Black/White : 리셋
>     - Black/Black : 수동 컬러 캘리브레이션
>   - 5번 : 자동 거리 센서 캘리브레이션
>   - 6번 : 수동 컬러 캘리브레이션
>   - 7번 : 자동 컬러 캘리브레이션
>   - 9번 : 데이터 초기화, 모션 센서 캘리브레이션

[Download](https://drive.google.com/open?id=1tWWAswZHqxXfCVIhcKw9Lg-mT5M2j-7l)

<br>

---

# 2019.12.24

- **Go Car: 19.12.41**
- Go Car BleServer: 19.10.16
- Go Car Tester: 19.9.1

> - 이전 버전에서 현재 버전으로 업데이트 시 사용자 데이터 전체 초기화 됨(컬러 센서, 거리 센서, 모션 센서 캘리브레이션 데이터, 카드 코딩 등 전체 초기화)
> - 자동 거리 센서 캘리브레이션 기능 추가
>   - White/Green 카드 사용 시 자동 거리 센서 캘리브레이션 모드로 전환(임시)
>   - 자동 거리 센서 캘리브레이션 모드로 전환 후 자동차 바로 앞에 흰색의 평평한 장애물을 두고 캘리브레이션을 시작
>   - 자동차가 뒤로 이동하면서 좌우 거리 센서의 값을 측정하여 자동으로 차이를 보정
> - 자동 컬러 캘리브레이션 기능 추가
>   - White/Cyan 카드 사용 시 자동 컬러 캘리브레이션 모드로 전환(임시)
>   - White, Black, Red, Yellow, Green, Cyan, Blue, Magenta 색상을 차례로 이동하며 색상 캘리브레이션
> - 버튼 연속 입력 시 동작하는 특수 기능
>   - 5번 : 모션 센서 캘리브레이션
>   - 6번 : 자동 거리 센서 캘리브레이션
>   - 7번 : 수동 컬러 캘리브레이션
>   - 8번 : 자동 컬러 캘리브레이션
>   - 9번 : 데이터 초기화

[Download](https://drive.google.com/open?id=1mdhYNh9hQLwdtGzKXDECp5IzYiqKXZ7p)

<br>

---

# 2019.12.18

- **Go Car: 19.12.36**
- Go Car BleServer: 19.10.16
- Go Car Tester: 19.9.1

> - 카드 코딩 용지와 라인 코딩 용지가 다른 경우 별도 컬러 캘리브레이션 지원
>   - 카드 코딩 상태에서 컬러 캘리브레이션 시 앞, 뒤, 앞(라인코딩) 캘리브레이션 값이 갱신됨
>   - 라인 코딩 상태에서 컬러 캘리브레이션 시 앞(라인코딩) 캘리브레이션 값이 갱신됨
>   - 현재 라인 코딩용 컬러 캘리브레이션 용지로 카드 모드에서 컬러 캘리브레이션을 하더라도 카드 색상을 정상적으로 판별할 수 있도록 각 영역을 확장한 상태. 그런데도 인식하지 못하는 경우도 발생할 수 있음
> - 컬러 캘리브레이션 방법 변경
>   - 컬러 캘리브레이션 시 White, Black, Red, Yellow, Green, Cyan, Blue, Magenta 순서로 진행.
>   - 컬러 캘리브레이션 시 각 색을 판별하는 시간을 줄임
> - 컬러 캘리브레이션 내부 처리 방법 변경
>   - 컬러 캘리브레이션 시 각 색의 Hue, Saturation, Lightness의 Min, Max 범위를 저장
>   - 위에서 저장한 영역에 일정값의 +- 여유값을 추가하여 해당 범위에 들어오는 경우 해당 색으로 판정
>   - 위의 색상 판정이 모두 끝난 후 밝기를 확인하여 흰색과 검정을 분리
>   - 위의 색상 판정과 흰색 검정 분리에도 속하지 못한 색들은 모두 Unknown으로 처리
> - 컬러 캘리브레이션과 색상 인식 방법이 모두 변경된 관계로 그에 맞추어 라인 코딩 튜닝
> - 색상 인식 중 두 가지 이상 색상 범위에 모두 포함되는 경우, 범위의 중간값에서 오차가 가장 적은 색상을 선택하게 함

[Download](https://drive.google.com/open?id=1cbBe_Bw_YBDlbEZhDGR1j4Em_IDMyMhZ)

<br>

---

# 2019.12.13

- **Go Car: 19.12.27**
- Go Car BleServer: 19.10.16
- Go Car Tester: 19.9.1

> - 라인코딩 업데이트
>   - 12mm 스티커에 최적화
> - 핸드팔로잉 업데이트
>   - 조향, 속도 조절 수정

[Download](https://drive.google.com/open?id=11APu03pQTtA0mbimruGhu22Xi1iai0gU)

<br>

---

# 2019.12.6

- **Go Car: 19.12.14**
- Go Car BleServer: 19.10.16
- Go Car Tester: 19.9.1

> - 라인코딩 업데이트
>   - 좌우 회전 속도 올림
>   - 길 찾았다고 판단하는 기준 값 변경
>   - 일시 정지 후 다시 시작 할 때 라인을 벗어난 경우 짧은 좌우 혹은 우좌 회전하면서 라인을 찾는 명령을 넣음
>   - 교차로에서 좌회전, 우회전 시 방향 지시등 사용
>   - 유턴 시 방향 지시등 사용
>   - 일시 정지 시 비상등 사용
>   - 처음 라인 찾는 동작에서 비상등 사용
>   - 라인을 잃어버린 후 라인을 찾는 좌, 우 회전 동작에서 비상등 사용

[Download](https://drive.google.com/open?id=1TvyIUcWJjGU18Mf-O7ZCxJ1K-JFmCC-p)

<br>

---

# 2019.12.5

- **Go Car: 19.12.8**
- Go Car BleServer: 19.10.16
- Go Car Tester: 19.9.1

> - 라인코딩 업데이트
>   - 좌우 회전, 유턴 동작 개선
>   - 처음 라인 찾기 동작 시 움직임 기준을 시간에서 각도로 변경
>   - 길을 잃어버렸을 때 길찾기 방법 변경
>   - 길을 잃어버렸다고 판단하는 기준 변경

[Download](https://drive.google.com/open?id=1PYiF99FqjqVIoxtS9qY0JJuyX0ZHx0IT)

<br>

---

# 2019.11.27

- **Go Car: 19.11.43**
- Go Car BleServer: 19.10.16
- Go Car Tester: 19.9.1

> - Protocol::DataType::Motor 를 받으면 제어기에서 모터 제어 중단
> - Protocol::DataType::Control 을 받으면 제어기에서 모터 제어 재개
> - 등록되지 않은 장치에 대한 제어기 모터 제어 중단
> - 등록되지 않은 장치는 주기적으로 LED를 빠르게 깜빡이게 함

[Download](https://drive.google.com/open?id=1bH0oQn7j-nLh9PBFTTVNLBKMjxDENAwp)

<br>

---

# 2019.11.21

- **Go Car: 19.11.38**
- Go Car BleServer: 19.10.16
- Go Car Tester: 19.9.1

> - **_이전 버전에서 펌웨어 업그레이드 할 수 없음. 부트로더 교체 필요_**
> - **_부트로더 교체 이후에는 이전 버전으로 다운그레이드 불가능_**
> - 사용자 데이터 저장 단위를 512byte에서 **1Kbyte**로 변경
> - 카드 코딩, 함수 데이터를 항상 플래시 메모리에 저장(각각 최대 120장)
> - 카드, 동작 등을 더 이상 입력할 수 없는 경우 경고음으로 알림

[Download](https://drive.google.com/open?id=1Dd96z9nYzwmJaoaHoJKZQfsw4dD0KoXT)

<br>

---

# 2019.11.19

- **Go Car: 19.11.33**
- Go Car BleServer: 19.10.16
- Go Car Tester: 19.9.1

> - 색상 구분 경계 값 기준을 Front, Rear, Line 세 가지로 구분해서 사용하게 함
> - 위의 변경으로 Drone7Card 프로그램이 이전 버전의 펌웨어와 호환되지 않음
> - 색상 구분 경계 값 측정 실행 중 자동차를 45도 이상 기울이면 동작이 중단됨
> - 색상 구분 경계 값 측정 실행 중 지정한 색상 범위를 크게 벗어나는 경우 Error로 처리하게 함
> - 색상 구분 경계 값 측정 실행 완료 시 Front와 Line은 같은 값으로 설정됨

[Download](https://drive.google.com/open?id=1NRZiF2qcRCESBjZgiRyL69bK0CwmGTun)

<br>

---

# 2019.11.18

- **Go Car: 19.11.29**
- Go Car BleServer: 19.10.16
- Go Car Tester: 19.9.1

> - 버튼을 7회 연속으로 누르면 색상 구분 경계값을 측정하는 모드로 동작함
>   - 버튼을 7회 연속으로 누르면 흰색 깜빡이는 상태가 됨
>   - 위의 상태에서 자동차를 들면 빨간색이 깜빡이는 상태가 됨
>   - 이 때 상하가 모두 빨간색인 카드 위에 자동차를 올려두면 빨간색의 최대-최소 값을 측정
>   - 측정하는 동안 버저가 0.5초 간격으로 울리고 측정이 끝나면 '띠딕'하는 소리가 남
>   - 이 때 자동차를 들어올리면 다음 측정할 색상을 표시
>   - 위의 색상 측정 과정을 6회 반복하면 마지막에 색상 경계값을 계산하여 저장하고 LED가 흰색으로 계속 켜진 상태 유지

[Download](https://drive.google.com/open?id=1xsLlMUNzzB40erjz5GXowvOFTMgQVNqq)

<br>

---

# 2019.11.13

- **Go Car: 19.11.23**
- Go Car BleServer: 19.10.16
- Go Car Tester: 19.9.1

> - 색 분류 기준을 카드 코딩과 라인 코딩에 다르게 적용되도록 분리함

[Download](https://drive.google.com/open?id=1fi1nMVQRBYUPs7IUX5c0W4l8ukZe-BWR)

<br>

---

# 2019.11.8

- **Go Car: 19.11.21**
- Go Car BleServer: 19.10.16
- Go Car Tester: 19.9.1

> - 핸드팔로잉 제어 수정
> - 버튼을 3초 이상 눌러 동작 실행 기능 제거(버튼 두 번 연속 누르기만 사용함, 피아노 모드에서는 멜로디 실행 카드 사용)
> - 버튼을 10초 이상 눌러 센서 리셋 기능 제거(버튼 다섯 번 연속 누르기만 사용함)
> - 카드 코딩 중 코딩 완료 또는 대기 상태일 때에만 실행이 가능하도록 수정
> - 모션 모딩 중 코딩 완료 또는 대기 상태일 때에만 실행이 가능하도록 수정
> - 사용자 멜로디 저장 완료 후에만 멜로디 재생이 동작하도록 수정

[Download](https://drive.google.com/open?id=1LRgtF2L9rU9JUHZRxaVP9vobhtPbUibC)

<br>

---

# 2019.11.7

- **Go Car: 19.11.19**
- Go Car BleServer: 19.10.16
- Go Car Tester: 19.9.1

> - 10초 이상 버튼을 눌러서 센서를 초기화 할 때의 LED 이벤트 수정

[Download](https://drive.google.com/open?id=1W24I85kIh-wlCbyGgQei7dc5edpgv99w)

<br>

---

# 2019.11.6

- **Go Car: 19.11.17**
- Go Car BleServer: 19.10.16
- Go Car Tester: 19.9.1

> - 모션 코딩, 라인 코딩 시작이 안되는 문제 수정
> - 블루투스 연결 이벤트를 받으면 드라이브 모드로 전환

[Download](https://drive.google.com/open?id=14F86mkJE4WppJg6UGgEv0uGnNssZB3g2)

<br>

---

# 2019.11.5

- **Go Car: 19.11.15**
- Go Car BleServer: 19.10.16
- Go Car Tester: 19.9.1

> - **_이전 버전에서 펌웨어 업그레이드 할 수 없음. 부트로더 교체 필요_**
> - **_부트로더 교체 이후에는 이전 버전으로 다운그레이드 불가능_**
> - 사용자 데이터 저장 단위를 256byte에서 **512Kbyte**로 변경
> - 사용자 정의 멜로디 기능 추가
>   - 피아노 모드에서 저장한 멜로디를 카드 코딩에서 멜로디 호출 카드를 사용하여 재생할 수 있는 기능
> - 사용자 정의 멜로디 변경 방법
>   - 피아노 모드 전환
>   - 멜로디 입력 시작 카드 읽기
>   - 멜로디 입력
>   - 멜로디 입력 끝 카드 읽기
> - 피아노 모드에서 사용자 정의 멜로디 실행 방법
>   - 멜로디 실행 카드 읽기
>   - 3초 이상 눌렀다 떼기
> - 현재 미묘하게 수정이 필요할 것으로 보이는 사항
>   - 저장한 멜로디가 이어서 연주됨
>   - 같은 음을 두 번 연주할 경우 하나의 음을 길게 연주한 것처럼 들림
> - 카드 코딩, 함수, 멜로디 카드 최대 120장까지 입력할 수 있도록 수정(코딩 시작, 코딩 끝 카드를 제외하면 118장)
> - 버튼을 5회 연속으로 누르거나 10초 이상 누르면 '도레미파솔라시도' 연주와 함께 센서 리셋
> - 사용자 정의 멜로디를 저장하려고 데이터 저장 단위를 변경함. 부트로더 또한 수정되었기 때문에 이전 버전과 호환이 안됨.

[Download](https://drive.google.com/open?id=1vLFJRM5Y_luuOv7mYYZ7mWleZsLl8Rvv)

<br>

---

# 2019.10.23

- **Go Car: 19.10.13**
- Go Car BleServer: 19.10.16
- Go Car Tester: 19.9.1

> - 카드 코딩에서 Tail LED(브레이크 등) 제어 기능을 제거
> - 브레이크 등은 모터 동작 여부에 따라 제어하도록 변경
> - LED Manual 제어에서도 Tail LED는 조작하지 못하도록 차단
> - 전조등 밝기 조절
> - 브레이크등 밝기 조절
> - E-Drone과 DataType의 Motion, Range 번호 순서를 맞추기 위헤 Altitude를 앞에 추가함
> - 앞으로 PC 프로그램의 중복 개발을 줄이려고 함. 그에 따라 대상 장치에 상관없이 Protocol을 최대한 일치하게 만들 예정

[Download](https://drive.google.com/open?id=1_hwX8KkXVlJ6yJm48oj35MfZ36MY5JBc)

<br>

---

# 2019.10.21

- **Go Car: 19.10.9**
- Go Car BleServer: 19.10.16
- Go Car Tester: 19.9.1

> - 핸드 팔로잉 시 후진 속도를 낮추고 최대 속도를 제한

[Download](https://drive.google.com/open?id=1QYiBlxExXY8rORgW9tHq0Vl6WeRY_L2X)

<br>

---

# 2019.10.18

- **Go Car: 19.10.7**
- **Go Car BleServer: 19.10.16**
- Go Car Tester: 19.9.1

> - 버튼 짧게 누름으로 인식하는 시간을 300ms 이내에서 2초 이내로 변경
> - 버튼 길게 누름으로 인식하는 시간을 1.2초 이상에서 3초 이상으로 변경
> - 버튼 입력 시 정해진 기능 이외에는 오류 알림 소리가 나게 함(버튼 4회 연속 입력 등)
> - 버튼 입력 시 연속 입력으로 인식하는 시간을 0.5초에서 0.6초로 변경(0.6초 이내에 버튼을 다시 누른 경우 연속 입력으로 인식)
> - 각 모드의 기본색 변경
> - 카드 코딩 시 카드 입력 시작(Red -> White), 함수 입력 시작(Green -> Yellow) 기본색을 변경
> - 카드 코딩 모드에서 카드 코딩 시작 전 LED 제어 카드를 눌렀을 때 버튼 입력 소리가 나게 함
> - 통신 보드 BLE 연결이 끊어졌을 때 밝게 깜빡이는 대신 낮은 밝기로 계속 켜져있게 함
> - 펌웨어 자동 업데이트 프로그램 수정

[Download](https://drive.google.com/open?id=1QZizFQrSQEQisZkzl0lWl3I8sgvV1e7X)

<br>

---

# 2019.10.17

- **Go Car: 19.10.6**
- Go Car BleServer: 19.10.14
- Go Car Tester: 19.9.1

> - 모드 전환시 멜로디 알림
> - 핸드팔로잉 기능 추가
>   - 핸드팔로잉 카드를 읽으면 핸드팔로잉 모드로 전환
>   - 바닥에 자동차를 내려놓고 버튼을 **2회 연속** 누르거나 **3초 이상** 누르면 핸드팔로잉 동작 시작
>   - 손 또는 장애물을 자동차 정면 일정 거리 안에 두면 그것과 일정한 거리를 유지하려고 이동 시작
>   - 장애물이 일정거리 이상 멀어지거나 센서 범위를 벗어나면 노란색으로 깜빡이며 정지

[Download](https://drive.google.com/open?id=1oZvVE8qhCGT6SHjvWRQcoIPWul0nUz7G)

<br>

---

# 2019.10.16

- **Go Car: 19.10.4**
- Go Car BleServer: 19.10.14
- Go Car Tester: 19.9.1

> - 모션 코딩 기능 추가
>   - 모션 코딩 카드를 읽으면 모션 코딩 모드로 전환
>   - **코딩 시작 카드**를 읽으면 동작 입력 시작
>   - 앞(전진), 뒤(후진), 좌(왼쪽으로 90도 회전), 우(오른쪽으로 90도 회전)로 기울이면 동작 입력
>   - 다시 수평으로 들면 다음 동작 입력 대기 상태가 됨
>   - 동작 입력이 끝나면 **코딩 종료 카드**를 읽어서 입력을 끝냄
>   - 바닥에 자동차를 내려놓고 버튼을 **2회 연속** 누르거나 **3초 이상** 누르면 모션 코딩 동작 시작

[Download](https://drive.google.com/open?id=14xPjBY8m6U9PoSZFOhTIUz-jQRjnYdnV)

<br>

---

# 2019.10.15

- **Go Car: 19.10.3**
- Go Car BleServer: 19.10.14
- Go Car Tester: 19.9.1

> - 카드 배치 순서 변경

[Download](https://drive.google.com/open?id=1k2oiprOk_ApyQJoRGRCsTo31id5ql8AV)

<br>

---

# 2019.10.11

- **Go Car: 19.10.2**
- Go Car BleServer: 19.10.14
- Go Car Tester: 19.9.1

> - Go Car의 BLE 통신 보드 펌웨어 업데이트 기능 추가
> - Drone7Card.exe의 UI 개선

[Download](https://drive.google.com/open?id=1rG5oz9p1Ff_SK-llNb-6QiK7pkcznGSk)

<br>

---

# 2019.8.28

- **Go Car: 19.8.3**

> - 카드 코딩과 관련된 DataType의 위치 조정, 관련 송수신 클래스 조정

[Download](https://drive.google.com/open?id=1L8Swy8QvJfmzowGek9T79n6KOj4pkXEH)

<br>

---

# 2019.8.23

- **Go Car: 19.8.2**

> - ColorClassify 정의 추가 및 Drone7Card 프로그램에서 카드 분류 기준 값 변경가능하도록 수정함
> - 라인 코딩시에도 CARDREADER에서 분류한 카드 값을 그대로 사용

[Download](https://drive.google.com/open?id=19L5twy8qqK4s5LVczYZ-VNIpEEqpsQBq)

<br>

---

# 2019.8.8

- **Go Car: 19.8.1**

> - 배터리 알람 기준을 30%로 변경
> - RawLineTracer에서 라인트레이서가 인식한 바닥 색상 값이 업데이트 안되는 문제 수정

[Download](https://drive.google.com/open?id=15k5s_RM6OjIFSWm5wxgxmB8nyZnjwhQx)

<br>

---

# 2019.7.26

- **Go Car: 19.7.18**

> - State에서 modeSystem을 modeDrone으로 변경
> - 제어기 수정 사항 반영
> - RawLineTracer에서 바닥 좌우측 IR 데이터 변수 삭제

[Download](https://drive.google.com/open?id=17YawG7WzvIwktDAbe4zfEGrCq0BpCJ2S)

<br>

---

# 2019.7.25 - 2

- **Go Car: 19.7.17**

> - Instant run에서 비상등을 브레이크 등에서 좌우 깜빡이를 동시에 작동시키는 것으로 변경(깜빡임 계속 유지)
> - Instant run에서 TailLight를 끌 때 좌우 깜빡이(비상등)도 끄게 함
> - State 클래스 수정(15 -> 11 byte)

[Download](https://drive.google.com/open?id=11A2eWzCWfYtI2IzzSCF8gMwI9xyskUe7)

<br>

---

# 2019.7.25

- **Go Car: 19.7.16**

> - Low Battery 알림 추가
> - 카드 코딩에서 TailLight를 끌 때 좌우 깜빡이(비상등)도 끄게 함
> - 버저 버퍼를 64에서 128로 변경
> - '조건이 맞지 않으면' 카드 사용 시 조건 루프를 빠져나가는 버그 수정

[Download](https://drive.google.com/open?id=1QCVqnPEv3GDhrz_sORRgYFB5lJ2tADnG)

<br>

---

# 2019.7.24

- **Go Car: 19.7.15**

> - 무한루프에서 버저 사용 시 1회 재생 후 버저가 완전 중단되는 문제 수정
> - 버튼을 길게 눌러 카드 코딩 실행을 할 때 실행 준비가 되면 Buzzer에서 소리가 나게 함
> - 카드 코딩에서 비상등을 브레이크 등에서 좌우 깜빡이를 동시에 작동시키는 것으로 변경(깜빡임 계속 유지)
> - 버저에 멜로디 예약 시 멜로디 전체가 들어갈 공간이 충분한 경우에만 예약하게 함

[Download](https://drive.google.com/open?id=1t7tcTjQexSAdlIIJr4DMqA9H2muomQ5M)

<br>

---

# 2019.7.23

- **Go Car: 19.7.14**

> - 버전 구성을 (Major, Minor, Build)에서 (Year, Month, Build)로 변경함. 제품 출시 전까지 적용해보고 문제가 없을 경우 이후 출시하는 다른 제품에도 적용할 예정. 문제가 있으면 이전 구성으로 복원할 계획임

<br>
