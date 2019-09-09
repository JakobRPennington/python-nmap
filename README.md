# python-nmap

[![Python 3.7](https://img.shields.io/badge/python-3.7-blue.svg?style=for-the-badge)](https://www.python.org/downloads/release/python-374/)
[![GNU General Public License v3.0](https://img.shields.io/github/license/JakobRPennington/python-nmap?style=for-the-badge)](https://github.com/JakobRPennington/python-nmap/blob/master/LICENSE)

A python library to build and run nmap scans and parse scan output.

## Wait.. You didn't make this

Thanks to all the work put into this library by Alexandre Norman and past contributors. I have forked the python-nmap since it appears to have been inactive for some time. If I make further updates to the library, or others contribute to this repo, I may re-publish the package.

Original repository: [https://bitbucket.org/xael/python-nmap](https://bitbucket.org/xael/python-nmap)  
Webiste: [https://xael.org/pages/python-nmap-en.html](https://xael.org/pages/python-nmap-en.html)

## Installation

To install from source:

```bash
git clone https://github.com/JakobRPennington/python-nmap.git
cd python-nmap
python setup.py install
```

## Example usage

```python
>>> import nmap
>>> nm = nmap.PortScanner()
>>> nm.scan('127.0.0.1', '22-443')
>>> nm.command_line()
'nmap -oX - -p 22-443 -sV 127.0.0.1'
>>> nm.scaninfo()
{'tcp': {'services': '22-443', 'method': 'connect'}}
>>> nm.all_hosts()
['127.0.0.1']
>>> nm['127.0.0.1'].hostname()
'localhost'
>>> nm['127.0.0.1'].state()
'up'
>>> nm['127.0.0.1'].all_protocols()
['tcp']
>>> nm['127.0.0.1']['tcp'].keys()
[80, 25, 443, 22, 111]
>>> nm['127.0.0.1'].has_tcp(22)
True
>>> nm['127.0.0.1']['tcp'][22]
{'state': 'open', 'reason': 'syn-ack', 'name': 'ssh'}
```

For more example usage, see [eamples/example.py](https://github.com/JakobRPennington/python-nmap/examples/example.py).

## Contributors

The original package maintainer:

* Alexandre Norman

Contributors to the original package:

* Steve 'Ashcrow' Milner
* Brian Bustin
* old.schepperhand
* Johan Lundberg
* Thomas D. maaaaz
* Robert Bost
