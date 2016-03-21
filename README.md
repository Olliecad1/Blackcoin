# How to setup Blackcoin gui and command line interface on linux or raspberry pi 

1. You will need to install Blackcoin zip file from here https://github.com/rat4/blackcoin/archive/master.zip
2. Once you have it installed go to file manager and navigate to Downloads and you will see a folder called blackcoin-master.zip right click on it and click extract to then you will see a little box that called Extract files also you will see a little box with the name above Extract to default it will be /home/pi/Downloads/ but we want to extract it to /home/pi/ so backspace until you see /home/pi then click extract at the bottom
3. Now were getting into the good stuff open up a terminal window and type ls (ls stands for list segments it lists all the segments in the current directory) once you have typed ls you will see a directory called blackcoin-master so cd into blackcoin-master (cd stands for change directory we are changing directory) now that your in blackcoin-master type ls and you will see some more directorys now cd src and now you will see a bunch of c++ code now run this command 
<p>make -f makefile.unix USE_UPNP=-</p> 
this could take up to about an hour 
4. Once make has finished you can start copying files to /usr/local/bin so run the following command 
<p>strip blackcoind</p>
then press enter now run another command 
<p>sudo cp blackcoind /usr/local/bin/</p> 
thats all you have to do for now 
5. So now you can start creating the blackcoin.conf file so cd .. out of src and cd .. again out of blackcoin and now you will be in the home/pi directory so cd .blackcoin and you will see a bunch of data and files now type the following commands sudo nano blackcoin.conf and press enter (nano is a text editor) so now type or copy and paste the following code
<p>#Config file for Blackcoin</p> 
<p>#Daemon and listen ON/OFF</p> 
<p>daemon=1</p>
<p>#listen=1</p>

<p>#Connection User and Password</p>
<p>rpcuser=changethisuser</p>
<p>rpcpassword=changethispassword</p>

<p>#Authorized IPs</p>
<p>rpcallowip=127.0.0.1</p>

<p>#write the location for this blockchain below if not on standard directory</p>
<p>#datadir=/home/media/USB/.blackcoin</p>

<p>#Add extra Nodes</p>
<p>#addnode=1.2.3.4</p> 

6. Now control-x and press y then enter to save the code now cd .. and you will be in /home/pi now type cd /usr/local/bin and press enter now enter ls and you will see blackcoin now run ./blackcoind and it will say blackcoin server has started if you want to see how to get the blackcoin gui then carry on reading 
7. So close the terminal and open up a new one and cd blackcoin now your gonna have to install some dependencies so run the following commands
<p>sudo apt-get install libqt4-dev qt4-dev-tools libprotobuf-dev protobuf-compiler libqrencode-dev -y</p>
8. So now you can make the gui so now your in blackcoin run this command qmake this could take up to about 2 mins after that has finished run make this could up to about an hour and a half
9. Now after make has finished run 
<p>strip blackcoin-qt</p>
then when that has finished run 
<p>sudo cp blackcoin-qt /usr/local/bin</p>
10. Now you have finished setting everything up now how to run the gui so run blackcoind stop that will stop the command line interface now to run the gui type blackcoin-qt 
### That's all there is to it thanks for reading 