# Установка

### Docker

```text
docker pull antonkuzmin/web-scout:latest
```

### Ubuntu/Debian

```text
apt update
apt install git python-configparser python-argparse python-selenium python-lxml xvfb python-pyvirtualdisplay python-dnspython python-requests python-pip
pip install pysocks
git clone https://github.com/AntonKuzminRussia/web-scout.git 
cd web-scout
```

### Fedora/CentOS

```text
yum install git python-configparser python-lxml xorg-x11-server-Xvfb python-requests python-pip 
pip install pysocks dnspython pyvirtualdisplay selenium argparse
git clone https://github.com/AntonKuzminRussia/web-scout.git 
cd web-scout
```

### virtualenv

```text
virtualenv env 
source env/bin/activate 
pip intall -r requirements.txt
```

### Из исходных кодов

Исходные коды можно взять на [https://github.com/AntonKuzminRussia/web-scout](https://github.com/AntonKuzminRussia/web-scout) . Установите следующие пакеты для Python2:

* configparser 
* argparse 
* requests 
* selenium 
* dnspython 
* pyvirtualdisplay 
* lxml
* pysocks





