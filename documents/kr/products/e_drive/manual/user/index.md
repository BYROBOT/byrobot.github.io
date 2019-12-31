**[E-DRIVE](/documents/kr/products/e_drive/) User Manual**

Modified : 2019.3.11

---

<h3>GO CAR 사용자 설명서</h3>

---

* Kramdown table of contents
{:toc .toc}

<br>


# 1. 자동차


## 1.1. 좌표계

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



## 1.2 동작 모드

GO CAR 는 여러 동작 모드를 가지고 있습니다.

| 이름                          | 설명                                                                                                      |
|------------------------------:|:----------------------------------------------------------------------------------------------------------|
| 조종                          | 앱으로 자동차를 사용할 때 동작하는 모드입니다                                                             |
| 카드 코딩                     | 카드 코딩 모드입니다. 자동차를 켰을 때 처음 시작하는 모드입니다                                           |
| 모션 코딩                     | 자동차를 앞, 뒤, 좌, 우 방향으로 기울여서 코딩하는 모드입니다                                             |
| 핸드 팔로잉                   | 자동차가 정면의 장애물과 일정 거리를 유지하면서 움직이게 하는 모드입니다                                  |
| 라인 코딩                     | 자동차가 바닥의 두꺼운 검정 선을 따라다니며 바닥의 둥근 색깔 스티커를 인식하여 특정한 동작을 합니다       |
| 수동 컬러 캘리브레이션        | 검정, 흰색, 빨강, 노랑, 초록, 하늘, 파랑, 자홍 색을 차례로 눌러서 카드 색상을 잘 인식할 수 있게 합니다    |
| 자동 컬러 캘리브레이션        | 검정, 흰색, 빨강, 노랑, 초록, 하늘, 파랑, 자홍 색 영역을 차례로 이동하며 색상을 자동으로 인식합니다       |
| 자동 거리 센서 캘리브레이션   | 장애물과 완전히 밀착한 상태에서 뒤로 이동하며 양쪽 거리 센서의 출력값 차이를 보정합니다                   |



<br>



## 1.3 버튼

GO CAR 의 상단 LED 부분을 누르면 바닥에 있는 버튼이 눌러집니다.
이 버튼을 누르는 횟수에 따라 정해진 명령을 실행합니다.


<br>


### 1.3.1. 기본 동작

| 횟수    | 동작                                                            |
|:-------:|:----------------------------------------------------------------|
| 1       | 카드 읽기                                                       |
| 2       | 실행                                                            |
| 3       | 흰색, 검정색 카드를 각각 읽어서 R, G, B 색 범위 캘리브레이션    |
| 4       | 자동차 바닥 색상에 따라 동작 실행(아래에 상세 설명)             |
| 5       | 자동 거리 센서 캘리브레이션                                     |
| 6       | 수동 컬러 캘리브레이션                                          |
| 7       | 자동 컬러 캘리브레이션                                          |
| 8       | -                                                               |
| 9       | 설정값 초기화 및 모션 센서 캘리브레이션                         |


<br>


### 1.3.2. 버튼을 4회 눌렀을 때 바닥 색상에 따른 동작 실행

| 바탕 색상(앞/뒤)  | 동작                                      |
|:-----------------:|:------------------------------------------|
| 흰색 / 흰색       | 자동 컬러 캘리브레이션                    |
| 흰색 / 검정       | 거리 센서 캘리브레이션                    |
| 검정 / 흰색       | 설정값 초기화 및 모션 센서 캘리브레이션   |
| 검정 / 검정       | 수동 컬러 캘리브레이션                    |

<br>


## 1.4. 카드


