<h1>Video 17</h1>
<h4>resumes where video 16 left off</h4>
<ul>
    <li><u>free5gc vm (f)</u></li>
    <li><u>ueransim vm (u)</u></li>
    <li><u>terminal/cmd window (t)</u></li>
    <li><u>terminal/cmd window (c)</u></li>
    <li><u>terminal/cmd window (L)</u></li>
    <li><u>terminal/cmd window (v)</u></li>
</ul>
<ul>
    <li>(v) <i>ifconfig</i></li>
    <li>(v) <i>ping google.com</i></li>
    <li>(v) <i>ping -I uesimtun0 google.com</i></li>
    <li>(v) <i>route -n</i></li>
    <li>(v) <i>sudo ifconfig enp0s3 down</i></li>
    <li>(v) <i>route -n</i></li>
    <li>(v) <i>ping 8.8.8.8</i></li>
    <li>(v) <i>ping -I uesimtun0 8.8.8.8</i></li>
    <li>(v) <i>sudo ip r add default dev uesimtun0</i></li>
    <li>(v) <i>route -n</i></li>
    <ul>
        <li>there should be a destination '0.0.0.0' with 'Iface': 'uesimtun0'</li>
    </ul>
    <li>(v) <i>ping 8.8.8.8</i></li>
    <li>(v) <i>ping google.com</i></li>
    <li>(v) <i>sudo nano /etc/resolv.conf</i></li>
    <ul>
        <li>change 'nameserver 127.0.0.53'</li>
        <li>to 'nameserver 8.8.8.8'</li>
        <li>save and exit</li>
    </ul>
    <li>(v) <i>ping google.com</i></li>
    <li>(v) <i>ifconfig</i></li>
    <ul>
        <li>under 'uesimtun0', note value for inet (x or 60.60.0.2)</li>
    </ul>
    <li>(v) <i>sudo tcpdump -n -i any host 60.60.0.2 or 192.168.56.101</i></li>
    <ul>
        <li>for 60.60.0.2 use whatever the previously noted value for inet was</li>
    </ul>
    <li>open a new terminal/cmd window, concurrently with the others (d)</li>
    <li>(d) <i>ssh 192.168.56.102 -l {username}</i></li>
    <li>(d) <i>ping 8.8.8.8</i></li>
    <li>verify outputs in (v) from last command match video results</li>
</ul>
