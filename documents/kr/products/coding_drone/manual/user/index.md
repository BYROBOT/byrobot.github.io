<style>

    td.spec       { background: #EEFAFA !important; }
    td.coord      { background: #FFF9FA !important; }
    td.setup_odd  { background: #FFFEF5 !important; }
    td.setup_even { background: #F5FAFF !important; }
    td.white      { background: #FFFFFF !important; }

    td.joystick_left   { background: #FFF5F5 !important; }
    td.joystick_right  { background: #F5F5FF !important; }

    td.throttle   { background: #FFDDDD !important; }
    td.rudder     { background: #FFFFDD !important; }
    td.elevator   { background: #DDFFFF !important; }
    td.aileron    { background: #DDFFDD !important; }

    td.w { background: #FFFFFF !important; }
    td.k { background: #000000 !important; }
    td.r { background: #FF0000 !important; }
    td.y { background: #FFFF00 !important; }
    td.g { background: #00FF00 !important; }
    td.c { background: #00FFFF !important; }
    td.b { background: #0000FF !important; }
    td.m { background: #FF00FF !important; }

    td.lightgrey  { background: #C9C9C9 !important; }
    td.darkgrey   { background: #909090 !important; }

</style>

**[CODING DRONE](/documents/kr/products/e_drone/) User Manual**

Modified : 2020.4.28

---

<h3>Coding Drone 사용자 설명서</h3>

---

* Kramdown table of contents
{:toc .toc}

<br>


# 1. 드론

<div align="center">
    <img src="./images/byrobot_drone_8.jpg" alt="CODING DRONE" width="600" height="600">
    <p>CODING DRONE</p>
</div>


<br>

## 1.1. 사양

<br>

<div align="center">
    <table>
        <tr>
            <td class="spec"><div align="center"><b>항목</b></div></td>
            <td class="spec"><div align="center"><b>Coding Drone</b></div></td>
        </tr>
        <tr>
            <td class="spec"><div align="center">모터 축간 대각선 길이</div></td>
            <td class="white"><div align="center">103 mm</div></td>
        </tr>
        <tr>
            <td class="spec"><div align="center">무게</div></td>
            <td class="spec"><div align="center">55g<br>(배터리 포함)</div></td>
        </tr>
        <tr>
            <td class="spec"><div align="center">배터리</div></td>
            <td class="white"><div align="center">3.7V, 530mAh<br>LiPo battery<br>(Lithium polymer)</div></td>
        </tr>
        <tr>
            <td class="spec"><div align="center">비행시간</div></td>
            <td class="spec"><div align="center">7 ~ 10분</div></td>
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
            <td class="white"><div align="center">Mode 1, 2, 3, 4</div></td>
        </tr>
        <tr>
            <td class="spec" rowspan="4"><div align="center">센서</div></td>
            <td class="spec"><div align="center">Optical flow</div></td>
        </tr>
        <tr>
            <td class="white"><div align="center">6-Axis MEMS MotionTracking</div></td>
        </tr>
        <tr>
            <td class="spec"><div align="center">IR Time of Flight</div></td>
        </tr>
        <tr>
            <td class="white"><div align="center">Barometer</div></td>
        </tr>
        <tr>
            <td class="spec" rowspan="3"><div align="center">주요기능</div></td>
            <td class="spec"><div align="center">실내 위치 인식</div></td>
        </tr>
        <tr>
            <td class="white"><div align="center">Return Home</div></td>
        </tr>
        <tr>
            <td class="spec"><div align="center">엔트리, 파이썬 코딩</div></td>
        </tr>
    </table>
</div>


<br>
<br>
<br>


## 1.2. 좌표계

Coding Drone은 오른손 좌표계를 사용하고 있습니다.

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
<br>


## 1.3. 동작 모드

Coding Drone은 여러 동작 모드를 가지고 있습니다.

| 이름                | 설명                                                                                                   |
|--------------------:|:-------------------------------------------------------------------------------------------------------|
| **조종**            | 조종기로 드론을 조종할 때 사용하는 모드입니다                                                          |
| **카드 코딩**       | 카드 코딩 모드입니다. 드론을 켰을 때 처음 시작하는 모드입니다                                          |
| **모션 코딩**       | 드론를 앞, 뒤, 좌, 우 방향으로 기울여서 코딩하는 모드입니다                                            |
| **피아노**          | 카드를 사용하여 음악 연주를 하는 모드입니다                                                            |

<br>

센서 초기화 기능

| 이름                          | 설명                                                                                                      |
|:-----------------------------:|:----------------------------------------------------------------------------------------------------------|
| **모션 센서 캘리브레이션**    | 동작 센서의 바이어스를 초기화합니다.                                                                      |
| **컬러 캘리브레이션**    | 검정, 흰색, 빨강, 노랑, 초록, 하늘, 파랑, 자홍 색을 차례로 눌러서 카드 색상을 잘 인식하게 합니다          |



<br>
<br>
<br>


## 1.4. 버튼

Coding Drone은 두 개의 버튼이 있습니다. 여기에서는 편의에 따라 *드론 윗면 앞 부분의 버튼*은 **설정 버튼**, <br>
드론 바닥 부분의 좌측에(뒤집어서 봤을 때 우측) 있는 버튼은 **모드 버튼**이라고 하겠습니다.<br>
버튼을 사용 방법은 **여러번 연속으로 누르기**와 **길게 누르가**를 사용합니다.


<br>


### 1.4.1. 설정 버튼 동작


| 버튼 누른 횟수 | 동작                         |
|:--------------:|:-----------------------------|
| 1              | **카드 읽기**                |
| 2              | **시작** 또는 **실행**       |
| 4              | 모션 센서 캘리브레이션 시작  |
| 5              | 컬러 캘리브레이션 시작       |
| 9              | 설정값 초기화                |

<br>
<br>


### 1.4.2. 모드 버튼 동작


| 버튼 누른 횟수 | 동작                      |
|:--------------:|:--------------------------|
| 2              | 카드 코딩 모드            |
| 3              | 모션 코딩 모드            |
| 4              | 피아노 모드               |
| 5              | 컬러 캘리브레이션 모드    |

<br> 

| 버튼 누른 시간 | 동작                      |
|:--------------:|:--------------------------|
| 3초            | **페어링**                |


<br>
<br>
<br>


## 1.5. 카드

<br>


### 1.5.1. 모드 변경(버튼 1회 입력)

<table>
    <tr>
        <td><div align="center">분류</div></td>
        <td><div align="center">앞</div></td>
        <td><div align="center">뒤</div></td>
        <td><div align="center">동작</div></td>
    </tr>
    <tr>
        <td rowspan="3"><div align="center">모드</div></td>
        <td rowspan="3" class="w"></td>
        <td class="r"></td><td>카드 코딩 모드(초기 모드)</td>
    </tr>
        <tr><td class="y"></td><td>모션 코딩 모드</td></tr>
        <tr><td class="k"></td><td>피아노 모드</td></tr>
</table>


<br>



### 1.5.2. 카드 코딩

<table>
    <tr>
        <td><div align="center">분류</div></td>
        <td><div align="center">앞</div></td>
        <td><div align="center">뒤</div></td>
        <td><div align="center">기본 동작(1회 누름)</div></td>
    </tr>
    <tr>
        <td rowspan="8"><div align="center">기능</div></td>
        <td rowspan="8" class="r"></td>
        <td class="w"></td><td>카드 입력 시작</td>
    </tr>
        <tr><td class="r"></td><td>카드 입력 종료</td></tr>
        <tr><td class="y"></td><td>함수 입력 시작</td></tr>
        <tr><td class="g"></td><td>함수 입력 종료</td></tr>
        <tr><td class="c"></td><td>함수 호출</td></tr>
        <tr><td class="b"></td><td>멜로디 호출</td></tr>
        <tr><td class="m"></td><td>속도 조절(카드를 읽을 때 마다 1, 2, 3 단계가 차례로 바뀜)</td></tr>
        <tr><td class="k"></td><td>1초 기다림</td></tr>
    <tr>
        <td rowspan="8"><div align="center">RGB LED</div></td>
        <td rowspan="8" class="y"></td>
        <td class="w"></td><td>흰색</td>
    </tr>
        <tr><td class="r"></td><td>빨강</td></tr>
        <tr><td class="y"></td><td>노랑</td></tr>
        <tr><td class="g"></td><td>초록</td></tr>
        <tr><td class="c"></td><td>하늘</td></tr>
        <tr><td class="b"></td><td>파랑</td></tr>
        <tr><td class="m"></td><td>자홍</td></tr>
        <tr><td class="k"></td><td>검정(꺼짐)</td></tr>
    <tr>
        <td rowspan="8"><div align="center">동작 설정</div></td>
        <td rowspan="8" class="g"></td>
        <td class="w"></td><td>이륙</td>
    </tr>
        <tr><td class="r"></td><td>착륙</td></tr>
        <tr><td class="y"></td><td>이동 단위를 <b>30cm</b>로 설정</td></tr>
        <tr><td class="g"></td><td>이동 단위를 <b>50cm</b>로 설정</td></tr>
        <tr><td class="c"></td><td>이동 단위를 <b>1m</b>로 설정</td></tr>
        <tr><td class="b"></td><td>회전 단위를 <b>30도</b>로 설정</td></tr>
        <tr><td class="m"></td><td>회전 단위를 <b>45도</b>로 설정</td></tr>
        <tr><td class="k"></td><td>회전 단위를 <b>90도</b>로 설정</td></tr>
    <tr>
        <td rowspan="8"><div align="center">이동, 회전</div></td>
        <td rowspan="8" class="c"></td>
        <td class="w"></td><td>앞으로 이동</td>
    </tr>
        <tr><td class="r"></td><td>뒤로 이동</td></tr>
        <tr><td class="y"></td><td>왼쪽으로 이동</td></tr>
        <tr><td class="g"></td><td>오른쪽으로 이동</td></tr>
        <tr><td class="c"></td><td>위로 이동</td></tr>
        <tr><td class="b"></td><td>아래로 이동</td></tr>
        <tr><td class="m"></td><td>왼쪽으로 회전</td></tr>
        <tr><td class="k"></td><td>오른쪽으로 회전</td></tr>
    <tr>
        <td rowspan="8"><div align="center">조건</div></td>
        <td rowspan="8" class="b"></td>
        <td class="w"></td><td>장애물 발견 시(If)</td>
    </tr>
        <tr><td class="r"></td><td>바닥 빨간색을 발견 시(If)</td></tr>
        <tr><td class="y"></td><td>바닥 노란색을 발견 시(If)</td></tr>
        <tr><td class="g"></td><td>바닥 초록색을 발견 시(If)</td></tr>
        <tr><td class="c"></td><td>바닥 하늘색을 발견 시(If)</td></tr>
        <tr><td class="b"></td><td>바닥 파란색을 발견 시(If)</td></tr>
        <tr><td class="m"></td><td>아니면(Else)</td></tr>
        <tr><td class="k"></td><td>조건 끝(End)</td></tr>
    <tr>
        <td rowspan="8"><div align="center">반복</div></td>
        <td rowspan="8" class="m"></td>
        <td class="w"></td><td>무한 반복</td>
    </tr>
        <tr><td class="r"></td><td>2회 반복</td></tr>
        <tr><td class="y"></td><td>3회 반복</td></tr>
        <tr><td class="g"></td><td>4회 반복</td></tr>
        <tr><td class="c"></td><td>5회 반복</td></tr>
        <tr><td class="b"></td><td>10회 반복</td></tr>
        <tr><td class="m"></td><td>중단(Break)</td></tr>
        <tr><td class="k"></td><td>반복 끝</td></tr>
    <tr>
        <td rowspan="8"><div align="center">음계</div></td>
        <td rowspan="8" class="k"></td>
        <td class="w"></td><td>도(5 옥타브)</td>
    </tr>
        <tr><td class="r"></td><td>레</td></tr>
        <tr><td class="y"></td><td>미</td></tr>
        <tr><td class="g"></td><td>파</td></tr>
        <tr><td class="c"></td><td>솔</td></tr>
        <tr><td class="b"></td><td>라</td></tr>
        <tr><td class="m"></td><td>시</td></tr>
        <tr><td class="k"></td><td>도(6 옥타브)</td></tr>
</table>

<br>


### 1.5.3. 피아노 모드

<br>

#### 1.5.3.1. 기능
<table>
    <tr>
        <td><div align="center">분류</div></td>
        <td><div align="center">앞</div></td>
        <td><div align="center">뒤</div></td>
        <td><div align="center">기본 동작</div></td>
    </tr>
    <tr>
        <td rowspan="8"><div align="center">기능</div></td>
        <td rowspan="8" class="r"></td>
        <td class="w"></td><td>사용자 정의 멜로디 입력 시작</td>
    </tr>
        <tr><td class="r"></td><td>사용자 정의 멜로디 입력 종료</td></tr>
        <tr><td class="y"></td><td>멜로디 1</td></tr>
        <tr><td class="g"></td><td>멜로디 2</td></tr>
        <tr><td class="c"></td><td>멜로디 3</td></tr>
        <tr><td class="b"></td><td>저장한 멜로디 실행</td></tr>
        <tr><td class="m"></td><td>쉼표 0.5초</td></tr>
        <tr><td class="k"></td><td>쉼표 1초</td></tr>
</table>

<br>

#### 1.5.3.2. 3 Octave

<table>
    <tr>
        <td></td>
        <td colspan="8"><div align="center">3 Octave Sharp</div></td>
    </tr>
    <tr>
        <td width="50"><div align="center">앞</div></td>
        <td width="50" class="y">&nbsp;&nbsp;&nbsp;&nbsp;</td>
        <td width="50" class="y">&nbsp;</td>
        <td width="50" class="lightgrey">&nbsp;</td>
        <td width="50" class="y">&nbsp;</td>
        <td width="50" class="y">&nbsp;</td>
        <td width="50" class="y">&nbsp;</td>
        <td width="50" class="lightgrey">&nbsp;</td>
        <td width="50" class="lightgrey">&nbsp;</td>
    </tr>
    <tr>
        <td><div align="center">뒤</div></td>
        <td class="w">&nbsp;</td>
        <td class="r">&nbsp;</td>
        <td class="lightgrey">&nbsp;</td>
        <td class="g">&nbsp;</td>
        <td class="c">&nbsp;</td>
        <td class="b">&nbsp;</td>
        <td class="lightgrey">&nbsp;</td>
        <td class="lightgrey">&nbsp;</td>
    </tr>
    <tr>
        <td></td>
        <td><div align="center">C#</div></td>
        <td><div align="center">D#</div></td>
        <td class="lightgrey"><div align="center">&nbsp;</div></td>
        <td><div align="center">F#</div></td>
        <td><div align="center">G#</div></td>
        <td><div align="center">A#</div></td>
        <td class="lightgrey"><div align="center">&nbsp;</div></td>
        <td class="lightgrey"><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td></td>
        <td colspan="8"><div align="center">3 Octave</div></td>
    </tr>
    <tr>
        <td><div align="center">앞</div></td>
        <td class="g">&nbsp;</td>
        <td class="g">&nbsp;</td>
        <td class="g">&nbsp;</td>
        <td class="g">&nbsp;</td>
        <td class="g">&nbsp;</td>
        <td class="g">&nbsp;</td>
        <td class="g">&nbsp;</td>
        <td class="lightgrey">&nbsp;</td>
    </tr>
    <tr>
        <td><div align="center">뒤</div></td>
        <td class="w">&nbsp;</td>
        <td class="r">&nbsp;</td>
        <td class="y">&nbsp;</td>
        <td class="g">&nbsp;</td>
        <td class="c">&nbsp;</td>
        <td class="b">&nbsp;</td>
        <td class="m">&nbsp;</td>
        <td class="lightgrey">&nbsp;</td>
    </tr>
    <tr>
        <td></td>
        <td><div align="center">C</div></td>
        <td><div align="center">D</div></td>
        <td><div align="center">E</div></td>
        <td><div align="center">F</div></td>
        <td><div align="center">G</div></td>
        <td><div align="center">A</div></td>
        <td><div align="center">B</div></td>
        <td class="lightgrey"><div align="center">&nbsp;</div></td>
    </tr>
</table>

<br>

#### 1.5.3.3. 4 Octave

<table>
    <tr>
        <td></td>
        <td colspan="8"><div align="center">4 Octave Sharp</div></td>
    </tr>
    <tr>
        <td width="50"><div align="center">앞</div></td>
        <td width="50" class="c">&nbsp;</td>
        <td width="50" class="c">&nbsp;</td>
        <td width="50" class="lightgrey">&nbsp;</td>
        <td width="50" class="c">&nbsp;</td>
        <td width="50" class="c">&nbsp;</td>
        <td width="50" class="c">&nbsp;</td>
        <td width="50" class="lightgrey">&nbsp;</td>
        <td width="50" class="lightgrey">&nbsp;</td>
    </tr>
    <tr>
        <td><div align="center">뒤</div></td>
        <td class="w">&nbsp;</td>
        <td class="r">&nbsp;</td>
        <td class="lightgrey">&nbsp;</td>
        <td class="g">&nbsp;</td>
        <td class="c">&nbsp;</td>
        <td class="b">&nbsp;</td>
        <td class="lightgrey">&nbsp;</td>
        <td class="lightgrey">&nbsp;</td>
    </tr>
    <tr>
        <td></td>
        <td><div align="center">C#</div></td>
        <td><div align="center">D#</div></td>
        <td class="lightgrey"><div align="center">&nbsp;</div></td>
        <td><div align="center">F#</div></td>
        <td><div align="center">G#</div></td>
        <td><div align="center">A#</div></td>
        <td class="lightgrey"><div align="center">&nbsp;</div></td>
        <td class="lightgrey"><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td></td>
        <td colspan="8"><div align="center">4 Octave</div></td>
    </tr>
    <tr>
        <td><div align="center">앞</div></td>
        <td class="b">&nbsp;</td>
        <td class="b">&nbsp;</td>
        <td class="b">&nbsp;</td>
        <td class="b">&nbsp;</td>
        <td class="b">&nbsp;</td>
        <td class="b">&nbsp;</td>
        <td class="b">&nbsp;</td>
        <td class="lightgrey">&nbsp;</td>
    </tr>
    <tr>
        <td><div align="center">뒤</div></td>
        <td class="w">&nbsp;</td>
        <td class="r">&nbsp;</td>
        <td class="y">&nbsp;</td>
        <td class="g">&nbsp;</td>
        <td class="c">&nbsp;</td>
        <td class="b">&nbsp;</td>
        <td class="m">&nbsp;</td>
        <td class="lightgrey">&nbsp;</td>
    </tr>
    <tr>
        <td></td>
        <td><div align="center">C</div></td>
        <td><div align="center">D</div></td>
        <td><div align="center">E</div></td>
        <td><div align="center">F</div></td>
        <td><div align="center">G</div></td>
        <td><div align="center">A</div></td>
        <td><div align="center">B</div></td>
        <td class="lightgrey"><div align="center">&nbsp;</div></td>
    </tr>
</table>

<br>

#### 1.5.3.4. 5 Octave

<table>
    <tr>
        <td></td>
        <td colspan="8"><div align="center">5 Octave Sharp</div></td>
    </tr>
    <tr>
        <td width="50"><div align="center">앞</div></td>
        <td width="50" class="m">&nbsp;</td>
        <td width="50" class="m">&nbsp;</td>
        <td width="50" class="lightgrey">&nbsp;</td>
        <td width="50" class="m">&nbsp;</td>
        <td width="50" class="m">&nbsp;</td>
        <td width="50" class="m">&nbsp;</td>
        <td width="50" class="lightgrey">&nbsp;</td>
        <td width="50" class="lightgrey">&nbsp;</td>
    </tr>
    <tr>
        <td><div align="center">뒤</div></td>
        <td class="w">&nbsp;</td>
        <td class="r">&nbsp;</td>
        <td class="lightgrey">&nbsp;</td>
        <td class="g">&nbsp;</td>
        <td class="c">&nbsp;</td>
        <td class="b">&nbsp;</td>
        <td class="lightgrey">&nbsp;</td>
        <td class="lightgrey">&nbsp;</td>
    </tr>
    <tr>
        <td></td>
        <td><div align="center">C#</div></td>
        <td><div align="center">D#</div></td>
        <td class="lightgrey"><div align="center">&nbsp;</div></td>
        <td><div align="center">F#</div></td>
        <td><div align="center">G#</div></td>
        <td><div align="center">A#</div></td>
        <td class="lightgrey"><div align="center">&nbsp;</div></td>
        <td class="lightgrey"><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td></td>
        <td colspan="8"><div align="center">5 Octave</div></td>
    </tr>
    <tr>
        <td><div align="center">앞</div></td>
        <td class="k">&nbsp;</td>
        <td class="k">&nbsp;</td>
        <td class="k">&nbsp;</td>
        <td class="k">&nbsp;</td>
        <td class="k">&nbsp;</td>
        <td class="k">&nbsp;</td>
        <td class="k">&nbsp;</td>
        <td class="lightgrey">&nbsp;</td>
    </tr>
    <tr>
        <td><div align="center">뒤</div></td>
        <td class="w">&nbsp;</td>
        <td class="r">&nbsp;</td>
        <td class="y">&nbsp;</td>
        <td class="g">&nbsp;</td>
        <td class="c">&nbsp;</td>
        <td class="b">&nbsp;</td>
        <td class="m">&nbsp;</td>
        <td class="lightgrey">&nbsp;</td>
    </tr>
    <tr>
        <td></td>
        <td><div align="center">C</div></td>
        <td><div align="center">D</div></td>
        <td><div align="center">E</div></td>
        <td><div align="center">F</div></td>
        <td><div align="center">G</div></td>
        <td><div align="center">A</div></td>
        <td><div align="center">B</div></td>
        <td class="lightgrey"><div align="center">&nbsp;</div></td>
    </tr>
</table>


<br>
<br>
<br>


# 2. 조종기


## 2.1 조종기 화면 구성

Coding Drone의 조종기는 크게 ***조종***과 ***설정*** 두 화면으로 구성되어 있습니다.

<div align="center">
    <table>
        <tr>
            <td class="lightgrey">
                <img src="./images/display_control.png" alt="control">
            </td>
        </tr>
    </table>
    〈조종 화면〉
</div>

조종 화면에서는 드론 조종, 트림 설정, 상태 확인 등을 할 수 있습니다.

<br>

<div align="center">
    <table>
        <tr>
            <td class="lightgrey">
                <img src="./images/display_setup.png" alt="setup">
            </td>
        </tr>
    </table>
    〈설정 화면〉
</div>

설정 화면에서는 드론 설정 변경, 상태 확인 등을 할 수 있습니다.

<br>
<br>
<br>


## 2.2 조종 화면 세부 구성

<br>

### 2.2.1. 높이-자세-RPM

<table>
    <tr>
        <td class="lightgrey">
            <div align="center">
                <a href="./images/drone4controller_1.png" target="_blank"><img src="./images/drone4controller_1.png"></a>
            </div>
        </td>
        <td></td>
        <td class="darkgrey">
            <div align="center">
                <a href="./images/drone4controller_1_desc.png" target="_blank"><img src="./images/drone4controller_1_desc.png"></a>
            </div>
        </td>
    </tr>
</table>


<br>


### 2.2.2. 높이-방향-RPM-자세-고도-위치

<table>
    <tr>
        <td class="lightgrey">
            <div align="center">
                <a href="./images/drone4controller_2.png" target="_blank"><img src="./images/drone4controller_2.png"></a>
            </div>
        </td>
        <td></td>
        <td class="darkgrey">
            <div align="center">
                <a href="./images/drone4controller_2_desc.png" target="_blank"><img src="./images/drone4controller_2_desc.png"></a>
            </div>
        </td>
    </tr>
</table>


<br>


### 2.2.3. 속도-위치-자세

<table>
    <tr>
        <td class="lightgrey">
            <div align="center">
                <a href="./images/drone4controller_3.png" target="_blank"><img src="./images/drone4controller_3.png"></a>
            </div>
        </td>
        <td></td>
        <td class="darkgrey">
            <div align="center">
                <a href="./images/drone4controller_3_desc.png" target="_blank"><img src="./images/drone4controller_3_desc.png"></a>
            </div>
        </td>
    </tr>
</table>


<br>


### 2.2.4. 자세-높이

<table>
    <tr>
        <td class="lightgrey">
            <div align="center">
                <a href="./images/drone4controller_4.png" target="_blank"><img src="./images/drone4controller_4.png"></a>
            </div>
        </td>
        <td></td>
        <td class="darkgrey">
            <div align="center">
                <a href="./images/drone4controller_4_desc.png" target="_blank"><img src="./images/drone4controller_4_desc.png"></a>
            </div>
        </td>
    </tr>
</table>


<br>


### 2.2.5. 위치-트림

<table>
    <tr>
        <td class="lightgrey">
            <div align="center">
                <a href="./images/drone4controller_5.png" target="_blank"><img src="./images/drone4controller_5.png"></a>
            </div>
        </td>
        <td></td>
        <td class="darkgrey">
            <div align="center">
                <a href="./images/drone4controller_5_desc.png" target="_blank"><img src="./images/drone4controller_5_desc.png"></a>
            </div>
        </td>
    </tr>
</table>


<br>


### 2.2.6. RF 정보 및 상태 

<table>
    <tr>
        <td class="lightgrey">
            <div align="center">
                <a href="./images/drone4controller_6.png" target="_blank"><img src="./images/drone4controller_6.png"></a>
            </div>
        </td>
        <td></td>
        <td class="darkgrey">
            <div align="center">
                <a href="./images/drone4controller_6_desc.png" target="_blank"><img src="./images/drone4controller_6_desc.png"></a>
            </div>
        </td>
    </tr>
</table>


<br>


### 2.2.7. 조이스틱 입력 값 

<table>
    <tr>
        <td class="lightgrey">
            <div align="center">
                <a href="./images/drone4controller_7.png" target="_blank"><img src="./images/drone4controller_7.png"></a>
            </div>
        </td>
        <td></td>
        <td class="darkgrey">
            <div align="center">
                <a href="./images/drone4controller_7_desc.png" target="_blank"><img src="./images/drone4controller_7_desc.png"></a>
            </div>
        </td>
    </tr>
</table>


<br>


### 2.2.8. 버전

<table>
    <tr>
        <td class="lightgrey">
            <div align="center">
                <a href="./images/drone4controller_8.png" target="_blank"><img src="./images/drone4controller_8.png"></a>
            </div>
        </td>
        <td></td>
        <td class="darkgrey">
            <div align="center">
                <a href="./images/drone4controller_8_desc.png" target="_blank"><img src="./images/drone4controller_8_desc.png"></a>
            </div>
        </td>
    </tr>
</table>


<br>
<br>
<br>


## 2.3. 버튼 구성 및 기능

<br>

### 2.3.1. 조종 화면

<div align="center">
    <img src="./images/button_control_front.jpg" alt="조종기 전면">
    <p>조종 화면에서 전면 버튼의 기능</p>
</div>
<br>

<div align="center">
    <img src="./images/button_control_top.jpg" alt="조종기 상단">
    <p>조종 화면에서 상단 버튼의 기능</p>
</div>
<br>

<br>

### 2.3.2. 설정 화면

<div align="center">
    <img src="./images/button_setup_front.jpg" alt="조종기 전면">
    <p>설정 화면에서 전면 버튼의 기능</p>
</div>
<br>

<div align="center">
    <img src="./images/button_setup_top.jpg" alt="조종기 상단">
    <p>설정 화면에서 상단 버튼의 기능</p>
</div>
<br>

<br>
<br>
<br>


## 2.4. 설정 화면 메뉴 구성

<div align="center">
    <table>
        <tr>
            <td class="setup_even">
                <div align="center">
                    1단계
                </div>
            </td>
            <td class="setup_even">
                <div align="center">
                    2단계
                </div>
            </td>
            <td class="setup_even" colspan="4">
                <div align="center">
                    설명
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_odd" rowspan="7">
                <div align="center">
                    DISPLAY
                </div>
            </td>
            <td class="setup_odd">
                <div align="center">
                    높이-자세-RPM
                </div>
            </td>
            <td class="setup_odd" colspan="4">
                <div align="left">
                    조종 화면에서 보여줄 것인지를 설정(SHOW / HIDE)
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    높이-방향-RPM-자세-고도-위치
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    조종 화면에서 보여줄 것인지를 설정(SHOW / HIDE)
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_odd">
                <div align="center">
                    속도-위치-자세
                </div>
            </td>
            <td class="setup_odd" colspan="4">
                <div align="left">
                    조종 화면에서 보여줄 것인지를 설정(SHOW / HIDE)
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    자세-높이
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    조종 화면에서 보여줄 것인지를 설정(SHOW / HIDE)
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_odd">
                <div align="center">
                    위치-트림
                </div>
            </td>
            <td class="setup_odd" colspan="4">
                <div align="left">
                    조종 화면에서 보여줄 것인지를 설정(SHOW / HIDE)
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    RF 정보 및 상태
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    조종 화면에서 보여줄 것인지를 설정(SHOW / HIDE)
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_odd">
                <div align="center">
                    조이스틱 입력 값
                </div>
            </td>
            <td class="setup_odd" colspan="4">
                <div align="left">
                    조종 화면에서 보여줄 것인지를 설정(SHOW / HIDE)
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_even" rowspan="2">
                <div align="center">
                    LIGHT
                </div>
            </td>
            <td class="setup_even">
                <div align="center">
                    DRONE
                </div>
            </td>
            <td class="setup_even" colspan="4">
                <div align="left">
                    드론 LED 기본 색 설정 변경
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    CONTROLLER
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    조종기 LED 기본 색 설정 변경
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_odd" rowspan="2">
                <div align="center">
                    CONTROL
                </div>
            </td>
            <td class="setup_odd">
                <div align="center">
                    ATTITUDE
                </div>
            </td>
            <td class="setup_odd" colspan="4">
                <div align="left">
                    자세 제어
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    POSITION
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    위치 제어
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_even" rowspan="5">
                <div align="center">
                    MODE
                </div>
            </td>
            <td class="setup_even">
                <div align="center">
                    MODE
                </div>
            </td>
            <td class="joystick_left">
                <div align="center">
                    Left ↕
                </div>
            </td>
            <td class="joystick_left">
                <div align="center">
                    Left ↔
                </div>
            </td>
            <td class="joystick_right">
                <div align="center">
                    Right ↕
                </div>
            </td>
            <td class="joystick_right">
                <div align="center">
                    Right ↔
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    MODE 1
                </div>
            </td>
            <td class="elevator">
                <div align="center">
                    앞뒤<br>(Elevator)
                </div>
            </td>
            <td class="rudder">
                <div align="center">
                    좌우 회전<br>(Rudder)
                </div>
            </td>
            <td class="throttle">
                <div align="center">
                    위아래<br>(Throttle)
                </div>
            </td>
            <td class="aileron">
                <div align="center">
                    좌우<br>(Aileron)
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_even">
                <div align="center">
                    MODE 2
                </div>
            </td>
            <td class="throttle">
                <div align="center">
                    위아래<br>(Throttle)
                </div>
            </td>
            <td class="rudder">
                <div align="center">
                    좌우 회전<br>(Rudder)
                </div>
            </td>
            <td class="elevator">
                <div align="center">
                    앞뒤<br>(Elevator)
                </div>
            </td>
            <td class="aileron">
                <div align="center">
                    좌우<br>(Aileron)
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    MODE 3
                </div>
            </td>
            <td class="elevator">
                <div align="center">
                    앞뒤<br>(Elevator)
                </div>
            </td>
            <td class="aileron">
                <div align="center">
                    좌우<br>(Aileron)
                </div>
            </td>
            <td class="throttle">
                <div align="center">
                    위아래<br>(Throttle)
                </div>
            </td>
            <td class="rudder">
                <div align="center">
                    좌우 회전<br>(Rudder)
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_even">
                <div align="center">
                    MODE 4
                </div>
            </td>
            <td class="throttle">
                <div align="center">
                    위아래<br>(Throttle)
                </div>
            </td>
            <td class="aileron">
                <div align="center">
                    좌우<br>(Aileron)
                </div>
            </td>
            <td class="elevator">
                <div align="center">
                    앞뒤<br>(Elevator)
                </div>
            </td>
            <td class="rudder">
                <div align="center">
                    좌우 회전<br>(Rudder)
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_odd" rowspan="2">
                <div align="center">
                    HEADLESS
                </div>
            </td>
            <td class="setup_odd">
                <div align="center">
                    HEADLESS
                </div>
            </td>
            <td class="setup_odd" colspan="4">
                <div align="left">
                    헤드리스(방향 고정)
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    NORMAL
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    일반(드론의 현재 방향 기준)
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_even" rowspan="3">
                <div align="center">
                    SPEED
                </div>
            </td>
            <td class="setup_even">
                <div align="center">
                    S1
                </div>
            </td>
            <td class="setup_even" colspan="4">
                <div align="left">
                    속도 1단계(느림)
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    S2
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    속도 2단계
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_even">
                <div align="center">
                    S3
                </div>
            </td>
            <td class="setup_even" colspan="4">
                <div align="left">
                    속도 3단계(빠름)
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_odd" rowspan="2">
                <div align="center">
                    FHSS
                </div>
            </td>
            <td class="setup_odd">
                <div align="center">
                    ON
                </div>
            </td>
            <td class="setup_odd" colspan="4">
                <div align="left">
                    채널 호핑
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    OFF
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    고정 채널
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_even" rowspan="3">
                <div align="center">
                    FUNCTION
                </div>
            </td>
            <td class="setup_even">
                <div align="center">
                    SENSOR RESET
                </div>
            </td>
            <td class="setup_even" colspan="4">
                <div align="left">
                    드론의 자이로 바이어스 리셋
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    PAIRING
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    페어링
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_even">
                <div align="center">
                    SET DEFAULT
                </div>
            </td>
            <td class="setup_even" colspan="4">
                <div align="left">
                    설정값 초기화(드론이 연결된 경우 드론 설정도 초기화 됨)
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_odd" rowspan="10">
                <div align="center">
                    INFORMATION
                </div>
            </td>
            <td class="setup_odd">
                <div align="center">
                    COUNT
                </div>
            </td>
            <td class="setup_odd" colspan="4">
                <div align="left">
                    비행 시간 및 이벤트 카운트 값 표시
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    BIAS
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    가속도, 자이로 바이어스 값 표시
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_odd">
                <div align="center">
                    TRIM
                </div>
            </td>
            <td class="setup_odd" colspan="4">
                <div align="left">
                    Trim 값 표시
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    MOTION
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    IMU 센서 데이터를 연산하여 변환한 결과 표시
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_odd">
                <div align="center">
                    ALTITUDE
                </div>
            </td>
            <td class="setup_odd" colspan="4">
                <div align="left">
                    높이-고도와 관련된 센서 데이터 표시
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    POSITION
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    위치 데이터 표시
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_odd">
                <div align="center">
                    RF
                </div>
            </td>
            <td class="setup_odd" colspan="4">
                <div align="left">
                    RF 설정 데이터 표시
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    ADDRESS
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    드론과 조종기의 고유번호 표시
                </div>
            </td>
        </tr>
        <tr>
            <td class="setup_odd">
                <div align="center">
                    BOOT
                </div>
            </td>
            <td class="setup_odd" colspan="4">
                <div align="left">
                    조종기의 부트 정보 및 장치 등록 여부 표시
                </div>
            </td>
        </tr>
        <tr>
            <td class="white">
                <div align="center">
                    CRC32
                </div>
            </td>
            <td class="white" colspan="4">
                <div align="left">
                    드론과 조종기의 부트로더 및 앱 영역 CRC32 값 표시
                </div>
            </td>
        </tr>
    </table>
</div>


<br>
<br>
<br>


## 2.5. MODE

### 2.5.1. MODE 1

<div align="center">
    <img src="./images/mode1.jpg" alt="MODE 1" width="800">
    <p>MODE 1</p>
</div>

<br>
<br>

### 2.5.2. MODE 2

<div align="center">
    <img src="./images/mode2.jpg" alt="MODE 2" width="800">
    <p>MODE 2</p>
</div>
<br>

<br>



여기까지 Coding Drone 조종기와 드론에 대한 간략한 설명이었습니다.
