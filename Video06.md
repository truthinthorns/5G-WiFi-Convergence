<h1>Video 6</h1>
<ul>
    <li>In VirtualBox, right click original ubuntu vm</li>
    <ul>
        <li>Select snapshots</li>
    </ul>
    <li>Click clone at the top</li>
    <ul>
        <li>Change name to free5gc</li>
        <li>Change MAC Address Policy to "Generate new MAC addresses for all network adapters"</li>
        <li>Click Next</li>
        <li>Select Linked clone</li>
        <li>Click Finish</li>
    </ul>
    <li>Start the new free5gc VM</li>
    <ul>
        <li>Log in</li>
    </ul>
    <li><i>ping google.com</i></li>
    <li><i>ifconfig</i></li>
    <li><i>sudo nano /etc/hostname</i></li>
    <ul>
        <li>Replace "ubuntu" with "free5gc"</li>
        <li>Save file</li>
    </ul>
    <li><i>sudo nano /etc/hosts</i></li>
    <ul>
        <li>Replace "127.0.1.1 ubuntu" with "127.0.1.1 free5gc"</li>
        <li>Save file</li>
    </ul>
    <li><i>cd /etc/netplan</i></li>
    <li><i>ls</i></li>
    <ul>
        <li>There should be one file: "00-installer-config.yaml"</li>
    </ul>
    <li><i>sudo nano 00-installer-config.yaml</i></li>
    <ul>
        <li>Replace "enp0s8: \n dhcp4: true" with "enp0s8: \n dhcp4: false"</li>
        <li>Add line after "enp0s8: \n dhcp4: false" with same indentation (as the dhcp4 line) that says "addresses:
            [192.168.56.101/24]"</li>
        <li>Save file</li>
    </ul>
    <li>If you don't see "00-installer-config.yaml", run <i>sudo nano 00-installer-config.yaml</i></li>
    <ul>
        <li>network:<br>
            (tab)ethernets:<br>
            (tab tab)enp0s3:<br>
            (tab tab tab)dhcp: true<br>
            (tab tab)enp0s8:<br>
            (tab tab tab)dhcp4: false<br>
            (tab tab tab)addresses: [192.168.56.101/24]<br>
            (tab)version: 2
        </li>
    </ul>
    <li><i>sudo netplan try</i></li>
    <ul>
        <li>Press ENTER to confirm</li>
        <li>Should say 'Configuration accepted'</li>
    </ul>
    <li><i>sudo netplan apply</i></li>
    <li><i>ifconfig</i></li>
    <ul>
        <li>Under enp0s8, inet should now be '192.168.56.101'</li>
    </ul>
    <li>Open cmd on host comp, outside of vm</li>
    <li><i>ssh 192.168.56.101 -l {your username} </i></li>
    <ul>
        <li>No brackets around username</li>
        <li>Type "yes" to confirm connection</li>
        <li>Enter password (no text will show, while typing password text is obscured)</li>
    </ul>
    <li>Now should be ssh'ed into vm</li>
    <li><i>sudo shutdown -r now</i></li>
    <ul>
        <li>Enter password (no text will show, while typing password text is obscured)</li>
        <li>This will restart the vm, stay on the separate host cmd</li>
        <li>Wait until vm is fully restarted before running next command on host cmd</li>
    </ul>
    <li><i>ssh 192.168.56.101 -l {your username}</i></li>
    <ul>
        <li>No brackets around username</li>
        <li>Type "yes" to confirm connection</li>
        <li>Enter password (no text will show, while typing password text is obscured)</li>
    </ul>
    <li>Now should be ssh'ed into vm</li>
</ul>
