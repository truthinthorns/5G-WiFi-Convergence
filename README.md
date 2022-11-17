# 5G-WiFi-Convergence
<h2>Prerequisites</h2>
<ul>
    <li>Have either the Server (Command Line) or Desktop (GUI) version of Ubuntu 22.04</li>
    <ul>
        <li>Server: https://ubuntu.com/download/server</li>
        <li>Dekstop: https://ubuntu.com/download/desktop</li>
    </ul>
    <li>Have VirtualBox 7.0</li>
    <ul>
        <li>https://www.virtualbox.org/</li>
    </ul>
    <li>Ensure Virtualization is enabled in your host computer's UEFI/BIOS.</li>
    <ul>
        <li>Steps to do this vary based on motherboard.</li>
    </ul>
</ul>

<h2>Video 1</h2>
<ul>
    <li>Open Oracle VM VirtualBox</li>
    <li>Click 'New' at the top</li>
    <li>Set the Name: as 'ubuntu'</li>
    <li>Set the Type: as 'Linux'</li>
    <li>Set the Version: as 'Ubuntu (64-bit)'</li>
    <li>Click 'Next'</li>
    <li>Select 8192 MB for Base Memory</li>
    <li>Allocate 4 CPUs for Processors</li>
    <li>Click 'Next'</li>
    <li>Select 'Create a virtual hard disk now'</li>
    <li>Allocate 40 GB of storage for Disk Size</li>
    <li>Click 'Next'</li>
    <li>Click 'Finish'</li>
</ul>

<h2>Video 2</h2>
<ul>
    <li>Select 'ubuntu' VM on the left</li>
    <li>Click 'Settings' at the top</li>
    <li>Click 'Storage'</li>
    <li>On the left, under storage devices, to the right of 'Controller: IDE' click the circular button that says 'Adds
        optical drive'</li>
    <li>Click 'Add'</li>
    <li>Select your ubuntu .iso file from the pre-video setup instructions</li>
    <li>Click 'Open'</li>
    <li>Select your newly added .iso file, and click 'Choose'</li>
    <li>Click 'Network'</li>
    <li>Click 'Adapter 2' under 'Network'</li>
    <li>Click 'Enable Network Adapter'</li>
    <li>Under 'Attached to' select 'Host-only Adapter'</li>
    <li>Click 'OK'</li>
</ul>

<h2>Video 3</h2>
<ul>
    <li>Start the 'ubuntu' VM</li>
    <li>Select 'Try or Install Ubuntu Server'</li>
    <li>Select 'English'</li>
    <li>Select 'Continue without updating'</li>
    <li>Select 'Done' for Keyboard Configuration</li>
    <li>Select 'Ubuntu Server' then select 'Done' for Choose type of install</li>
    <li>Select 'Done' for Network connections</li>
    <li>Select 'Done' for Configure proxy</li>
    <li>Select 'Done' for Configure Ubuntu Archive Mirror</li>
    <li>Under Guided storage configuration, disable 'Set up this disk as an LVM group'</li>
    <li>Select 'Done' for Guided storage configuration</li>
    <li>Select 'Done' for Storage configuration</li>
    <li>Select 'Continue'</li>
    <li>Set 'Your name:' as ubuntu</li>
    <li>Set 'Your server's name:' as ubuntu</li>
    <li>Set 'Pick a username:' to your preferred username</li>
    <li>Set 'Choose a password:' to your preferred password</li>
    <li>Set 'Confirm your password:' to your preferred password </li>
    <li>Select 'Done' for Profile setup</li>
    <li>Enable 'Install OpenSSH server'</li>
    <li>Select 'Done' for SSH Setup</li>
    <li>Select 'Done' for Featured Server Snaps</li>
</ul>

<h2>Video 4</h2>
<h4>Resumes where Video 3 left off</h4>
<ul>
    <li>VirtualBox open, ubuntu VM running</li>
    <li>ubuntu Install complete!</li>
    <li>Select 'Reboot Now'</li>
    <li>Press ENTER</li>
    <li>Log in to ubuntu VM </li>
    <li><i>ping google.com</i></li>
    <ul>
        <li>This should work</li>
    </ul>
    <li><i>sudo apt install net-tools</i></li>
    <li><i>ifconfig</i></li>
    <ul>
        <li>This should work</li>
    </ul>
    <li>Shutdown ubuntu VM</li>
</ul>

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

