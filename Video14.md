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
