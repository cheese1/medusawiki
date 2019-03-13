Since version 3.0.0 Medusa supports Python version 3.5 and newer. As Python 2.7 will reach its [EOL in 2020](https://github.com/python/devguide/pull/344) we recommend to switch to Python 3 as soon as possible. For security reasons we won't be providing support for Python 2.7 after its EOL date.

## Ubuntu
1. Install Python 3.6 if you haven't already:

Follow this well written guide over at [Real Python](https://realpython.com/installing-python/#ubuntu).

2. Update your systemd script: [Systems with systemd](https://github.com/pymedusa/Medusa/wiki/_new#systems-with-systemd).


## Debian
1. Your best bet will be compiling Python 3 from source:

Follow this well written guide over at [Real Python](https://realpython.com/installing-python/#compiling-python-from-source).

2. Update your daemon:

**Debian 8.0 and newer**:

Update your systemd script: [Systems with systemd](https://github.com/pymedusa/Medusa/wiki/_new#systems-with-systemd).

**Debian 7.0**:

Update your initd script: [Systems with SysVinit](https://github.com/pymedusa/Medusa/wiki/Switch-to-Python-3#systems-with-sysvinit).

## CentOS
1. Install Python 3.6 if you haven't already:

Follow this well written guide over at [Real Python](https://realpython.com/installing-python/#centos).

2. Update your daemon:

**CentOS 7 and newer**:

Update your systemd script: [Systems with systemd](https://github.com/pymedusa/Medusa/wiki/_new#systems-with-systemd).

**CentOS 6**:

Update your initd script: [Systems with SysVinit](https://github.com/pymedusa/Medusa/wiki/Switch-to-Python-3#systems-with-sysvinit).

## Systems with systemd
1. Open your systemd script located at:
```
/etc/systemd/system/medusa.service
```
2. Replace all mentions of python**2.7** with python**3.6** and save.
3. Reload systemd daemon:
```
systemctl daemon-reload
```
4. Restart Medusa as you'd normally do:
```
sudo systemctl restart medusa
```

## Systems with SysVinit
1. Open your init.d script located at:
```
/etc/init.d/medusa
```
2. Replace all mentions of python**2.7** with python**3.6** and save.
3. Update and restart the service
```
sudo update-rc.d medusa defaults
sudo service medusa start
```