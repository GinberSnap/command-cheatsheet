# Autopsy


### Running Autopsy on Kali on VM

```
cd /home/kali/autopsy/autopsy-4.21.0

bin/autopsy --nosplash
```

### Installing Autopsy on Kali on VM

* https://github.com/sleuthkit/autopsy/blob/develop/Running_Linux_OSX.md

* https://github.com/sleuthkit/autopsy/releases

```
sudo apt remove sleuthkit
sudo apt remove libtsk19
sudo apt autoremove
sudo apt install ./sleuthkit-java_4.12.1-1_amd64.deb
```

```
install_application.sh -z autopsy-4.21.0.zip  -i /home/kali/autopsy -j /usr/lib/jvm/java-1.17.0-openjdk-amd64
```
