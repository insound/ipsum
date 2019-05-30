![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-Public_domain-red.svg)](https://wiki.creativecommons.org/wiki/Public_domain)

About
----

**IPsum** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt-get -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

**Important:** If you are planning to use `git` to get the content of this repository do it like `git clone --depth 1 https://github.com/stamparm/ipsum.git`

Wall of shame (2019-05-30)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
171.25.193.77|tor-exit1-readme.dfri.se|12
171.25.193.78|tor-exit4-readme.dfri.se|11
171.25.193.20|tor-exit0-readme.dfri.se|11
197.231.221.211|exit1.ipredator.se|11
171.25.193.25|tor-exit5-readme.dfri.se|10
80.82.77.33|sky.census.shodan.io|9
89.248.172.169|-|9
103.79.141.158|-|9
183.230.146.26|-|9
199.87.154.255|tor.les.net|9
198.98.60.66||9
134.209.175.214|-|9
166.70.207.2|this.is.a.tor.node.xmission.com|9
176.10.104.240|tor1e1.digitale-gesellschaft.ch|9
80.82.77.139|dojo.census.shodan.io|9
171.25.193.235|tor-exit3-readme.dfri.se|9
65.19.167.131|-|9
64.113.32.29|tor.t-3.net|9
37.187.129.166|ns316491.ip-37-187-129.eu|9
89.248.172.16|house.census.shodan.io|9
85.248.227.165|-|9
185.100.87.207|freki.enn.lu|9
128.199.46.189|-|8
167.99.38.73|-|8
89.234.157.254|marylou.nos-oignons.net|8
134.209.175.199|-|8
178.73.215.171|178-73-215-171-static.glesys.net|8
134.209.84.42|-|8
134.209.82.3|-|8
128.199.55.17|-|8
176.31.208.193|tor-exit1.netnik.xyz|8
145.249.107.10|-|8
223.100.123.8|-|8
162.213.3.221|tor-exit1.sjc02.svwh.net|8
198.96.155.3|exit.tor.uwaterloo.ca|8
185.107.47.171|tor-exit.r2.darknet.dev|8
206.189.128.225|-|8
46.165.245.154|-|8
165.227.75.114|-|8
109.201.133.100||8
158.69.192.200|200.ip-158-69-192.net|8
222.187.254.189|-|8
185.165.168.229|-|8
192.42.116.16|tor-exit.hartvoorinternetvrijheid.nl|8
113.255.21.140|140-21-255-113-on-nets.com|8
185.220.101.46|-|8
18.85.192.253|wholesomeserver.media.mit.edu|8
193.32.163.89|srv.eqaltech.su|8
85.248.227.163|ori.enn.lu|8
159.65.151.151|-|8
98.235.133.140|c-98-235-133-140.hsd1.pa.comcast.net|8
207.244.70.35|-|8
178.62.127.90|-|8
104.244.73.126|lu1.exit.tor.alkyl.eu.org|8
165.227.46.17|-|8
142.93.153.153|-|8
65.19.167.132|-|8
185.244.25.205|-|8
80.82.70.118|group-ib.com|8
35.0.127.52|tor-exit.eecs.umich.edu|8
80.67.172.162|algrothendieck.nos-oignons.net|8
134.209.219.47|-|8
138.197.162.115|-|8
42.61.24.202|-|8
128.199.47.29|-|8
68.183.89.236|-|8
142.93.157.35|-|8
142.93.157.67|-|8
159.89.237.34|-|8
62.102.148.68|-|8
62.102.148.67|-|8
5.199.130.188|tor.piratenpartei-nrw.de|8
108.53.62.148|pool-108-53-62-148.nwrknj.fios.verizon.net|8
159.65.145.206|-|8
142.93.153.234|-|8
192.160.102.166|chaucer.relay.coldhak.com|8
178.62.98.15|-|8
221.13.68.195|-|8
194.36.173.3|-|8
185.142.236.34|hat.census.shodan.io|8
62.210.105.116|62-210-105-116.rev.poneytelecom.eu|8
137.74.167.96|ns200.anycast.me.6290lv1irc.xyz|8
101.227.64.169|-|8
