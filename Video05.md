<h2>Video 5</h2>
<ul>
    <li>Start 'ubuntu' VM</li>
    <li><i>ping google.com</i></li>
    <ul>
        <li>This should work</li>
    </ul>
    <li><i>ifconfig</i></li>
    <ul>
        <li>note 'inet' address under 'enp0s8'</li>
    </ul>
    <li>Open a separate terminal/cmd window outside of the VM on your host machine</li>
    <li><i>ssh 192.168.56.104 -l {your username}</i></li>
    <ul>
        <li>This will access your VM from your host machine</li>
        <li>The ip address should match what was found when you ran 'ipconfig' on the vm</li>
    </ul>
    <li><i>ifconfig</i></li>
    <ul>
        <li>results should look the same as on the VM</li>
    </ul>
    <li><i>sudo apt update</i></li>
    <li><i>sudo apt upgrade</i></li>
    <li><i>sudo shutdown -P now</i></li>
</ul>
