<h2>Video 8</h2>
<h4>Resumes within host computer cmd ssh'ed to vm immediately after last command in video 7, vm should not have been
    closed between vid 7 and 8</h4>
<ul>
    <li><i>sudo sysctl -w net.ipv4.ip_forward=1</i></li>
    <ul>
        <li>result should be "net.ipv4.ip_forward = 1"</li>
    </ul>
    <li><i>sudo iptables -t nat -A POSTROUTING -o enp0s3 -j MASQUERADE</i></li>
    <li><i>sudo systemctl stop ufw</i></li>
    <li><i>sudo service ufw status</i></li>
    <ul>
        <li>results should be as follows</li>
        <li>"Loaded: loaded (/lib/systemd/system/ufw.service; enabled; vendor preset: enabled)...</li>
        <li>"Active: inactive (dead) since..."</li>
    </ul>
    <li><i>sudo iptables -t nat -S</i></li>
    <ul>
        <li>results should be as follows</li>
        <ul>
            <li>"-P PREROUTING ACCEPT"</li>
            <li>"-P INPUT ACCEPT"</li>
            <li>"-P OUTPUT ACCEPT"</li>
            <li>"-P POSTROUTING ACCEPT"</li>
            <li>"-A POSTROUTING -o enp0s3 -j MASQUERADE"</li>
        </ul>
    </ul>
    <li><i>ifconfig</i></li>
    <ul>
        <li>enp0s3 "inet" should be "10.0.2.15"</li>
    </ul>
</ul>
