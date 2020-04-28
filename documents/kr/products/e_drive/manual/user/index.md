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

**[E-DRIVE](/documents/kr/products/e_drive/) User Manual**

Modified : 2020.4.28

---

<h3>GO CAR 사용자 설명서</h3>

---

* Kramdown table of contents
{:toc .toc}

<br>



# 자동차


<br>


## 1. 좌표계

GO CAR 는 오른손 좌표계를 사용하고 있습니다.

| 좌표축  | +        | -        |
|:-------:|:--------:|:--------:|
| X       | 앞       | 뒤       |
| Y       | 왼쪽     | 오른쪽   |
| Z       | 위       | 아래     |
| Z 회전  | 반시계   | 시계     |

아래 문서의 Figure 6 이미지를 참고하시기 바랍니다.

[http://www.physics.brocku.ca/PPLATO/h-flap/math2_5.html#section_3](http://www.physics.brocku.ca/PPLATO/h-flap/math2_5.html#section_3)



<br>
<br>
<br>


## 2. 동작 모드

GO CAR는 여러 동작 모드를 가지고 있습니다.

| 이름                          | 설명                                                                                                      |
|:-----------------------------:|:----------------------------------------------------------------------------------------------------------|
| **조종**                      | 앱으로 자동차를 조종할 때 사용하는 모드입니다                                                             |
| **카드 코딩**                 | 카드 코딩 모드입니다. 자동차를 켰을 때 처음 시작하는 모드입니다                                           |
| **모션 코딩**                 | 자동차를 앞, 뒤, 좌, 우 방향으로 기울여서 코딩하는 모드입니다                                             |
| **핸드 팔로잉**               | 자동차가 정면의 장애물과 일정 거리를 유지하면서 움직이게 하는 모드입니다                                  |
| **라인 코딩**                 | 자동차가 바닥의 두꺼운 검정 선을 따라다니며 바닥의 둥근 색깔 스티커를 인식하여 정해진 동작을 합니다       |
| **피아노**                    | 카드를 사용하여 음악 연주를 하는 모드입니다                                                               |

<br>

센서 초기화 기능
| 이름                          | 설명                                                                                                      |
|:-----------------------------:|:----------------------------------------------------------------------------------------------------------|
| **모션 센서 캘리브레이션**    | 동작 센서의 바이어스를 초기화합니다.                                                                      |
| **수동 컬러 캘리브레이션**    | 검정, 흰색, 빨강, 노랑, 초록, 하늘, 파랑, 자홍 색을 차례로 눌러서 카드 색상을 잘 인식하게 합니다          |
| 자동 컬러 캘리브레이션        | 검정, 흰색, 빨강, 노랑, 초록, 하늘, 파랑, 자홍 색 영역을 차례로 이동하며 색상을 자동으로 인식합니다       |
| 자동 거리 센서 캘리브레이션   | 장애물과 완전히 밀착한 상태에서 뒤로 이동하며 양쪽 거리 센서의 출력값 차이를 보정합니다                   |



<br>
<br>
<br>


## 3. 버튼

GO CAR 의 상단 LED 부분을 누르면 바닥에 있는 버튼이 눌러집니다.<br>
이 버튼을 누르는 횟수에 따라 정해진 명령을 실행합니다.


| 버튼을 누른 횟수  | 동작                                                            |
|:-----------------:|:----------------------------------------------------------------|
| 1                 | **카드 읽기**                                                   |
| 2                 | **시작** 또는 **실행**                                          |
| 4                 | 자동차 바닥 색상에 따라 동작 실행([4.2.](#4_2_)에 상세 설명)    |
| 5                 | **모션 센서 캘리브레이션 시작**                                 |
| 6                 | 자동 거리 센서 캘리브레이션 시작                                |
| 7                 | **수동 컬러 캘리브레이션 시작**                                 |
| 8                 | 자동 컬러 캘리브레이션 시작                                     |
| 9                 | 설정값 초기화                                                   |



<br>
<br>
<br>


## 4. 카드

<br>


### 4.1. 모드 변경(버튼 1회 입력)

<table>
    <tr>
        <td><div align="center">분류</div></td>
        <td><div align="center">앞</div></td>
        <td><div align="center">뒤</div></td>
        <td><div align="center">동작</div></td>
    </tr>
    <tr>
        <td rowspan="5"><div align="center">모드</div></td>
        <td rowspan="5" class="w"></td>
        <td class="r"></td><td>카드 코딩 모드(초기 모드)</td>
    </tr>
        <tr><td class="y"></td><td>모션 코딩 모드</td></tr>
        <tr><td class="b"></td><td>핸드 팔로잉</td></tr>
        <tr><td class="m"></td><td>라인 트레이서 모드</td></tr>
        <tr><td class="k"></td><td>피아노 모드</td></tr>
</table>


<br>
<br>
<br>



<a name="4_2_"></a>

### 4.2. 기능 실행(버튼 4회 입력)

<table>
    <tr>
        <td><div align="center">분류</div></td>
        <td><div align="center">앞</div></td>
        <td><div align="center">뒤</div></td>
        <td><div align="center">동작</div></td>
    </tr>
    <tr>
        <td rowspan="4"><div align="center">기능</div></td>
        <td rowspan="2" class="w"></td>
        <td class="w"></td><td>자동 컬러 캘리브레이션 시작</td>
    </tr>
        <tr><td class="k"></td><td>거리 센서 캘리브레이션 시작</td></tr>
    <tr>
        <td rowspan="2" class="k"></td>
        <td class="w"></td><td>모션 센서 캘리브레이션 시작</td>
    </tr>
        <tr><td class="k"></td><td><b>수동 컬러 캘리브레이션 시작</b></td></tr>
</table>


<br>
<br>
<br>



### 4.3. 카드 코딩

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
        <tr><td class="m"></td><td>도리도리</td></tr>
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
        <td rowspan="8"><div align="center">LIGHT</div></td>
        <td rowspan="8" class="g"></td>
        <td class="w"></td><td>상향등</td>
    </tr>
        <tr><td class="r"></td><td>비상등</td></tr>
        <tr><td class="y"></td><td>전조등</td></tr>
        <tr><td class="g"></td><td>좌회전 신호</td></tr>
        <tr><td class="c"></td><td>우회전 신호</td></tr>
        <tr><td class="b"></td><td>정지등</td></tr>
        <tr><td class="m"></td><td>정지등 끄기</td></tr>
        <tr><td class="k"></td><td>전조등 끄기</td></tr>
    <tr>
        <td rowspan="8"><div align="center">이동</div></td>
        <td rowspan="8" class="c"></td>
        <td class="w"></td><td>전진</td>
    </tr>
        <tr><td class="r"></td><td>1 블럭 전진</td></tr>
        <tr><td class="y"></td><td>유턴</td></tr>
        <tr><td class="g"></td><td>좌회전</td></tr>
        <tr><td class="c"></td><td>우회전</td></tr>
        <tr><td class="b"></td><td>1 블럭 후진</td></tr>
        <tr><td class="m"></td><td>후진</td></tr>
        <tr><td class="k"></td><td>정지</td></tr>
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
        <td class="w"></td><td>도</td>
    </tr>
        <tr><td class="r"></td><td>레</td></tr>
        <tr><td class="y"></td><td>미</td></tr>
        <tr><td class="g"></td><td>파</td></tr>
        <tr><td class="c"></td><td>솔</td></tr>
        <tr><td class="b"></td><td>라</td></tr>
        <tr><td class="m"></td><td>시</td></tr>
        <tr><td class="k"></td><td>도</td></tr>
</table>

<br>
<br>
<br>


### 4.4. 피아노 모드

<br>

#### 4.4.1. 기능
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

#### 4.4.2. 3 Octave

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

#### 4.4.3. 4 Octave

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

#### 4.4.4. 5 Octave

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


여기까지 GO CAR 에 대한 간략한 설명이었습니다.

