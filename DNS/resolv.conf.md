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