<h2>Video 7</h2>
<ul>
    <li>start free5gc vm through virtualbox</li>
    <li>open a cmd on the host computer outside of the vm</li>
    <li><i>ssh 192.168.56.101 -l {your username}</i></li>
    <ul>
        <li>no brackets around username</li>
        <li>type "yes" to confirm connection</li>
        <li>enter password (no text will show, while typing password text is obscured)</li>
    </ul>
    <li>should now be ssh'ed into vm on the host computer's cmd</li>
    <li><i>uname -r</i></li>
    <ul>
        <li>result in video says: "5.4.0-65-generic"</li>
        <li>result says '5.15.0-52-generic'</li>
    </ul>
    <li><i>go version</i></li>
    <ul>
        <li>result in video says: "Command 'go' not found, ... "</li>
    </ul>
    <li>open a web browser, and proceed to https://golang.org/dl/</li>
    <ul>
        <li>under featured downloads, there should be a Linux download link titled "go1.19.1.linux-amd64.tar.gz"</li>
        <li>right click the link, and select "Copy Link Location"</li>
    </ul>
    <li>navigate back to the host computer cmd which is ssh'ed into the vm</li>
    <li><i>wget {copied link from browser}</i></li>
    <ul>
        <li>could type out link as well (w/o brackets):</li>
        <li>{https://golang.org/dl/go1.19.1.linux-amd64.tar.gz}</li>
    </ul>
    <li><i>ls</i></li>
    <ul>
        <li>there should be one file:</li>
        <ul>
            <li>go1.19.1.linux-amd64.tar.gz</li>
        </ul>
    </ul>
    <li><i>sudo tar -C /usr/local -xzf go1.19.1.linux-amd64.tar.gz</i></li>
    <li><i>mkdir -p ~/go/{bin,pkg,src}</i></li>
    <li><i>echo 'export GOPATH=$HOME/go' >> ~/.bashrc</i></li>
    <li><i>echo 'export GOROOT=/usr/local/go' >> ~/.bashrc</i></li>
    <li><i>echo 'export PATH=$PATH:$GOPATH/bin:$GOROOT/bin' >> ~/.bashrc</i></li>
    <li><i>echo 'export GO111MODULE=auto' >> ~/.bashrc</i></li>
    <li><i>source ~/.bashrc</i></li>
    <li><i>go version</i></li>
    <ul>
        <li>should say "go version go1.19.1 linux/amd64"</li>
    </ul>
    <li><i>sudo apt -y update</i></li>
    <li><i>sudo apt update</i></li>
    <li><i>sudo apt install wget curl gnupg2 software-properties-common apt-transport-https ca-certificates
            lsb-release</i></li>
    <li><i>curl -fsSL https://www.mongodb.org/static/pgp/server-6.0.asc|sudo gpg --dearmor -o
            /etc/apt/trusted.gpg.d/mongodb-6.gpg</i></li>
    <li><i>echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/6.0 multiverse" | sudo
            tee /etc/apt/sources.list.d/mongodb-org-6.0.list</i></li>
    <li><i>wget http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.1_1.1.1f-1ubuntu2.16_amd64.deb</i></li>
    <li><i>sudo dpkg -i ./libssl1.1_1.1.1f-1ubuntu2.16_amd64.deb</i></li>
    <li><i>sudo apt update</i></li>
    <li><i>sudo apt install mongodb-org</i></li>
    <li><i>sudo systemctl start mongod</i></li>
    <li><i>mongosh</i></li>
    <ul>
        <li>opens the MongoDB shell</li>
    </ul>
    <li><i>exit</i></li>
    <ul>
        <li>exits the MongoDB shell, returning to normal VM terminal</li>
    </ul>
    <li><i>sudo apt -y install git gcc g++ cmake autoconf libtool pkg-config libmnl-dev libyaml-dev</i></li>
    <li><i>go get -u github.com/sirupsen/logrus </i></li>
</ul>

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

<h2>Video 9</h2>
<h4>resumes within host computer cmd ssh'ed to vm</h4>
<ul>
    <li><b><u>Make sure that every time the vm is started from this point onwards, run ip routing config commands from
                video 8</u></b></li>
    <ul>
        <li>Link to bash file for routing commands: </li>
    </ul>
    <li><i>git clone --recursive https://github.com/free5gc/free5gc.git</i></li>
    <li><i>cd free5gc</i></li>
    <li><i>make</i></li>
    <li><i>cd ~</i></li>
    <li><i>git clone https://github.com/free5gc/gtp5g.git</i></li>
    <li><i>cd gtp5g/</i></li>
    <li><i>make</i></li>
    <li><i>sudo make install</i></li>
    <li><i>lsmod | grep gtp</i></li>
</ul>

<h2>Video 10</h2>
<h4>Resumes within host computer cmd ssh'ed to vm immediately after last command in video 9, vm should not have been
    closed between vid 9 and 10</h4>
<ul>
    <li><b><u>make sure to run ip routing config commands from video 8, if a restart did occur between vid 9 &
                10</u></b></li>
    <li><b><u>make sure to run sudo systemctl enable --now mongod, if a restart did occur between vid 9 & 10</u></b>
    </li>
    <li><i>cd ~</i></li>
    <li><i>cd free5gc/</i></li>
    <li><i>./test.sh TestDeregistration > ~/TestDeregistration.txt</i></li>
    <li><i>./test.sh TestDuplicateRegistration > ~/TestDuplicateRegistration.txt</i></li>
    <li><i>./test.sh TestEAPAKAPrimeAuthentication > ~/TestEAPAKAPrimeAuthentication.txt</i></li>
    <li><i>./test.sh TestGUTIRegistration > ~/TestGUTIRegistration.txt</i></li>
    <li><i>./test.sh TestN2Handover > ~/TestN2Handover.txt</i></li>
    <li><i>./test.sh TestNon3GPP > ~/TestNon3GPP.txt</i></li>
    <li><i>./test.sh TestPaging > ~/TestPaging.txt</i></li>
    <li><i>./test.sh TestPDUSessionReleaseRequest > ~/TestPDUSessionReleaseRequest.txt</i></li>
    <li><i>./test.sh TestRegistration > ~/TestRegistration.txt</i></li>
    <li><i>./test.sh TestReSynchronization > ~/TestReSynchronization.txt</i></li>
    <li><i>./test.sh TestServiceRequest > ~/TestServiceRequest.txt</i></li>
    <li><i>./test.sh TestXnHandover > ~/TestXnHandover.txt</i></li>
    <li>all tests should pass, besides maybe TestNon3GPP</li>
    <li>if there is an error in any of the tests, restart the vm and run video 8 routing commands, then run the other
        tests</li>
    <ul>
        <li>when the tests break, sometimes processes aren't shut down, which can mess with other tests</li>
    </ul>
</ul>

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

<h2>Video 12</h2>
<h4>Resumes with where Video 11 left off</h4>
<h4>both free5gc (f) and ueransim (u) vms are running</h4>
<h4>terminal sshed into ueransim</h4>
<ul>
    <li>(t) <i>cd ~</i></li>
    <li>(t) <i>git clone https://github.com/aligungr/UERANSIM</i></li>
    <li>(t) <i>sudo apt update</i></li>
    <li>(t) <i>sudo apt upgrade</i></li>
    <li>(t) <i>sudo apt install make</i></li>
    <li>(t) <i>sudo apt install g++</i></li>
    <li>(t) <i>sudo apt install libsctp-dev lksctp-tools</i></li>
    <li>(t) <i>sudo apt install iproute2</i></li>
    <li>(t) <i>sudo snap install cmake --classic</i></li>
    <li>(t) <i>cd ~/UERANSIM</i></li>
    <li>(t) <i>make</i></li>
    <ul>
        <li>should say 'UERANSIM successfully built'</li>
    </ul>
</ul>

<h2>Video 13</h2>
<h4>resumes with where video 12 left off:</h4>
<h4>both free5gc (f) and ueransim (u) vms are running</h4>
<ul>
    <li>open a terminal/cmd window (t)</li>
    <li>(t) <i>ssh 192.168.56.101 -l {username}</i></li>
    <li>(t) <i>cd free5gc</i></li>
    <li>(t) <i>sudo apt remove cmdtest</i></li>
    <li>(t) <i>sudo apt remove yarn</i></li>
    <li>(t) <i>curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -</i></li>
    <ul>
        <li>should result in 'OK'</li>
    </ul>
    <li>(t) <i>echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list</i>
    </li>
    <li>(t) <i>sudo apt-get update</i></li>
    <li>(t) <i>sudo apt-get install -y nodejs yarn</i></li>
    <li>(t) <i>pwd</i></li>
    <li>(t) <i>cd ~/free5gc</i></li>
    <li>(t) <i>make webconsole</i></li>
</ul>

<h2>Video 14</h2>
<h4>resumes with where video 13 left off</h4>
<h4>both free5gc (f) and ueransim (u) vms are running</h4>
<h4>terminal/cmd window sshed into free5gc (t)</h4>
<ul>
    <li>(t) <i>cd ~/free5gc</i></li>
    <li>(t) <i>cd webconsole</i></li>
    <li>(t) <i>go run server.go</i></li>
    <ul>
        <li>should result in 'Listening and serving HTTP on :5000'</li>
    </ul>
    <li>open a browser and enter the following url:</li>
    <ul>
        <li>'http://192.168.56.101:5000'</li>
        <li>login with 'admin' as username and 'free5gc' as password</li>
        <li>open subscribers tab on the left</li>
        <li>click 'New Subscriber'</li>
        <li>change 'Operator Code Type' to 'OP'</li>
        <li>scroll to the bottom and click 'Submit'</li>
    </ul>
    <li>go to terminal/cmd (t) and press Ctrl and C concurrently to interrupt the server</li>
    <ul>
        <li>should see logs of the new subscriber in the terminal (before interrupting)</li>
    </ul>
</ul>

<h2>Video 15</h2>
<h4>resumes with where video 14 left off</h4>
<h4>both free5gc (f) and ueransim (u) vms are running</h4>
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

<h2>Video 16</h2>
<h4>resumes with all vms powered off</h4>
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

<h2>Video 17</h2>
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

<h2>Video 18</h2>
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
