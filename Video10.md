<h1>Video 10</h1>
<h3>Resumes within host computer cmd ssh'ed to vm immediately after last command in video 9, vm should not have been
    closed between vid 9 and 10</h3>
<ul>
    <li><b><u>Make sure to run ip routing config commands from video 8, if a restart did occur between vid 9 &
                10</u></b></li>
    <li><b><u>Make sure to run sudo systemctl enable --now mongod, if a restart did occur between vid 9 & 10</u></b>
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
    <li>All tests should pass, besides maybe TestNon3GPP</li>
    <li>If there is an error in any of the tests, restart the vm and run video 8 routing commands, then run the other
        tests</li>
    <ul>
        <li>When the tests break, sometimes processes aren't shut down, which can mess with other tests</li>
    </ul>
</ul>
