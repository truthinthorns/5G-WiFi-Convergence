<h1>Video 15</h1>
<h3>resumes with where video 14 left off</h3>
<h3>both free5gc (f) and ueransim (u) vms are running</h3>
<ul>
    <li>open a terminal/cmd window (t)</li>
    <li>(t) <i>ssh 192.168.56.101 -l {username}</i></li>
    <li>(t) <i>cd ~/free5gc/config</i></li>
    <li>(t) <i>ls</i></li>
    <li>(t) <i>nano amfcfg.yaml</i></li>
    <ul>
        <li>change from:</li>
        <ul>
            <li>configuration:</li>
            <ul>
                <li>...</li>
                <li>ngapIpList: #...</li>
                <ul>
                    <li>- 127.0.0.1</li>
                </ul>
            </ul>
        </ul>
        <li>to:</li>
        <ul>
            <li>configuration</li>
            <ul>
                <li>...</li>
                <li>ngapIpList: #...</li>
                <ul>
                    <li>- 192.168.56.101 # 127.0.0.1</li>
                </ul>
            </ul>
        </ul>
        <li>save and exit</li>
    </ul>
    <li>(t) <i>nano smfcfg.yaml</i></li>
    <ul>
        <li>scroll down to</li>
        <ul>
            <li>configuration:</li>
            <ul>
                <li>...</li>
                <li>userplane_information:</li>
                <ul>
                    <li>...</li>
                    <li>interfaces</li>
                    <li>...</li>
                    <li>endpoints:</li>
                    <ul>
                        <li>- 127.0.0.8</li>
                    </ul>
                </ul>
            </ul>
        </ul>
        <li>replace the endpoint with:</li>
        <ul>
            <li>- 192.168.56.101 # 127.0.0.8</li>
        </ul>
        <li>save and exit</li>
    </ul>
    <li>(t) <i>nano upfcfg.yaml</i></li>
    <ul>
        <li>change '- addr: 127.0.0.8' under</li>
        <ul>
            <li>gtpu:</li>
            <ul>
                <li>ifList:</li>
            </ul>
        </ul>
        <li>to '- addr: 192.168.56.101 # 127.0.0.8'</li>
        <li>save and exit</li>
    </ul>
    <li>(t) <i>cd ..</i></li>
    <li>(t) <i>git status</i></li>
    <li>(t) <i>git diff</i></li>
    <ul>
        <li>open a new terminal/cmd window (c)</li>
    </ul>
    <li>(c) <i>ssh 192.168.56.102 -l {username}</i></li>
    <ul>
        <li>this is sshing into the ueransim vm</li>
    </ul>
    <li>(c) <i>cd UERANSIM/</i></li>
    <li>(c) <i>ls</i></li>
    <li>(c) <i>cd config</i></li>
    <li>(c) <i>ls</i></li>
    <li>(c) <i>nano free5gc-gnb.yaml</i></li>
    <ul>
        <li>change 'ngapIp: 127.0.0.1'</li>
        <li>to 'ngapIp: 192.168.56.102 # 127.0.0.1'</li>
        <li>change 'gtpIp: 127.0.0.1'</li>
        <li>to 'gtpIp: 192.168.56.102 # 127.0.0.1'</li>
        <li>change:</li>
        <ul>
            <li>amfConfigs:</li>
            <ul>
                <li>- address: 127.0.0.1</li>
            </ul>
        </ul>
        <li>to</li>
        <li>amfConfigs:</li>
        <ul>
            <li>- address: 192.168.56.101 # 127.0.0.1</li>
        </ul>
        <li>save and exit</li>
    </ul>
    <li>(c) <i>nano free5gc-ue.yaml</i></li>
    <ul>
        <li>verify values match subscriber setup on webconsole from previous video</li>
        <li>verify OP Type is set to 'OP' and not 'OPc'</li>
    </ul>
    <li>(c) <i>cd ..</i></li>
    <li>(c) <i>git diff</i></li>
</ul>
