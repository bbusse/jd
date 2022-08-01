# jd
Collects data about FreeBSD jails and makes it available as JSON,  
exports data for Prometheus

# Usage
## Install
```
$ git clone https://github.com/bbusse/jd
$ pip install --user -r requirements.txt
```

## Start jd
### Ad-hoc
```
$ JD_LISTEN_ADDRESS=hq JD_LISTEN_PORT="8080" ./jd
```
or
```
$ ./jd --listen-address [::1] --listen-port 8080
```
### Service
An rc script is included  
```
$ sudo cp jd_rc /usr/local/etc/rc.d/jd
```
jd can run as its own unprivileged user as long as only data about jails
is required. Manipulation of jails , e.g. start and stop needs root privileges
```
$ sudo service jd onestart
```
or
```
$ sudo service jd enable
$ sudo service jd start
```

## List jails
```
$ curl http://[::1]:8080/jails
```

# How
jd as of now has two sources of information.  
One is [jls(8)](https://docs.freebsd.org/en/books/handbook/jails/) for running jails.  
The other is the per jail config file of ezjail.  
While jls only gives information about running jails, ezjail configuration files are the source of information for defined jails.
ezjail however is optional

## Start / Stop / Restart Jail
Not implemented
```
$ curl http://[::1]/jail/start/[#index]
```

# Resources
[FreeBSD Handbooki - Jails](https://docs.freebsd.org/en/books/handbook/jails/)  
[jls(8) Manual Page](https://www.freebsd.org/cgi/man.cgi?query=jls&sektion=8)  
[ezjail](https://erdgeist.org/arts/software/ezjail/)  
