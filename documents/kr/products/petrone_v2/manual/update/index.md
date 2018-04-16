**Petrone V2 firmware Update**

Modified : 2018.4.16

---

<h3>Petrone V2 펌웨어 업데이트</h3>

---

* Kramdown table of contents
{:toc .toc}

<br>

# 1. 펌웨어 다운로드

[Download](/download/) 페이지에서 최신 Petrone V2 펌웨어를 다운로드 받습니다.


<br>


# 2. 조종기 펌웨어 업데이트

<b>(1) 조종기에 USB 커넥터를 연결합니다.</b>

<br>

<b>(2) 조종기 우측 상단의 빨간색 버튼을 누른 채로, 하단 중앙의 스위치를 <i>ON</i>에서 <i>USB</i>로 밀어서 전원을 켭니다.</b>

<div align="center">
    <img src="1_controller_1_off.jpg" alt="controller off">
</div>
<br>

<b>(3) 조종기의 전원이 켜지면서 부트로더의 펌웨어 업데이트 모드를 시작합니다.</b>

<div align="center">
    <img src="1_controller_2_bootloader.jpg" alt="controller bootloader">
    <p>부트로더 펌웨어 업데이트 모드 진입 화면</p>
</div>
<br>

<div align="center">
    <img src="1_controller_3_info.jpg" alt="controller bootloader information">
    <p>부트로더 요약 정보 표시 화면</p>
</div>
<br>

<div align="center">
    <img src="1_controller_4_ready.jpg" alt="controller update ready">
    <p>조종기 펌웨어 업데이트 대기 화면</p>
</div>
<br>

<b>(4) 펌웨어 업데이트 프로그램을 실행합니다.</b>

<div align="center">
    <img src="1_controller_5_folder.jpg" alt="run firmware update program">
    <p>펌웨어 업데이트 프로그램</p>
</div>
<br>

<div align="center">
    <img src="1_controller_6_firmware_folder.jpg" alt="firmware folder">
    <p>펌웨어 파일 폴더</p>
</div>
<br>

<b>(5) 펌웨어를 선택합니다. 처음 실행하면 기본으로 조종기 펌웨어가 선택되어 있습니다.</b>

<div align="center">
    <img src="1_controller_7_firmware_updater.jpg" alt="run firmware update program">
    <p>펌웨어 업데이트 프로그램 실행 화면</p>
</div>
<br>

<div align="center">
    <img src="1_controller_8_firmware_updater_combobox_open.jpg" alt="firmware folder">
    <p>펌웨어 파일 선택 콤보박스</p>
</div>
<br>

<b>(6) SCAN 버튼을 눌러 시리얼 포트 검색을 실행합니다. 그 후 SCAN 버튼 하단의 콤보 박스를 눌러 원하는 시리얼 포트를 선택합니다. 조종기를 먼저 연결한 후 프로그램을 실행하였다면 이 단계를 건너뛰셔도 됩니다.</b>

<div align="center">
    <img src="1_controller_9_scan_button.jpg" alt="scan">
    <p>스캔 버튼</p>
</div>
<br>

<b>(7) UPDATE 버튼을 눌러 펌웨어 업데이트를 시작합니다.</b>

<div align="center">
    <img src="1_controller_10_update_button.jpg" alt="update">
    <p>업데이트 버튼</p>
</div>
<br>

<div align="center">
    <img src="1_controller_11_firmware_updater_update.jpg" alt="update">
    <p>업데이트 진행 화면</p>
</div>
<br>

<div align="center">
    <img src="1_controller_12_controller_graph.jpg" alt="update controller">
    <p>조종기 업데이트 진행 상태</p>
</div>
<br>

<b>(8) 업데이트가 완료되면 조종기는 자동으로 재시작합니다. USB 연결이 정상적으로 되려면 전원을 껐다가 다시 켜시기 바랍니다.</b>

<div align="center">
    <img src="1_controller_13_updatecomplete.jpg" alt="update complete">
    <p>조종기 업데이트 완료 상태</p>
