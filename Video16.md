<h1>Video 16</h1>
<h3>resumes with all vms powered off</h3>
<ul>
    <li>start free5gc vm (f)</li>
    <li>start ueransim vm (u)</li>
    <li>open a terminal/cmd window (t)</li>
    <li>(t) <i>ssh 192.168.56.101 -l {username}</i></li>
    -this should ssh into free5gc vm
    <li>(t) <i>sudo sysctl -w net.ipv4.ip_forward=1</i></li>
    <li>(t) <i>sudo iptables -t nat -A POSTROUTING -o enp0s3 -j MASQUERADE</i></li>
    <li>(t) <i>ifconfig</i></li>
    -verify under 'enp0s3' that 'inet' is '10.0.2.15'
    <li>(t) <i>sudo systemctl stop ufw</i></li>
    <li>(t) <i>sudo service ufw status</i></li>
    -verify 'Loaded: loaded'
    -verify 'Active: inactive (dead)'
    <li>(t) <i>sudo iptables -I FORWARD 1 -j ACCEPT</i></li>
    <li>(t) <i>sudo iptables -t nat -S</i></li>
    <ul>
        <li>verify</li>
        <ul>
            <li>"-P PREROUTING ACCEPT"</li>
            <li>"-P INPUT ACCEPT"</li>
            <li>"-P OUTPUT ACCEPT"</li>
            <li>"-P POSTROUTING ACCEPT"</li>
            <li>"-A POSTROUTING -o enp0s3 -j MASQUERADE"</li>
        </ul>
    </ul>
    <li>(t) <i>sudo iptables -S</i></li>
    <ul>
        <li>verify</li>
        <ul>
            <li>"-P INPUT ACCEPT"</li>
            <li>"-P FORWARD ACCEPT"</li>
            <li>"-P OUTPUT ACCEPT"</li>
            <li>"-A FORWARD -j ACCEPT"</li>
        </ul>
    </ul>
    <li>(t) <i>cd free5gc/</i></li>
    <li>(t) <i>git diff</i></li>
    <li>(t) <i>nano config/upfcfg.yaml</i></li>
    <ul>
        <li>save and exit</li>
    </ul>
    <li>(t) <i>./run.sh</i></li>
    <li>open a new terminal/cmd window concurrently with the other one (c)</li>
    <li>(c) <i>ssh 192.168.56.102 -l {username}</i></li>
    <li>(c) <i>cd UERANSIM/ </i></li>
    <li>(c) <i>ls</i></li>
    <li>(c) <i>git diff</i></li>
    <li>(c) <i>build/nr-gnb -c config/free5gc-gnb.yaml</i></li>
    <li>open a new terminal/cmd window concurrently with the other two (L)</li>
    <li>(L) <i>ssh 192.168.56.102 -l {username}</i></li>
    <li>(L) <i>cd UERANSIM/</i></li>
    <li>(L) <i>build/nr-ue -c config/free5gc-ue.yaml</i></li>
    <li>(L) <i>sudo build/nr-ue -c config/free5gc-ue.yaml</i></li>
    <li>open a new terminal/cmd window concurrently with the other three (v)</li>
    <li>(v) <i>ssh 192.168.56.102 -l {username}</i></li>
    <li>(v) <i>ifconfig</i></li>
    <ul>
        <li>there should be a uesimtun0 entry:</li>
    </ul>
    <li>(v) <i>ping google.com</i></li>
    <li>(v) <i>ping -I uesimtun0 google.com</i></li>
</ul>
