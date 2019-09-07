# /etc/resolv.conf

## Operation by svccfg command


### input

#### /etc/resolv.conf domain

```
# svccfg -s network/dns/client setprop 'config/domain = astring: example.jp'
```

#### /etc/resolv.conf search

```
# svccfg -s network/dns/client setprop 'config/search = astring: ( "example.jp" "example.com" "example.net" )'
```

#### /etc/resolv.conf nameserver

Max 3 servers.

```
# svccfg -s network/dns/client setprop 'config/nameserver = net_address: ( 192.168.0.1 172.16.0.1 10.0.0.1 )'
```

#### /etc/resolv.conf options

```
# svccfg -s network/dns/client setprop 'config/options = astring: ( "timeout:2 attempts:2" )'
```

See also resolv.conf(4)


### commit

Last check, this values not update /etc/resolv.conf yet.

```
# svccfg -s network/dns/client listprop | grep ^config/
config/value_authorization                                     astring     solaris.smf.value.name-service.dns.client
config/domain                                                  astring     example.jp
config/options                                                 astring     "timeout:2 attempts:2"
config/search                                                  astring     "example.jp" "example.com" "example.net"
config/nameserver                                              net_address 192.168.0.1 172.16.0.1 10.0.0.1
```

```
# svcadm refresh svc:/network/dns/client:default
```

/etc/resolv.conf update after "svcadm refresh"

```
# egrep -v "^$|^#" /etc/resolv.conf
domain  example.jp
search  example.jp example.com example.net
options timeout:2 attempts:2
nameserver      192.168.0.1
nameserver      172.16.0.1
nameserver      10.0.0.1
```

#### Syntax check

```
# nscfg validate svc:/network/dns/client:default && echo OK
OK
```