</div>
<br>


<br>


# 3. 드론 펌웨어 업데이트

<b>(1) 조종기에 USB 커넥터를 연결합니다.</b>
<br>

<b>(2) 조종기 하단 중앙의 스위치를 <i>ON</i>에서 <i>USB</i>로 밀어서 전원을 켭니다.</b>

<div align="center">
    <img src="2_drone_1_on.jpg" alt="controller on">
    <p>조종기 전원을 켠 상태</p>
</div>
<br>

<b>(3) 드론의 전원이 꺼진 상태에서 드론 측면의 버튼을 누른 채로 배터리를 밀어 넣어 전원을 켭니다. 드론이 부트로더의 펌웨어 업데이트 모드가 되면 LED가 하늘색으로 느리게 깜빡입니다.</b>

<div align="center">
    <img src="2_drone_2_side_button.jpg" alt="drone switch">
    <p>드론 측면 스위치를 누른 상태에서 배터리를 연결</p>
</div>
<br>

<b>(4) 드론이 부트로더의 펌웨어 업데이트 모드로 켜진 상태에서 조종기와 연결된 경우 아래와 같은 화면을 볼 수 있습니다. 만약 드론과 조종기의 전원이 모두 켜진 상태에서 아래와 같은 화면이 나오지 않고 연결이 끊어졌다고 표시되는 경우 페어링을 하셔야 합니다. 보통 때의 페어링과 동일한 방법으로, 전원이 켜진 상태에서 드론 측면의 버튼을 길게 눌러서 페어링 대기 상태로 만들고, 조종기를 설정 모드로 바꾼 다음 조종기의 우측 하단의 원형 버튼을 길게 눌러서 페어링을 하시면 됩니다.</b>

<div align="center">
    <img src="2_drone_3_drone_connected.jpg" alt="update ready">
    <p>드론 펌웨어 업데이트 모드</p>
</div>
<br>

<b>(5) 펌웨어 업데이트 프로그램을 실행한 뒤 펌웨어 선택 콤보박스에서 드론 펌웨어를 선택합니다.</b>

<div align="center">
    <img src="2_drone_4_firmware_combobox.jpg" alt="firmware combobox">
    <p>펌웨어 선택 콤보박스</p>
</div>
<br>

<div align="center">
    <img src="2_drone_5_firmware_selected.jpg" alt="firmware selected">
    <p>드론 펌웨어를 선택한 후 화면</p>
</div>
<br>

<b>(6) SCAN 버튼을 눌러 시리얼 포트 검색을 실행합니다. 그 후 SCAN 버튼 하단의 콤보 박스를 눌러 원하는 시리얼 포트를 선택합니다. 조종기를 먼저 연결한 후 프로그램을 실행하였다면 이 단계를 건너뛰셔도 됩니다.</b>

<div align="center">
    <img src="2_drone_6_scan.jpg" alt="scan">
    <p>스캔 버튼</p>
</div>
<br>

<b>(7) UPDATE 버튼을 눌러 펌웨어 업데이트를 시작합니다.</b>

<div align="center">
    <img src="2_drone_7_update.jpg" alt="update">
    <p>업데이트 버튼</p>
</div>
<br>

<div align="center">
    <img src="2_drone_8_firmware_update.jpg" alt="update">
    <p>업데이트 진행 화면</p>
</div>
<br>

<div align="center">
    <img src="2_drone_9_update_controller.jpg" alt="update controller">
    <p>드론 펌웨어 업데이트 시 조종기 업데이트 진행 화면</p>
</div>
<br>

<b>(8) 업데이트가 완료된 후 조종기 또는 드론의 전원을 껐다 켜면 드론이 새로운 펌웨어로 다시 시작합니다.</b>

<div align="center">
    <img src="2_drone_10_firmware_update_complete.jpg" alt="update complete">
    <p>드론 업데이트 완료 상태</p>
</div>
<br>

<br>


여기까지 Petrone V2 조종기와 드론의 펌웨어 업데이트를 완료하였습니다.

