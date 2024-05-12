```sh
nmap 192.168.246.0/24 -sV -T5 -v --reason -Pn -n
```

```
nmap 192.168.246.0/24 -sV -T5 -v --reason -n -oA **nmap_output**
```

```sh
nmap 192.168.0.0/24 -sV -T5 -v --reason -n -p139,445 -oA nmap-192.168.246.0.txt

nmap 192.168.246.0/24 -sV -T5 -v --reason -n -p139,445 -oA nmap-192.168.246.0-sV-T5-n-139-445

grep '445\/open' **nmap-192.168.246.0-sV-T5-n-139-445.gnmap**

grep '445\/open' **nmap-192.168.246.0-sV-T5-n-139-445.gnmap** **|** cut -d' ' -f2

nmap -iL **445.txt** -p139,445 -sVC -v
```