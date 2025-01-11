## Python

#### venv

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

### Decomplie Python 2.7 scripts

```
uncompyle6 -o . script.pyc
```



#### List all installed packages and dependencies. 

```
python3 -m pip freeze
```

#### Managing libraries 

```
python3
import sys
sys.path
```


