### PETRONE

---
<!-------------------------------------------------------------------------------------------------------

    2020.4.2

    각 index.md 파일 변경 시 사소한 링크 수정이나 펌웨어 업데이트 등은 직접 수정해도 상관없으나

    디자인 변경, 테이블 구조 변경 등의 작업을 하게 되는 경우, nightly.md 파일에서 먼저 작업을 할 것.

    git에 올려 화면이 정상적으로 표시되는지를 확인하고, index.md 파일을 변경하는 것을 권장함

-------------------------------------------------------------------------------------------------------->

<style>

    td.documents   { background: #EEFAFA !important; }
    td.firmware    { background: #FFF9FA !important; }
    td.driver      { background: #F7FFF7 !important; }
    td.entry       { background: #FEF3FE !important; }
    td.repository  { background: #F5FAFF !important; }
    td.python      { background: #FFFEF5 !important; }
    td.issues      { background: #EFF1FC !important; }
    td.byrobot     { background: #FAFEFE !important; }
    td.white       { background: #FFFFFF !important; }
    td.space       { background: #FFFFFF !important; }

    span.odd 	   { color: #0489B1; }
    span.even	   { color: #FF4000; }
    span.byrobot   { color: #CCDDEE; }

</style>

<div align="center">
    <img src="/assets/images/products/byrobot_drone_1.png" alt="petrone">
    <table style="padding: 0px 0px 0px 0px;">
        <tr>
            <td width="110" class="documents"><a href="#Documents"><span class="odd"><div align="center">Documents</div></span></a></td>
            <td width="110" class="firmware"><a href="#Firmware"><span class="even"><div align="center">Firmware</div></span></a></td>
            <td width="110" class="driver"><a href="#Driver"><span class="odd"><div align="center">Driver</div></span></a></td>
        </tr>
        <tr>
            <td width="110" class="repository"><a href="#Repository"><span class="even"><div align="center">Repository</div></span></a></td>
            <td width="110" class="python"><a href="#Python"><span class="odd"><div align="center">Python</div></span></a></td>
            <td width="110" class="issues"><a href="https://github.com/BYROBOT/drone1/issues/" target="_blank"><span class="even"><div align="center">Issues</div></span></a></td>
        </tr>
    </table>
    <br>
    <table>
        <!-- Documents -->
        <tr><td colspan="3" class="space"></td></tr>
        <tr>
            <td colspan="3" class="documents"><div align="center"><a name="Documents"></a>&nbsp;<br>Documents<br>&nbsp;</div></td>
        </tr>
        <!--
        <tr>
            <td class="documents"><div align="center">User Manual</div></td>
            <td colspan="2" class="white"><div align="center"><a href="/documents/kr/products/e_drone/manual/user/">한국어</a></div></td>
        </tr>
        -->
        <tr>
            <td class="documents"><div align="center">Protocol</div></td>
            <td colspan="2" class="white"><div align="center"><a href="/documents/kr/products/petrone/protocol/">한국어</a>,&nbsp;<a href="/documents/en/products/petrone/protocol/">English</a></div></td>
        </tr>
        <!-- Firmware -->
        <tr><td colspan="3" class="space"></td></tr>
        <tr>
            <td colspan="3" class="firmware"><div align="center"><a name="Firmware"></a>&nbsp;<br>Firmware<br>&nbsp;</div></td>
        </tr>
        <tr>
            <td rowspan="3" class="firmware"><div align="center">Version</div></td>
            <td class="white"><div align="center">Drone Main</div></td>
            <td class="white"><div align="center">51</div></td>
        </tr>
        <tr>
            <td class="firmware"><div align="center">Drone Sub</div></td>
            <td class="firmware"><div align="center">18</div></td>
        </tr>
        <tr>
            <td class="white"><div align="center">Link</div></td>
            <td class="white"><div align="center">17</div></td>
        </tr>
        <tr>
            <td class="firmware"><div align="center">Release Date</div></td>
            <td colspan="2" class="firmware"><div align="center">2019.2.27</div></td>
        </tr>
        <tr>
            <td class="firmware"><div align="center">Download</div></td>
            <td colspan="2" class="white"<div align="center"><a href="https://drive.google.com/open?id=1GkjdZaI1P0CaDn6RZDYJ9-ZNmt5Onkp-" target="_blank">Windows</a></div></td>
        </tr>
        <tr>
            <td class="firmware"><div align="center">Update Log</div></td>
            <td colspan="2" class="firmware"><div align="center"><a href="/documents/kr/products/petrone/log/updates/firmware/">한국어</a></div></td>
        </tr>
        <tr>
            <td class="firmware"><div align="center">Update Manual</div></td>
            <td colspan="2" class="white">
                <div align="center">
                    <a href="/documents/kr/products/petrone/manual/update/">한국어</a>
                </div>
            </td>
        </tr>
        <!-- Driver -->
        <tr><td colspan="3" class="space"></td></tr>
        <tr>
            <td colspan="3" class="driver"><div align="center"><a name="Driver"></a>&nbsp;<br>Driver<br>&nbsp;</div></td>
        </tr>
        <tr>
            <td class="driver">
                <div align="center">Download</div>
            </td>
            <td colspan="2" class="white">
                <div align="center"><a href="https://www.silabs.com/documents/public/software/CP210x_Windows_Drivers.zip" target="_blank">CP210x Windows Drivers<br>(for Petrone Link)</a></div>
            </td>
        </tr>
        <!-- Repository -->
        <tr><td colspan="3" class="space"></td></tr>
        <tr>
            <td colspan="3" class="repository"><div align="center"><a name="Repository"></a>&nbsp;<br>Repository<br>&nbsp;</div></td>
        </tr>
        <tr>
            <td class="repository"><div align="center">Android</div></td>
            <td colspan="2" class="white">
                <div align="center">
                    <a href="https://github.com/petrone/PetroneAPI_kotlin" target="_blank">PetroneAPI_kotlin</a>
                </div>
            </td>
        </tr>
        <tr>
            <td class="repository"><div align="center">iOS</div></td>
            <td colspan="2" class="repository">
                <div align="center">
                    <a href="https://github.com/petrone/PetroneAPI_swift" target="_blank">PetroneAPI_swift</a><br>
                    <a href="https://github.com/petrone/PetroneAPI_swift_Sample" target="_blank">PetroneAPI_swift_Sample</a>
                </div>
            </td>
        </tr>
        <!-- Python -->
        <tr><td colspan="3" class="space"></td></tr>
        <tr>
            <td colspan="3" class="python"><div align="center"><a name="Python"></a>&nbsp;<br>Python<br>&nbsp;</div></td>
        </tr>
        <tr>
            <td class="python"><div align="center">Library</div></td>
            <td colspan="2" class="white"><div align="center"><a href="https://pypi.org/project/petrone/" target="_blank">petrone</a></div></td>
        </tr>
        <tr>
            <td class="python"><div align="center">Version</div></td>
            <td colspan="2" class="python"><div align="center">0.1.58</div></td>
        </tr>
        <tr>
            <td class="python"><div align="center">Release Date</div></td>
            <td colspan="2" class="white"><div align="center">2019.3.14</div></td>
        </tr>
        <tr>
            <td class="python"><div align="center">Manual</div></td>
            <td colspan="2" class="python"><div align="center"><a href="/documents/kr/products/petrone/library/python/petrone/">한국어</a>,&nbsp;
                <a href="/documents/en/products/petrone/library/python/petrone/">English</a></div></td>
        </tr>
        <tr><td colspan="3" class="space"></td></tr>
    </table>
</div>

---

Modified : 2020.4.8
