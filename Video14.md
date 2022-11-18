<h1>Video 14</h1>
<h3>Resumes with where video 13 left off</h3>
<h3>Both free5gc (f) and ueransim (u) vms are running</h3>
<h3>Terminal/cmd window sshed into free5gc (t)</h3>
<ul>
    <li>(t) <i>cd ~/free5gc</i></li>
    <li>(t) <i>cd webconsole</i></li>
    <li>(t) <i>go run server.go</i></li>
    <ul>
        <li>Should result in 'Listening and serving HTTP on :5000'</li>
    </ul>
    <li>Open a browser and enter the following url:</li>
    <ul>
        <li>'http://192.168.56.101:5000'</li>
        <li>Login with 'admin' as username and 'free5gc' as password</li>
        <li>Open subscribers tab on the left</li>
        <li>Click 'New Subscriber'</li>
        <li>Change 'Operator Code Type' to 'OP'</li>
        <li>Scroll to the bottom and click 'Submit'</li>
    </ul>
    <li>Go to terminal/cmd (t) and press Ctrl and C concurrently to interrupt the server</li>
    <ul>
        <li>Should see logs of the new subscriber in the terminal (before interrupting)</li>
    </ul>
</ul>
