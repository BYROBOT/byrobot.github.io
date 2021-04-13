**[GO CAR](/documents/kr/products/e_drone/) firmware Update**

Modified : 2021.4.13

---

<h3>GO CAR 펌웨어 업데이트</h3>

---

- [Drone4AutoUpdaterLight](../drone4autoupdaterlight/)
- [drone_4_updater_windows](../drone_4_updater_windows/)
- [drone_4_updater_mac](../drone_4_updater_mac/)
- [drone_4_updater_linux](../drone_4_updater_linux/)
- **drone_4_updater_raspberry_pi**
- [Python Library](../python/)

---

* Kramdown table of contents
{:toc .toc}

<br>

# 1. 펌웨어 다운로드 및 업데이트 프로그램 실행

## 1.1. 펌웨어 다운로드
[GO CAR](/documents/kr/products/e_drive/) 페이지에서 최신 GO CAR 펌웨어를 내려받습니다.

<div align="center">
    <img src="./images/1_download.png" alt="Download">
    <p>펌웨어 업데이트 프로그램 다운로드 링크(빨간색 상자 안의 'Raspberry PI')</p>
</div>
<br>

<br>

## 1.2. 프로그램 실행

<div align="center">
    <img src="./images/1_2_terminal.png" alt="Download">
    <p>Terminal에서 프로그램을 실행하기까지의 명령 입력 예</p>
</div>
<br>

### 1.2.1. Terminal 프로그램을 실행합니다.

<br>

### 1.2.2. Download 폴더로 이동합니다.

```
cd Downloads/
```

<br>

### 1.2.3. 다운 받은 프로그램의 압축을 풀어줍니다.

파일명을 입력하실 때 처음 몇 글자를 입력한 후 'Tab' 키를 누르면 자동으로 남은 이름을 채워줍니다.

```
unzip drone_4_updater_raspberry_pi_linux_arm_20210401.zip
```

<br>

### 1.2.4. 압축 푼 경로로 이동합니다.

폴더명을 입력할 때에도 처음 몇 글자를 입력한 후 'Tab' 키를 누르면 자동으로 남은 이름을 채워줍니다.

```
cd drone_4_updater_raspberry_pi_linux_arm_20210401
```

<br>

### 1.2.5. 프로그램의 권한을 변경합니다.

```
chmod 755 drone_4_updater
```

<br>

### 1.2.6. 프로그램을 실행합니다.

```
./drone_4_updater
```

<br>


<br>


# 2. 자동차 업데이트

(1) "drone_4_updater"를 실행합니다.

<div align="center">
    <img src="./images/2_1_1_2_drone_4_updater.png" alt="drone_4_updater.exe">
    <p>펌웨어 업데이트 프로그램 실행 화면</p>
</div>
<br>

(2) 자동차의 전원이 켜져 있다면 전원을 꺼주세요.

<br>

(3) 자동차 바닥 면의 버튼(아래 그림의 빨간색 박스)을 누른 채로 스위치(아래 그림의 노란색 박스)를 켭니다.

<div align="center">
    <img src="../images/bootloader_button_drone.jpg" alt="bootloader button">
    <p>자동차 부트로더 진입 버튼과 전원 스위치</p>
</div>
<br>

(4) 자동차의 전원이 켜지고 자동으로 업데이트를 진행합니다.

<div align="center">
    <img src="./images/2_1_4_1_drone_4_updater.png" alt="drone_4_updater.exe">
    <p>자동차 펌웨어 업데이트 진행 화면</p>
</div>
<br>

<div align="center">
    <img src="./images/2_1_4_2_drone_4_updater.png" alt="drone_4_updater.exe">
    <p>자동차 펌웨어 업데이트 완료 화면</p>
</div>
<br>


<br>


여기까지 GO CAR 펌웨어 업데이트를 완료하였습니다.

