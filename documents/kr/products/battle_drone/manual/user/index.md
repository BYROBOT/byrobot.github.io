<style>

    td.spec      { background: #EEFAFA !important; }
    td.coord     { background: #FFF9FA !important; }
    td.team      { background: #F5FFF7 !important; }
    td.red       { background: #FFDDDD !important; }
    td.blue      { background: #DDDDFF !important; }
    td.magenta   { background: #FFDDFF !important; }
    td.explain   { background: #EAFFEA !important; }
    td.white     { background: #FFFFFF !important; }

    span.command   { color: #FF2211; }

</style>

**[BATTLE DRONE](/documents/kr/products/e_drone/) User Manual**

Modified : 2020.4.13

---

<h3>BATTLE DRONE 사용자 설명서</h3>

---

* Kramdown table of contents
{:toc .toc}

<br>


# 1. 드론

<div align="center">
    <img src="./images/byrobot_drone_3_10.jpg" alt="배틀 드론" width="600">
    <p>배틀 드론</p>
</div>

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
            <td class="spec"><div align="center">엔트리, 파이썬 코딩</div></td>
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
    <img src="./images/byrobot_controller_3_4_button.jpg" alt="배틀 드론 조종기" width="600">
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
    <img src="./images/byrobot_controller_3_4_mode1.jpg" alt="MODE 1" width="600">
    <p>MODE 1</p>
</div>
<br>

<br>

### 2.2.2. MODE 2

<div align="center">
    <img src="./images/byrobot_controller_3_4_mode2.jpg" alt="MODE 2" width="600">
    <p>MODE 2</p>
</div>

<br>
<br>
<br>



# 3. 동작


<br>


## 3.1. 페어링

<div align="center">
    <table>
        <tr>
            <td class="explain"><div align="left" style="line-height:2em">
                1. 드론에 배터리가 연결되어 있다면 제거하세요.<br>
                2. 드론에 배터리를 연결합니다.<br>
                3. 드론의 양 옆을 잡고, 좌우로 흔들어줍니다.<br>
                4. 드론의 프로펠러 쪽 LED가 파란색-빨간색 순서로 계속해서 깜빡이면 드론의 페어링 준비가 완료된 것입니다.<br>
                5. 조종기의 전원을 켭니다.<br>
                6. 조종기 오른쪽 하단의 둥근 버튼(11번 버튼)을 3초 이상 길게 누르면 페어링이 완료됩니다.
            </div></td>
        </tr>
    </table>
</div>


<br>

## 3.2. 모드 구분

4번 버튼을 누르면 차례대로 팀 색상이 **Red**, **Blue**, **Magenta**(Red,Blue 동시 켜짐)로 바뀝니다.

<div align="center">
    <table>
        <tr>
            <td class="team"><div align="center"><b>모드</b></div></td>
            <td class="team"><div align="center"><b>색상</b></div></td>
            <td class="team"><div align="center"><b>동작</b></div></td>
            <td class="team"><div align="center"><b>2번 버튼 동작</b></div></td>
        </tr>
        <tr>
            <td class="team" rowspan="2"><div align="center">배틀 모드</div></td>
            <td class="red"><div align="center">RED</div></td>
            <td class="red"><div align="center">전투</div></td>
            <td class="red"><div align="center">미사일 발사</div></td>
        </tr>
        <tr>
            <td class="blue"><div align="center">BLUE</div></td>
            <td class="blue"><div align="center">전투</div></td>
            <td class="blue"><div align="center">미사일 발사</div></td>
        </tr>
        <tr>
            <td class="team"><div align="center">비행 모드</div></td>
            <td class="magenta"><div align="center">MAGENTA</div></td>
            <td class="magenta"><div align="center">비행</div></td>
            <td class="magenta"><div align="center">LED 색 변경</div></td>
        </tr>
    </table>
</div>

<br>
<br>
<br>



## 4. 배틀 모드

배틀 모드는 RED 팀과 BLUE 팀이 배틀 게임을 하는 모드입니다.<br>
기본적인 규칙은 다음과 같습니다.

<div align="center">
    <table>
        <tr>
            <td class="explain"><div align="left">
                1. 사용 가능한 무기는 6종류입니다.
            </div></td>
        </tr>
        <tr>
            <td class="white"><div align="left">
                2. 기본 무기는 레이저입니다.
            </div></td>
        </tr>
        <tr>
            <td class="explain"><div align="left"">
                3. 레이저 이외의 무기는 따로 장전과 발사 동작이 필요합니다.
            </div></td>
        </tr>
        <tr>
            <td class="white"><div align="left"">
                4. 무기 장전 방법 및 효과는 <b>'4.1. 무기'</b>를 참고하시기 바랍니다.
            </div></td>
        </tr>
        <tr>
            <td class="explain"><div align="left"">
                5. 레이저 이외의 무기는 장전되면 10초 이내로 발사해야합니다.
            </div></td>
        </tr>
        <tr>
            <td class="white"><div align="left"">
                6. 무기를 장전한 후 10초가 지나면 다시 레이저로 바뀝니다.
            </div></td>
        </tr>
        <tr>
            <td class="explain"><div align="left"">
                7. 에너지는 전체 6칸이며 <b>레이저</b>에 1회 피격을 당할 때마다 1개씩 줄어듭니다.
            </div></td>
        </tr>
        <tr>
            <td class="white"><div align="left"">
                8. 에너지가 0이 되면 비행기는 착륙합니다.
            </div></td>
        </tr>
        <tr>
            <td class="explain"><div align="left"">
                9. 비행 중에는 팀 변경을 할 수 없습니다.
            </div></td>
        </tr>
        <tr>
            <td class="white"><div align="left"">
                10. 같은 편이 발사한 무기에 대해서는 피격되지 않습니다.
            </div></td>
        </tr>
    </table>
</div>

<br>

### 4.1. 무기

<div align="center">
    <table>
        <tr>
            <td class="coord"><div align="center"><b>무기</b></div></td>
            <td class="coord"><div align="center"><b>최대 장탄 수</b></div></td>
            <td class="coord"><div align="center"><b>무기 보충 시간</b></div></td>
            <td class="coord"><div align="center"><b>사용 방법</b></div></td>
            <td class="coord"><div align="center"><b>효과</b></div></td>
        </tr>
        <tr>
            <td class="coord"><div align="center">레이저</div></td>
            <td class="white"><div align="center">6</div></td>
            <td class="white"><div align="center">0.6초</div></td>
            <td class="white"><div align="center">기본 무기</div></td>
            <td class="white"><div align="center">피격 시 에너지가 1칸 떨어집니다.</div></td>
        </tr>
        <tr>
            <td class="coord"><div align="center">쉴드</div></td>
            <td class="white"><div align="center">1</div></td>
            <td class="white"><div align="center">60초</div></td>
            <td class="white"><div align="center">오른쪽 조이스틱을 <span class="command">우-좌-우-좌</span>로 조작</div></td>
            <td class="white"><div align="center">10초간 무적 상태가 됩니다</div></td>
        </tr>
        <tr>
            <td class="coord"><div align="center">데몬</div></td>
            <td class="white"><div align="center">1</div></td>
            <td class="white"><div align="center">60초</div></td>
            <td class="coord"><div align="center">오른쪽 조이스틱을 <span class="command">왼쪽 방향부터 반시계 방향으로 두 바퀴 회전</span></div></td>
            <td class="coord"><div align="center">10초 동안 적 기체의 앞뒤와 좌우를 반대로 움직이게 합니다.</div></td>
        </tr>
        <tr>
            <td class="coord"><div align="center">물폭탄</div></td>
            <td class="white"><div align="center">1</div></td>
            <td class="white"><div align="center">60초</div></td>
            <td class="white"><div align="center">오른쪽 조이스틱을 <span class="command">오른쪽 방향부터 방향부터 시계 방향으로 두 바퀴 회전</span></div></td>
            <td class="white"><div align="center">10초 동안 적 기체의 조작을 차단하고 미사일을 쏘기 못하게 합니다.</div></td>
        </tr>
        <tr>
            <td class="coord"><div align="center">증폭</div></td>
            <td class="white"><div align="center">1</div></td>
            <td class="white"><div align="center">60초</div></td>
            <td class="coord"><div align="center">왼쪽 조이스틱을 <span class="command">왼쪽 방향부터 반시계 방향으로 두 바퀴 회전</span></div></td>
            <td class="coord"><div align="center">10초 동안 모든 방향의 조작을 최대값으로 만들어 세밀한 조종을 할 수 없게합니다.</div></td>
        </tr>
        <tr>
            <td class="coord"><div align="center">헤딩락</div></td>
            <td class="white"><div align="center">1</div></td>
            <td class="white"><div align="center">60초</div></td>
            <td class="white"><div align="center">왼쪽 조이스틱을 <span class="command">오른쪽 방향부터 방향부터 시계 방향으로 두 바퀴 회전</span></div></td>
            <td class="white"><div align="center">10초 동안 적 기체의 좌우 회전 조작을 못하게 합니다.</div></td>
        </tr>
    </table>
</div>


<br>
<br>
<br>

여기까지 BATTLE DRONE 조종기와 드론에 대한 간략한 설명이었습니다.

