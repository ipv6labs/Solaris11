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


### refresh

