# Setting up Kali Environment on Raspberry Pi 5

### 1. Kali update
```
sudo apt update && sudo apt full-upgrade -y
```

## 2. Wordlists & Rules

```
sudo gzip -d /usr/share/wordlists/rockyou.txt.gz
```

```
sudo mv OneRuleToRuleThemAll.rule /usr/share/hashcat/rules/
```

## 3. Installing GDB

```
sudo apt install gdb
```

## 4. Installing GEF
```
wget -O ~/.gdbinit-gef.py -q https://gef.blah.cat/py
echo source ~/.gdbinit-gef.py >> ~/.gdbinit
```

## 5. Installing VScode

```
sudo apt install ./code_1.88.1-12345_amd64.deb
```

Note: Select `Arm64 .deb` for Raspberry pi. [Download link](https://code.visualstudio.com/download)


## 6. Install Ghidra

```
sudo apt install ghidra
```

## 7. Install Burp
```
sudo apt install openjdk-17-jre -y
java -version
```
```
chmod +x burpsuite_community_linux_arm64_v2024_12_1.sh
./burpsuite_community_linux_arm64_v2024_12_1.sh
```

[Burp Suite Community Download Link](https://portswigger.net/burp/releases/professional-community-2024-12-1)

## 8. Python Env
```
sudo apt install python3-dev python3-pip python3-venv
```

Go to a directory, then active `env`
```
python3 -m venv env
```
```
source env/bin/activate
```
Deactivate
```
deactivate
```
