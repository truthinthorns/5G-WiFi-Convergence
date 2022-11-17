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
