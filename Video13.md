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
