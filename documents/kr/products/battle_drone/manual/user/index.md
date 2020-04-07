<style>

    td.spec      { background: #EEFAFA !important; }
    td.coord     { background: #FFF9FA !important; }
    td.entry     { background: #F7FFF7 !important; }
    td.byblocks  { background: #FEF3FE !important; }
    td.python    { background: #F5FAFF !important; }
    td.issues    { background: #FFFEF5 !important; }
    td.byrobot   { background: #FAFEFE !important; }
    td.white     { background: #FFFFFF !important; }
    td.space     { background: #FFFFFF !important; }

    span.spec      { color: #0489B1; }
    span.firmware  { color: #FF4000; }
    span.driver    { color: #0489B1; }
    span.entry     { color: #FF4000; }
    span.byblocks  { color: #0489B1; }
    span.python    { color: #FF4000; }
    span.issues    { color: #0489B1; }
    span.byrobot   { color: #CCDDEE; }

</style>

**[BATTLE DRONE](/documents/kr/products/e_drone/) User Manual**

Modified : 2020.4.7

---

<h3>BATTLE DRONE 사용자 설명서</h3>

---

* Kramdown table of contents
{:toc .toc}

<br>


# 1. 드론

<br>

## 1.1. 사양

<br>

<div align="center">
    <table>
        <tr>
            <td class="spec"><div align="center"><b>항목</b></div></td>
            <td class="spec"><div align="center"><b>BATTLE DRONE</b></div></td>
        </tr>
        <tr>
            <td class="spec"><div align="center">모터 축간 대각선 길이</div></td>
            <td class="white"><div align="center">95 mm</div></td>
        </tr>
        <tr>
            <td class="spec"><div align="center">무게</div></td>
            <td class="spec"><div align="center">34.5g<br>(배터리 포함)</div></td>
        </tr>
        <tr>
            <td class="spec"><div align="center">배터리</div></td>
            <td class="white"><div align="center">3.7V, 300mAh, 15C<br>LiPo battery<br>(Lithium polymer) </div></td>
        </tr>
        <tr>
            <td class="spec"><div align="center">비행시간</div></td>
            <td class="spec"><div align="center">8분(Max)</div></td>
        </tr>
        <tr>
            <td class="spec"><div align="center">최대조종거리</div></td>
            <td class="white"><div align="center">50m</div></td>
        </tr>
        <tr>
            <td class="spec"><div align="center">통신방식</div></td>
            <td class="spec"><div align="center">2.4Ghz RF</div></td>
        </tr>
        <tr>
            <td class="spec"><div align="center">조종 모드</div></td>
            <td class="white"><div align="center">Mode 1, 2</div></td>
        </tr>
        <tr>
            <td rowspan="3" class="spec"><div align="center">센서</div></td>
            <td class="spec"><div align="center">6-Axis MEMS MotionTracking</div></td>
        </tr>
        <tr>
            <td class="white"><div align="center">Barometer</div></td>
        </tr>
        <tr>
            <td class="spec"><div align="center">IR Transmitter, Receiver</div></td>
        </tr>
        <tr>
            <td rowspan="2" class="spec"><div align="center">주요기능</div></td>
            <td class="white"><div align="center">드론 배틀 게임</div></td>
        </tr>
        <tr>
            <td class="spec"><div align="center">앱, 파이썬 코딩</div></td>
        </tr>
    </table>
</div>


<br>



## 1.2. 좌표계

BATTLE DRONE은 오른손 좌표계를 사용하고 있습니다.

<div align="center">
    <table>
        <tr>
            <td class="coord"><div align="center"><b>좌표축</b></div></td>
            <td class="coord"><div align="center"><b>+</b></div></td>
            <td class="coord"><div align="center"><b>-</b></div></td>
        </tr>
        <tr>
            <td class="coord"><div align="center">X</div></td>
            <td class="white"><div align="center">앞</div></td>
            <td class="white"><div align="center">뒤</div></td>
        </tr>
        <tr>
            <td class="coord"><div align="center">Y</div></td>
            <td class="coord"><div align="center">왼쪽</div></td>
            <td class="coord"><div align="center">오른쪽</div></td>
        </tr>
        <tr>
            <td class="coord"><div align="center">Z</div></td>
            <td class="white"><div align="center">위</div></td>
            <td class="white"><div align="center">아래</div></td>
        </tr>
        <tr>
            <td class="coord"><div align="center">Z 회전</div></td>
            <td class="coord"><div align="center">반시계</div></td>
            <td class="coord"><div align="center">시계</div></td>
        </tr>
    </table>
</div>

아래 문서의 Figure 6 이미지를 참고하시기 바랍니다.

[http://www.physics.brocku.ca/PPLATO/h-flap/math2_5.html#section_3](http://www.physics.brocku.ca/PPLATO/h-flap/math2_5.html#section_3)



<br>

<br>



# 2. 조종기


## 2.1. 버튼 구성 및 기능

<div align="center">
    <img src="./images/byrobot_controller_3_4_button.jpg" alt="조종기 전면">
    <p>배틀 드론 조종기</p>
</div>
<br>

<div align="center">
    <table>
        <tr>
            <td class="coord"><div align="center"><b>번호</b></div></td>
            <td class="coord"><div align="center"><b>짧게 눌렀을 때</b></div></td>
            <td class="coord"><div align="center"><b>길게 눌렀을 때</b></div></td>
        </tr>
        <tr>
            <td class="coord"><div align="center">1</div></td>
            <td class="white"><div align="center">속도 변경 ( 1 / 2 / 3 )</div></td>
            <td class="white"><div align="center">이륙 (대기 상태)<br>착륙 (비행 상태)<br>강제 정지 (Throttle 아래 방향)</div></td>
        </tr>
        <tr>
            <td class="coord"><div align="center">2</div></td>
            <td class="coord"><div align="center">미사일 발사 (Red, Blue)<br>LED 색상 변경 (Magenta)</div></td>
            <td class="coord"><div align="center">Flip 준비 (비행 상태)<br>Flip (Flip 준비가 완료된 상태에서 Roll 또는 Pitch 조작 시)</div></td>
        </tr>
        <tr>
            <td class="coord"><div align="center">3</div></td>
            <td class="white"><div align="center">Heading Reset</div></td>
            <td class="white"><div align="center">Headless 모드 ON / OFF</div></td>
        </tr>
        <tr>
            <td class="coord"><div align="center">4</div></td>
            <td class="coord"><div align="center">팀 변경</div></td>
            <td class="coord"><div align="center">Red, Blue(배틀 모드)<br>Magenta(조종 모드)</div></td>
        </tr>
        <tr>
            <td class="coord"><div align="center">5</div></td>
            <td class="white"><div align="center">Trim Pitch 증가</div></td>
            <td class="white"><div align="center">-</div></td>
        </tr>
        <tr>
            <td class="coord"><div align="center">6</div></td>
            <td class="coord"><div align="center">Trim Roll 감소</div></td>
            <td class="coord"><div align="center">Mode 1</div></td>
        </tr>
        <tr>
            <td class="coord"><div align="center">7</div></td>
            <td class="white"><div align="center">조종 모드 / Link 모드 전환<br>(USB로 데이터를 수신받은 적이 있는 경우에만)</div></td>
            <td class="white"><div align="center">전원 ON / OFF</div></td>
        </tr>
        <tr>
            <td class="coord"><div align="center">8</div></td>
            <td class="coord"><div align="center">Trim Roll 증가</div></td>
            <td class="coord"><div align="center">Mode 2</div></td>
        </tr>
        <tr>
            <td class="coord"><div align="center">9</div></td>
            <td class="white"><div align="center">Trim Pitch 감소</div></td>
            <td class="white"><div align="center">-</div></td>
        </tr>
        <tr>
            <td class="coord"><div align="center">10</div></td>
            <td class="coord"><div align="center">-</div></td>
            <td class="coord"><div align="center">드론 Motion 센서 리셋(드론과 연결된 경우)<br>조이스틱 캘리브레이션 리셋(드론과 연결이 끊어진 경우)</div></td>
        </tr>
        <tr>
            <td class="coord"><div align="center">11</div></td>
            <td class="white"><div align="center">-</div></td>
            <td class="white"><div align="center">페어링(드론이 연결되어 있고, 비행중인 경우엔 무시함)</div></td>
        </tr>
    </table>
</div>

<br>


<br>


## 2.2. MODE

### 2.2.1. MODE 1

<div align="center">
    <img src="./images/byrobot_controller_3_4_mode1.jpg" alt="MODE 1">
    <p>MODE 1</p>
</div>
<br>

<br>

### 2.2.2. MODE 2

<div align="center">
    <img src="./images/byrobot_controller_3_4_mode2.jpg" alt="MODE 2">
    <p>MODE 2</p>
</div>
<br>

<br>



여기까지 BATTLE DRONE 조종기와 드론에 대한 간략한 설명이었습니다.

