<h1>Video 9</h1>
<h3>Resumes within host computer cmd ssh'ed to vm</h3>
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
