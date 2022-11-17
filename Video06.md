<h2>Video 6</h2>
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
        <li>replace "ubuntu" with "free5gc"</li>
        <li>save file</li>
    </ul>
    <li><i>sudo nano /etc/hosts</i></li>
    <ul>
        <li>replace "127.0.1.1 ubuntu" with "127.0.1.1 free5gc"</li>
        <li>save file</li>
    </ul>
    <li><i>cd /etc/netplan</i></li>
    <li><i>ls</i></li>
    <ul>
        <li>there should be one file: "00-installer-config.yaml"</li>
    </ul>
    <li><i>sudo nano 00-installer-config.yaml</i></li>
    <ul>
        <li>replace "enp0s8: \n dhcp4: true" with "enp0s8: \n dhcp4: false"</li>
        <li>add line after "enp0s8: \n dhcp4: false" with same indentation (as the dhcp4 line) that says "addresses:
            [192.168.56.101/24]"</li>
        <li>save file</li>
    </ul>
    <li><i>sudo netplan try</i></li>
    <ul>
        <li>press ENTER to confirm</li>
        <li>Should say 'Configuration accepted'</li>
    </ul>
    <li><i>sudo netplan apply</i></li>
    <li><i>ifconfig</i></li>
    <ul>
        <li>under enp0s8, inet should now be '192.168.56.101'</li>
    </ul>
    <li>open cmd on host comp, outside of vm</li>
    <li><i>ssh 192.168.56.101 -l {your username} </i></li>
    <ul>
        <li>no brackets around username</li>
        <li>type "yes" to confirm connection</li>
        <li>enter password (no text will show, while typing password text is obscured)</li>
    </ul>
    <li>now should be ssh'ed into vm</li>
    <li><i>sudo shutdown -r now</i></li>
    <ul>
        <li>enter password (no text will show, while typing password text is obscured)</li>
        <li>this will restart the vm, stay on the separate host cmd</li>
        <li>wait until vm is fully restarted before running next command on host cmd</li>
    </ul>
    <li><i>ssh 192.168.56.101 -l {your username}</i></li>
    <ul>
        <li>no brackets around username</li>
        <li>type "yes" to confirm connection</li>
        <li>enter password (no text will show, while typing password text is obscured)</li>
    </ul>
    <li>now should be ssh'ed into vm</li>
</ul>
