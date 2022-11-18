<h1>Video 11</h1>
<h3>Resumes with VM powered off</h3>
<ul>
    <li>Go to ubuntu (linked base) snapshots</li>
    <li>Click the Clone button at the top</li>
    <ul>
        <li>Change name to 'ueransim'</li>
        <li>Change MAC Address Policy to 'Generate new MAC addresses for all network adapters'</li>
        <li>Click Continue</li>
        <li>Select 'Linked Clone'</li>
        <li>Click Clone</li>
    </ul>
    <li>Boot ueransim vm (u)</li>
    <ul>
        <li>Log in</li>
    </ul>
    <li><i>ping google.com</i></li>
    <ul>
        <li>This should work.</li>
    </ul>
    <li><i>ifconfig</i></li>
    <ul>
        <li>Confirm that results match video 11 results at 1:13</li>
    </ul>
    <li><i>sudo nano /etc/hostname</i></li>
    <ul>
        <li>Change from 'ubuntu' to 'ueransim'</li>
        <li>Save and exit</li>
    </ul>
    <li><i>sudo nano /etc/hosts</i></li>
    <ul>
        <li>Change from '127.0.1.1 ubuntu' to '127.0.1.1 ueransim'</li>
        <li>Save and exit</li>
    </ul>
    <li><i>cd /etc/netplan</i></li>
    <li><i>sudo nano 00-installer-config.yaml</i></li>
    <ul>
        <li>Change from:</li>
        <ul>
            <li>enp0s8</li>
            <ul>
                <li>dhcp4: true</li>
            </ul>
        </ul>
        <li>To:</li>
        <ul>
            <li>enp0s8</li>
            <ul>
                <li>dhcp4: false</li>
                <li>addresses: [192.168.56.102/24]</li>
            </ul>
        </ul>
        <li>Save and exit</li>
    </ul>
    <li><i>sudo netplan try</i></li>
    <ul>
        <li>It should say 'Configuration accepted.'</li>
    </ul>
    <li><i>sudo netplan apply</i></li>
    <li><i>ifconfig</i></li>
    <ul>
        <li>Confirm that 'inet 192.168.56.102' is under enp0s8</li>
    </ul>
    <li><i>sudo shutdown -r now</i></li>
    <li>Boot free5gc vm concurrently with ueransim (f)</li>
    <li>Start a terminal/cmd window as well (t)</li>
    <li>(t) <i>ssh 192.168.56.102 -l {username}</i></li>
    <li>(t) <i>ping 192.168.56.101</i></li>
    <li>(t) <i>ifconfig</i></li>
    <li>(t) <i>route -n</i></li>
</ul>
