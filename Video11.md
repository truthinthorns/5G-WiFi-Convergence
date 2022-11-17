<h2>Video 11</h2>
<h4>Resumes with VM powered off</h4>
<ul>
    <li>go to ubuntu (linked base) snapshots</li>
    <li>click the Clone button at the top</li>
    <ul>
        <li>change name to 'ueransim'</li>
        <li>change MAC Address Policy to 'Generate new MAC addresses for all network adapters'</li>
        <li>click Continue</li>
        <li>select 'Linked Clone'</li>
        <li>click Clone</li>
    </ul>
    <li>boot ueransim vm (u)</li>
    <ul>
        <li>log in</li>
    </ul>
    <li><i>ping google.com</i></li>
    <ul>
        <li>This should work.</li>
    </ul>
    <li><i>ifconfig</i></li>
    <ul>
        <li>confirm that results match video 11 results at 1:13</li>
    </ul>
    <li><i>sudo nano /etc/hostname</i></li>
    <ul>
        <li>change from 'ubuntu' to 'ueransim'</li>
        <li>save and exit</li>
    </ul>
    <li><i>sudo nano /etc/hosts</i></li>
    <ul>
        <li>change from '127.0.1.1 ubuntu' to '127.0.1.1 ueransim'</li>
        <li>save and exit</li>
    </ul>
    <li><i>cd /etc/netplan</i></li>
    <li><i>sudo nano 00-installer-config.yaml</i></li>
    <ul>
        <li>change from:</li>
        <ul>
            <li>enp0s8</li>
            <ul>
                <li>dhcp4: true</li>
            </ul>
        </ul>
        <li>to:</li>
        <ul>
            <li>enp0s8</li>
            <ul>
                <li>dhcp4: false</li>
                <li>addresses: [192.168.56.102/24]</li>
            </ul>
        </ul>
        <li>save and exit</li>
    </ul>
    <li><i>sudo netplan try</i></li>
    <ul>
        <li>should say 'Configuration accepted.'</li>
    </ul>
    <li><i>sudo netplan apply</i></li>
    <li><i>ifconfig</i></li>
    <ul>
        <li>confirm that 'inet 192.168.56.102' is under enp0s8</li>
    </ul>
    <li><i>sudo shutdown -r now</i></li>
    <li>boot free5gc vm concurrently with ueransim (f)</li>
    <li>start a terminal/cmd window as well (t)</li>
    <li>(t) <i>ssh 192.168.56.102 -l {username}</i></li>
    <li>(t) <i>ping 192.168.56.101</i></li>
    <li>(t) <i>ifconfig</i></li>
    <li>(t) <i>route -n</i></li>
</ul>
