<h1>Video 18</h1>
<h4>resumes where video 17 left off</h4>
<ul>
    <li><u>free5gc vm (f)</u></li>
    <li><u>ueransim vm (u)</u></li>
    <li><u>terminal/cmd window (t)</u></li>
    <li><u>terminal/cmd window (c)</u></li>
    <li><u>terminal/cmd window (L)</u></li>
    <li><u>terminal/cmd window (v)</u></li>
    <li><u>terminal/cmd window (d)</u></li>
</ul>
<ul>
    <li>(v) <i>ifconfig</i></li>
    <li>(v) <i>route -n</i></li>
    <li>(v) <i>wget https://golang.org/dl/go1.15.8.linux-amd64.tar.gz</i></li>
    <li>(v) <i>ls</i></li>
    <li>(v) <i>curl https://golang.org/dl/go1.15.8.linux-amd64.tar.gz</i></li>
    <ul>
        <li>should result in link under 'a href=' {prevlink}</li>
    </ul>
    <li>(v) <i>curl {prevlink}</i></li>
    <li>(v) <i>curl {prevlink} --output file.tar.gz</i></li>
    <li>(v) <i>ls</i></li>
    <li>(v) <i>diff file.tar.gz go1.15.8.linux-amd64.tar.gz</i></li>
    <li>(v) <i>sudo nano /etc/resolv.conf</i></li>
    <ul>
        <li>change 'nameserver 8.8.8.8'</li>
        <li>to 'nameserver 127.0.0.53'</li>
        <li>save and exit</li>
    </ul>
    <li>(v) <i>curl {prevlink} --output file.tar.gz</i></li>
    <li>(v) <i>wget https://golang.org/dl/go1.15.8.linux-amd64.tar.gz</i></li>
</ul>