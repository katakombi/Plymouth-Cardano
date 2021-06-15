# Plymouth-Cardano
Cardano Boot Splash

How to install
```
sudo mkdir /usr/share/plymouth/themes/cardano
clear
sudo rsync -aq --exclude=install-circle * /usr/share/plymouth/themes/cardano
clear
sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/cardano/cardano.plymouth 100
sudo update-alternatives --config default.plymouth  #here, choose the number of the theme you want to use then hit enter
sudo update-initramfs -u
echo
echo Installing plymouth-x11...   Redundant if already installed.
sudo apt-get install plymouth-x11
echo
echo Running 10-second test...
sudo plymouthd ; sudo plymouth --show-splash ; for ((I=0; I<10; I++)); do sleep 1 ; sudo plymouth --update=test$I ; done ; sudo plymouth --quit
exit
```

How to debug
```
#requires plymouth-x11 installed
#sudo apt-get install plymouth-x11
echo
echo "Running 5-second debug test..."
echo "Creates /usr/share/plymouth/themes/cardano/debug.log for debugging"
sudo plymouthd --debug --debug-file=/usr/share/plymouth/themes/cardano/debug.log; sudo plymouth --show-splash ; for ((I=0; I<40; I++)); do sleep 1 ; sudo plymouth --update=test$I ; done ; sudo plymouth --quit
```
