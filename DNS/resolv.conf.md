# /etc/resolv.conf

## Operation by svccfg command

### domain

```
# svccfg -s network/dns/client setprop 'config/domain = astring: example.jp'
```

### search

```
# svccfg -s network/dns/client setprop 'config/search = astring: ( "example.jp" "example.com" "example.net" )'
```

### nameserver

Max 3 servers.

```
# svccfg -s network/dns/client setprop 'config/nameserver = net_address: ( 192.168.0.1 172.16.0.1 10.0.0.1 )'
```