<table>
    <tr>
        <td>
            <div align="center">
                분류
            </div>
        </td>
        <td>
            <div align="center">
                앞
            </div>
        </td>
        <td>
            <div align="center">
                뒤
            </div>
        </td>
        <td>
            <div align="center">
                기본 동작(1회 누름)
            </div>
        </td>
        <td>
            <div align="center">
                3회 누름
            </div>
        </td>
        <td>
            <div align="center">
                4회 누름
            </div>
        </td>
    </tr>
    <tr>
        <td rowspan="8">모드</td>
        <td rowspan="8" bgcolor="white"></td>
        <td bgcolor="white"></td><td></td><td>카드 최대 밝기 설정</td><td>자동 컬러 캘리브레이션</td>
    </tr>
        <tr><td bgcolor="red"></td><td>카드 코딩</td><td></td><td></td></tr>
        <tr><td bgcolor="yellow"></td><td>모션 코딩</td><td></td><td></td></tr>
        <tr><td bgcolor="green"></td><td> - </td><td></td><td></td></tr>
        <tr><td bgcolor="cyan"></td><td> - </td><td></td><td></td></tr>
        <tr><td bgcolor="blue"></td><td>핸드 팔로잉</td><td></td><td></td></tr>
        <tr><td bgcolor="magenta"></td><td>라인 트레이서 모드</td><td></td><td></td></tr>
        <tr><td bgcolor="black"></td><td>피아노 모드</td><td></td><td>거리 센서 캘리브레이션</td></tr>
    <tr>
        <td rowspan="8">기능</td>
        <td rowspan="8" bgcolor="red"></td>
        <td bgcolor="white"></td><td>카드 입력 시작</td></td><td></td></td><td></td>
    </tr>
        <tr><td bgcolor="red"></td><td>카드 입력 종료</td><td></td><td></td></tr>
        <tr><td bgcolor="yellow"></td><td>함수 입력 시작</td><td></td><td></td></tr>
        <tr><td bgcolor="green"></td><td>함수 입력 종료</td><td></td><td></td></tr>
        <tr><td bgcolor="cyan"></td><td>함수 호출</td><td></td><td></td></tr>
        <tr><td bgcolor="blue"></td><td>핸</td><td></td><td></td></tr>
        <tr><td bgcolor="magenta"></td><td>라</td><td></td><td></td></tr>
        <tr><td bgcolor="black"></td><td>피</td><td></td><td></td></tr>
    <tr>
        <td rowspan="8">모드</td>
        <td rowspan="8" bgcolor="yellow"></td>
        <td bgcolor="white"></td><td>카</td></td><td></td></td><td></td>
    </tr>
        <tr><td bgcolor="red"></td><td>카</td><td></td><td></td></tr>
        <tr><td bgcolor="yellow"></td><td>모</td><td></td><td></td></tr>
        <tr><td bgcolor="green"></td><td>모</td><td></td><td></td></tr>
        <tr><td bgcolor="cyan"></td><td>모</td><td></td><td></td></tr>
        <tr><td bgcolor="blue"></td><td>핸</td><td></td><td></td></tr>
        <tr><td bgcolor="magenta"></td><td>라</td><td></td><td></td></tr>
        <tr><td bgcolor="black"></td><td>피</td><td></td><td></td></tr>
    <tr>
        <td rowspan="8">모드</td>
        <td rowspan="8" bgcolor="green"></td>
        <td bgcolor="white"></td><td>카</td></td><td></td></td><td></td>
    </tr>
        <tr><td bgcolor="red"></td><td>카</td><td></td><td></td></tr>
        <tr><td bgcolor="yellow"></td><td>모</td><td></td><td></td></tr>
        <tr><td bgcolor="green"></td><td>모</td><td></td><td></td></tr>
        <tr><td bgcolor="cyan"></td><td>모</td><td></td><td></td></tr>
        <tr><td bgcolor="blue"></td><td>핸</td><td></td><td></td></tr>
        <tr><td bgcolor="magenta"></td><td>라</td><td></td><td></td></tr>
        <tr><td bgcolor="black"></td><td>피</td><td></td><td></td></tr>
    <tr>
        <td rowspan="8">모드</td>
        <td rowspan="8" bgcolor="cyan"></td>
        <td bgcolor="white"></td><td>카</td></td><td></td></td><td></td>
    </tr>
        <tr><td bgcolor="red"></td><td>카</td><td></td><td></td></tr>
        <tr><td bgcolor="yellow"></td><td>모</td><td></td><td></td></tr>
        <tr><td bgcolor="green"></td><td>모</td><td></td><td></td></tr>
        <tr><td bgcolor="cyan"></td><td>모</td><td></td><td></td></tr>
        <tr><td bgcolor="blue"></td><td>핸</td><td></td><td></td></tr>
        <tr><td bgcolor="magenta"></td><td>라</td><td></td><td></td></tr>
        <tr><td bgcolor="black"></td><td>피</td><td></td><td></td></tr>
    <tr>
        <td rowspan="8">모드</td>
        <td rowspan="8" bgcolor="blue"></td>
        <td bgcolor="white"></td><td>카</td></td><td></td></td><td></td>
    </tr>
        <tr><td bgcolor="red"></td><td>카</td><td></td><td></td></tr>
        <tr><td bgcolor="yellow"></td><td>모</td><td></td><td></td></tr>
        <tr><td bgcolor="green"></td><td>모</td><td></td><td></td></tr>
        <tr><td bgcolor="cyan"></td><td>모</td><td></td><td></td></tr>
        <tr><td bgcolor="blue"></td><td>핸</td><td></td><td></td></tr>
        <tr><td bgcolor="magenta"></td><td>라</td><td></td><td></td></tr>
        <tr><td bgcolor="black"></td><td>피</td><td></td><td></td></tr>
    <tr>
        <td rowspan="8">모드</td>
        <td rowspan="8" bgcolor="magenta"></td>
        <td bgcolor="white"></td><td>카</td></td><td></td></td><td></td>
    </tr>
        <tr><td bgcolor="red"></td><td>카</td><td></td><td></td></tr>
        <tr><td bgcolor="yellow"></td><td>모</td><td></td><td></td></tr>
        <tr><td bgcolor="green"></td><td>모</td><td></td><td></td></tr>
        <tr><td bgcolor="cyan"></td><td>모</td><td></td><td></td></tr>
        <tr><td bgcolor="blue"></td><td>핸</td><td></td><td></td></tr>
        <tr><td bgcolor="magenta"></td><td>라</td><td></td><td></td></tr>
        <tr><td bgcolor="black"></td><td>피</td><td></td><td></td></tr>
    <tr>
        <td rowspan="8">모드</td>
        <td rowspan="8" bgcolor="black"></td>
        <td bgcolor="white"></td><td>카</td></td><td></td></td><td></td>
    </tr>
        <tr><td bgcolor="red"></td><td>카</td><td></td><td></td></tr>
        <tr><td bgcolor="yellow"></td><td>모</td><td></td><td></td></tr>
        <tr><td bgcolor="green"></td><td>모</td><td></td><td></td></tr>
        <tr><td bgcolor="cyan"></td><td>모</td><td></td><td></td></tr>
        <tr><td bgcolor="blue"></td><td>핸</td><td></td><td></td></tr>
        <tr><td bgcolor="magenta"></td><td>라</td><td></td><td></td></tr>
        <tr><td bgcolor="black"></td><td>피</td><td></td><td></td></tr>
</table>

<br>



여기까지 GO CAR 에 대한 간략한 설명이었습니다.

