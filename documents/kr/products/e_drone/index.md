### E-Drone

---
<!-------------------------------------------------------------------------------------------------------

    2020.4.2

    각 index.md 파일 변경 시 사소한 링크 수정이나 펌웨어 업데이트 등은 직접 수정해도 상관없으나

    디자인 변경, 테이블 구조 변경 등의 작업을 하게 되는 경우, nightly.md 파일에서 먼저 작업을 할 것.

    git에 올려 화면이 정상적으로 표시되는지를 확인하고, index.md 파일을 변경하는 것을 권장함

-------------------------------------------------------------------------------------------------------->

<style>

    td.documents { background: #EEFAFA !important; }
    td.firmware  { background: #FFF9FA !important; }
    td.driver    { background: #F7FFF7 !important; }
    td.entry     { background: #FEF3FE !important; }
    td.byblocks  { background: #F5FAFF !important; }
    td.python    { background: #FFFEF5 !important; }
    td.rust      { background: #E1F7EE !important; }
    td.issues    { background: #FEF8EA !important; }
    td.byrobot   { background: #FAFEFE !important; }
    td.white     { background: #FFFFFF !important; }
    td.space     { background: #FFFFFF !important; }

    span.odd       { color: #0489B1; }
    span.even      { color: #FF4000; }
    span.byrobot   { color: #CCDDEE; }

</style>

<div align="center">
    <img src="/assets/images/products/byrobot_drone_4.png" alt="e_drone">
    <table style="padding: 0px 0px 0px 0px;">
        <tr>
            <td width="110" class="documents"><div align="center">&nbsp;<br><a href="#Documents"><span class="odd">Documents</span></a><br>&nbsp;</div></td>
            <td width="110" class="firmware"><div align="center">&nbsp;<br><a href="#Firmware"><span class="even">Firmware</span></a><br>&nbsp;</div></td>
            <td width="110" class="driver"><div align="center">&nbsp;<br><a href="#Driver"><span class="odd">Driver</span></a><br>&nbsp;</div></td>
        </tr>
        <tr>
            <td width="110" class="entry"><div align="center">&nbsp;<br><a href="#Entry"><span class="even">Entry</span></a><br>&nbsp;</div></td>
            <td width="110" class="byblocks"><div align="center">&nbsp;<br><a href="#ByBlocks"><span class="odd">ByBlocks</span></a><br>&nbsp;</div></td>
            <td width="110" class="python"><div align="center">&nbsp;<br><a href="#Python"><span class="even">Python</span></a><br>&nbsp;</div></td>
        </tr>
        <tr>
            <td width="110" class="rust"><div align="center">&nbsp;<br><a href="#Rust"><span class="odd">Rust</span></a><br>&nbsp;</div></td>
            <td width="110" class="issues"><div align="center">&nbsp;<br><a href="https://github.com/BYROBOT/drone4/issues/" target="_blank"><span class="even">Issues</span></a><br>&nbsp;</div></td>
            <td width="110" class="byrobot"><div align="center">&nbsp;<br><span class="byrobot">BYROBOT</span><br>&nbsp;</div></td>
        </tr>
    </table>
    <br>
    <table>
        <!-- Documents -->
        <tr><td colspan="3" class="space"></td></tr>
        <tr>
            <td colspan="3" class="documents"><div align="center"><a name="Documents"></a>&nbsp;<br>Documents<br>&nbsp;</div></td>
        </tr>
        <tr>
            <td class="documents"><div align="center">User Manual</div></td>
            <td colspan="2" class="white"><div align="center"><a href="/documents/kr/products/e_drone/manual/user/">한국어</a></div></td>
        </tr>
        <tr>
            <td class="documents"><div align="center">Protocol</div></td>
            <td colspan="2" class="documents"><div align="center"><a href="/documents/kr/products/e_drone/protocol/">한국어</a></div></td>
        </tr>
        <!-- Firmware -->
        <tr><td colspan="3" class="space"></td></tr>
        <tr>
            <td colspan="3" class="firmware"><div align="center"><a name="Firmware"></a>&nbsp;<br>Firmware<br>&nbsp;</div></td>
        </tr>
        <tr>
            <td rowspan="3" class="firmware"><div align="center">Version</div></td>
            <td class="white"><div align="center">Drone</div></td>
            <td class="white"><div align="center">21.8.1</div></td>
        </tr>
        <tr>
            <td class="firmware"><div align="center">Drone(4m)</div></td>
            <td class="firmware"><div align="center">21.8.1</div></td>
        </tr>
        <tr>
            <td class="white"><div align="center">Controller</div></td>
            <td class="white"><div align="center">21.8.1</div></td>
        </tr>
        <tr>
            <td class="firmware"><div align="center">Release Date</div></td>
            <td colspan="2" class="firmware"><div align="center">2021.8.3</div></td>
        </tr>
        <tr>
            <td class="firmware"><div align="center">Update Log</div></td>
            <td colspan="2" class="white"><div align="center"><a href="/documents/kr/products/e_drone/log/updates/firmware/">한국어</a></div></td>
        </tr>
        <tr>
            <td class="firmware"><div align="center">Download</div></td>
            <td colspan="2" class="firmware"><div align="center">
                <a href="https://drive.google.com/file/d/1KAM4_VVC3r3njiZWqNGQ5YS_thLdAagm/view?usp=sharing" target="_blank">Windows (.NET)</a><br>
                <!--<a href="https://drive.google.com/file/d/1RFG2SBWmF84eiqO5YY4nKH3gXxh3Ig_u/view?usp=sharing" target="_blank">Windows</a><br>-->
                <a href="https://drive.google.com/file/d/1EzNCLJ6S7frO-VCze8TTPZFVV6VUnDh4/view?usp=sharing" target="_blank">macOS</a><br>
                <a href="https://drive.google.com/file/d/1RYV3_oNA98mjYOfOGvCiqp3f0IINW1Gp/view?usp=sharing" target="_blank">Linux</a><br>
                <a href="https://drive.google.com/file/d/1vjvUrJ5ivZvjWTcA6LgsrnfUqGMug6Ir/view?usp=sharing" target="_blank">Raspberry PI</a>
            </div></td>
        </tr>
        <tr>
            <td rowspan="2" class="firmware"><div align="center">Update Manual</div></td>
            <td class="white">
                <div align="center">GUI</div>
            </td>
            <td class="white">
                <div align="center">Terminal</div>
            </td>
        </tr>
        <tr>
            <td class="firmware">
                <div align="center">
                    <a href="/documents/kr/products/e_drone/manual/update/drone4autoupdaterlight/">Windows (.NET)</a><br>
                    <!--<a href="/documents/kr/products/e_drone/manual/update/drone_4_updater_windows/">Windows</a><br>-->
                    <a href="/documents/kr/products/e_drone/manual/update/drone_4_updater_mac/">macOS</a><br>
                    <a href="/documents/kr/products/e_drone/manual/update/drone_4_updater_linux/">Linux</a><br>
                    <a href="/documents/kr/products/e_drone/manual/update/drone_4_updater_raspberry_pi/">Raspberry PI</a>
                </div>
            </td>
            <td class="firmware">
                <div align="center">
                    &nbsp;<br>
                    <!--<a href="/documents/kr/products/e_drone/manual/update/drone_4_updater_cli_windows/">Windows</a><br>-->
                    <a href="/documents/kr/products/e_drone/manual/update/drone_4_updater_cli_mac/">macOS</a><br>
                    <a href="/documents/kr/products/e_drone/manual/update/drone_4_updater_cli_linux/">Linux</a><br>
                    <a href="/documents/kr/products/e_drone/manual/update/drone_4_updater_cli_raspberry_pi/">Raspberry PI</a>
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
                <div align="center"><a href="https://drive.google.com/open?id=1HisAPi3nipnnyuFklNXiKn46cV_5P0iy" target="_blank">Win7, Win8 (32bit)</a></div>
                <div align="center"><a href="https://drive.google.com/open?id=1Cm7fIt9XAi-dUNnqxVblNriL8oVfqekg" target="_blank">Win7, Win8 (64bit)</a></div>
                <div align="center"><a href="https://drive.google.com/open?id=1G6ma1HbzNSPqTcU9ir1I4lyYLobLM4K-" target="_blank">Win7, Win8 (new)</a></div>
                <div align="center">Win 10은 자동 인식</div>
            </td>
        </tr>
        <!-- Entry -->
        <tr><td colspan="3" class="space"></td></tr>
        <tr>
            <td colspan="3" class="entry"><div align="center"><a name="Entry"></a>&nbsp;<br>Entry<br>&nbsp;</div></td>
        </tr>
        <tr>
            <td class="entry"><div align="center">Homepage</div></td>
            <td colspan="2" class="white"><div align="center"><a href="https://playentry.org/" target="_blank">Entry</a></div></td>
        </tr>
        <tr>
            <td class="entry"><div align="center">Download</div></td>
            <td colspan="2" class="entry"><div align="center"><a href="https://playentry.org/#!/offlineEditor" target="_blank">Entry Offline</a></div></td>
        </tr>
        <!-- ByBlocks -->
        <tr><td colspan="3" class="white"></td></tr>
        <tr>
            <td colspan="3" class="byblocks"><div align="center"><a name="ByBlocks"></a>&nbsp;<br>ByBlocks<br>&nbsp;</div></td>
        </tr>
        <tr>
            <td class="byblocks"><div align="center">Version</div></td>
            <td colspan="2" class="white"><div align="center">1.0.19</div></td>
        </tr>
        <tr>
            <td class="byblocks"><div align="center">Release Date</div></td>
            <td colspan="2" class="byblocks"><div align="center">2019.2.28</div></td>
        </tr>
        <tr>
            <td class="byblocks">
                <div align="center">Download</div>
            </td>
            <td colspan="2" class="white">
                <div align="center"><a href="https://s3.ap-northeast-2.amazonaws.com/byrobot/byblocks-edrone_1.0.19.apk" target="_blank">Android (4.4 이상)</a></div>
            </td>
        </tr>
        <tr>
            <td class="byblocks"><div align="center">Update Log</div></td>
            <td colspan="2" class="byblocks"><div align="center"><a href="/documents/kr/products/e_drone/log/updates/byblocks/">한국어</a></div></td>
        </tr>
        <!-- Python -->
        <tr><td colspan="3" class="space"></td></tr>
        <tr>
            <td colspan="3" class="python"><div align="center"><a name="Python"></a>&nbsp;<br>Python<br>&nbsp;</div></td>
        </tr>
        <tr>
            <td class="python"><div align="center">Library</div></td>
            <td colspan="2" class="white"><div align="center"><a href="https://pypi.org/project/e-drone/" target="_blank">e_drone</a></div></td>
        </tr>
        <tr>
            <td class="python"><div align="center">Version</div></td>
            <td colspan="2" class="python"><div align="center">21.1.6</div></td>
        </tr>
        <tr>
            <td class="python"><div align="center">Release Date</div></td>
            <td colspan="2" class="white"><div align="center">2021.1.5</div></td>
        </tr>
        <tr>
            <td class="python"><div align="center">Manual</div></td>
            <td colspan="2" class="python"><div align="center"><a href="/documents/kr/products/e_drone/library/python/e_drone/">한국어</a></div></td>
        </tr>
        <tr>
            <td class="python"><div align="center">Update Log</div></td>
            <td colspan="2" class="white"><div align="center"><a href="/documents/kr/products/e_drone/log/updates/python/">한국어</a></div></td>
        </tr>
        <tr><td colspan="3" class="space"></td></tr>
        <!-- Rust -->
        <tr>
            <td colspan="3" class="rust"><div align="center"><a name="Rust"></a>&nbsp;<br>Rust<br>&nbsp;</div></td>
        </tr>
        <tr>
            <td rowspan="3" class="rust"><div align="center">Library</div></td>
            <td class="white"><div align="center">Core</div></td>
            <td class="white"><div align="center"><a href="https://crates.io/crates/e_drone" target="_blank">e_drone</a></div></td>
        </tr>
        <tr>
            <td class="rust"><div align="center">
                Windows 10<br>
                macOS<br>
                Linux<br>
                Raspberry Pi OS
            </div></td>
            <td class="rust"><div align="center"><a href="https://crates.io/crates/e_drone_sp" target="_blank">e_drone_sp</a></div></td>
        </tr>
        <tr>
            <td class="white"><div align="center">Raspberry PI OS</div></td>
            <td class="white"><div align="center"><a href="https://crates.io/crates/e_drone_rpi" target="_blank">e_drone_rpi</a></div></td>
        </tr>
        <tr>
            <td class="rust"><div align="center">Version</div></td>
            <td colspan="2" class="rust"><div align="center">21.7.2</div></td>
        </tr>
        <tr>
            <td class="rust"><div align="center">Release Date</div></td>
            <td colspan="2" class="white"><div align="center">2021.7.28</div></td>
        </tr>
        <tr>
            <td class="rust"><div align="center">Manual</div></td>
            <td colspan="2" class="rust"><div align="center"><a href="https://docs.rs/e_drone/" target="_blank">한국어</a></div></td>
        </tr>
        <tr>
            <td class="rust"><div align="center">Repository</div></td>
            <td colspan="2" class="white"><div align="center"><a href="https://github.com/byrobot-rust/e_drone" target="_blank">github</a></div></td>
        </tr>
        <!-- End -->
        <tr><td colspan="3" class="space"></td></tr>
    </table>
</div>

---

Modified : 2021.8.3
