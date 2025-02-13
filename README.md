![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-The_Unlicense-red.svg)](https://unlicense.org/)

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
ipset -q create ipsum hash:ip
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -D INPUT -m set --match-set ipsum src -j DROP 2>/dev/null
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

Wall of Shame (2024-02-27)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
185.161.248.218|-|10
80.82.77.33|sky.census.shodan.io|9
167.94.146.60|-|9
162.142.125.223|scanner-25.ch1.censys-scanner.com|9
80.82.77.139|dojo.census.shodan.io|9
178.20.55.16|marcuse.nos-oignons.net|9
103.251.167.20|-|9
189.6.45.130|bd062d82.virtua.com.br|9
85.209.11.227|-|9
115.20.185.86|-|9
141.98.11.169|exclu.lutend-169.seneciomorphology.com|9
93.174.95.106|battery.census.shodan.io|9
36.110.228.254|-|9
71.6.135.131|soda.census.shodan.io|9
182.72.142.62|nsg-static-062.142.72.182.airtel.in|8
112.161.151.6|-|8
182.229.10.141|-|8
162.247.74.200|-|8
185.224.128.17|-|8
71.6.199.23|einstein.census.shodan.io|8
218.92.0.34|-|8
218.92.0.31|-|8
123.31.29.192|static.vnpt.vn|8
162.142.125.221|scanner-25.ch1.censys-scanner.com|8
162.142.125.220|scanner-25.ch1.censys-scanner.com|8
162.142.125.226|scanner-25.ch1.censys-scanner.com|8
218.92.0.76|-|8
171.25.193.77|tor-exit-read-me.dfri.se|8
107.180.88.176|176.88.180.107.host.secureserver.net|8
167.248.133.37|scanner-08.ch1.censys-scanner.com|8
167.248.133.35|scanner-08.ch1.censys-scanner.com|8
194.152.206.17|-|8
218.92.0.56|-|8
61.177.172.136|-|8
71.6.146.186|inspire.census.shodan.io|8
71.6.146.185|pirate.census.shodan.io|8
213.109.202.127|-|8
61.177.172.179|-|8
186.10.125.209|z407.entelchile.net|8
167.248.133.38|scanner-08.ch1.censys-scanner.com|8
80.229.18.62|maryfindlay.plus.com|8
193.233.21.60|-|8
222.118.223.15|-|8
89.234.157.254|-|8
14.46.173.248|-|8
207.90.244.5|-|8
167.94.146.57|-|8
167.94.146.59|-|8
121.176.65.141|-|8
162.142.125.14|scanner-04.ch1.censys-scanner.com|8
114.118.10.141|-|8
61.177.172.140|-|8
121.158.203.212|-|8
218.92.0.29|-|8
218.92.0.22|-|8
218.92.0.25|-|8
218.92.0.24|-|8
218.92.0.27|-|8
122.116.57.36|122-116-57-36.hinet-ip.hinet.net|8
146.56.46.76|-|8
61.177.172.160|-|8
190.144.14.170|-|8
89.147.108.62|tor-is.reichsfunkma.st|8
162.142.125.216|scanner-05.ch1.censys-scanner.com|8
134.209.156.5|-|8
221.162.209.158|-|8
207.90.244.14|-|8
218.92.0.112|-|8
218.92.0.113|-|8
218.92.0.118|-|8
211.199.187.14|-|8
80.67.172.162|algrothendieck.nos-oignons.net|8
71.6.158.166|ninja.census.shodan.io|8
185.129.62.62|tor01.zencurity.com|8
180.101.88.197|-|8
180.101.88.196|-|8
185.161.248.217|-|8
89.97.218.142|89-97-218-142.ip19.fastwebnet.it|8
218.92.0.107|-|8
159.65.220.18|ulaportal.com|8
185.142.236.36|green.census.shodan.io|8
84.239.46.144|-|8
167.94.138.51|scanner-07.ch1.censys-scanner.com|8
61.93.186.125|061093186125.static.ctinets.com|8
134.122.8.241|-|8
192.42.116.24|this-is-a-tor-exit-node-hviv124.hviv.nl|7
180.76.124.150|-|7
205.185.127.240|-|7
211.193.31.52|-|7
137.184.92.227|-|7
51.79.250.103|vps-9cda1074.vps.ovh.ca|7
31.220.3.140|freecouncil.net|7
198.235.24.38|-|7
198.235.24.37|-|7
152.32.128.214|-|7
196.0.120.211|xen2.utlonline.co.ug|7
165.227.84.172|-|7
162.247.74.202|-|7
162.247.74.206|-|7
162.247.74.204|-|7
159.65.41.104|-|7
185.180.143.148|sh-ams-nl-gp1-wk113.internet-census.org|7
185.180.143.143|sh-ams-nl-gp1-wk115.internet-census.org|7
185.180.143.142|sh-ams-nl-gp1-wk114.internet-census.org|7
121.158.249.166|-|7
103.115.104.50|-|7
210.91.254.26|-|7
139.162.190.203|optout.scanopticon.com|7
117.50.118.202|-|7
121.204.164.96|-|7
79.104.0.82|-|7
43.155.172.248|-|7
43.153.22.166|-|7
43.156.19.22|-|7
121.186.97.121|-|7
161.35.50.225|-|7
43.134.70.191|-|7
165.22.193.40|-|7
43.129.158.215|-|7
194.113.236.217|-|7
211.253.10.96|-|7
157.230.113.181|-|7
190.202.124.93|correo.grupoplumas.net|7
121.159.163.6|-|7
172.104.11.34|edinburgh.scan.bufferover.run|7
180.184.46.145|-|7
118.123.105.85|-|7
202.51.74.123|-|7
105.28.108.165|-|7
45.128.232.67|-|7
97.74.95.243|243.95.74.97.host.secureserver.net|7
118.101.192.62|-|7
23.95.218.244|23-95-218-244-host.colocrossing.com|7
170.64.208.208|-|7
201.226.239.98|r1.up.ac.pa|7
31.210.220.97|-|7
139.59.71.253|-|7
85.247.2.222|bl14-2-222.dsl.telepac.pt|7
45.79.181.251|guernsey.scan.bufferover.run|7
114.199.123.211|ip-114-199-123-211.netzap.net.id|7
67.205.187.255|-|7
139.224.69.233|-|7
128.199.33.46|-|7
116.55.245.26|-|7
128.14.211.186|zl-dal-us-gp1-wk143.internet-census.org|7
188.166.47.99|-|7
167.248.133.190|scanner-29.ch1.censys-scanner.com|7
182.253.204.114|-|7
106.225.198.205|-|7
218.255.245.10|static.reserve.wtt.net.hk|7
45.225.195.250|45-225-195-250.ibiunet.com.br|7
220.80.180.170|-|7
94.102.49.193|cloud.census.shodan.io|7
161.35.108.241|-|7
213.6.203.226|-|7
103.47.82.152|-|7
124.156.203.28|-|7
122.160.65.215|abts-north-static-215.65.160.122.airtelbroadband.in|7
45.33.80.243|minsk.scan.bufferover.run|7
186.67.248.6|-|7
89.132.167.147|catv-89-132-167-147.catv.fixed.vodafone.hu|7
43.131.61.31|-|7
45.79.168.172|45-79-168-172.ip.linodeusercontent.com|7
146.190.231.213|portscanner-ams3-03.prod.cyberresilience.io|7
45.79.181.179|andorra.scan.bufferover.run|7
43.156.237.124|-|7
103.56.61.144|-|7
43.156.57.126|-|7
165.227.166.247|-|7
162.142.125.222|scanner-25.ch1.censys-scanner.com|7
162.142.125.225|scanner-25.ch1.censys-scanner.com|7
162.142.125.224|scanner-25.ch1.censys-scanner.com|7
103.115.104.38|-|7
158.180.65.241|-|7
167.248.133.50|scanner-09.ch1.censys-scanner.com|7
138.2.31.179|-|7
222.118.29.221|-|7
180.76.227.46|-|7
43.133.74.110|-|7
112.168.27.14|-|7
87.255.193.50|-|7
150.136.129.10|-|7
65.73.231.122|-|7
82.200.65.218|gw-bell-xen.ll-nsk.zsttk.ru|7
121.227.31.13|-|7
132.145.208.65|-|7
167.248.133.33|scanner-08.ch1.censys-scanner.com|7
167.248.133.39|scanner-08.ch1.censys-scanner.com|7
43.241.51.13|-|7
162.62.229.103|-|7
59.125.75.24|59-125-75-24.hinet-ip.hinet.net|7
185.220.101.187|tor-exit-187.relayon.org|7
185.220.101.183|tor-exit-183.relayon.org|7
218.92.0.53|-|7
34.85.163.94|94.163.85.34.bc.googleusercontent.com|7
35.207.98.222|222.98.207.35.bc.googleusercontent.com|7
164.77.117.10|-|7
95.156.96.46|-|7
121.153.203.84|-|7
97.74.80.116|116.80.74.97.host.secureserver.net|7
218.206.136.24|-|7
43.153.226.61|-|7
180.148.4.194|-|7
202.55.175.236|-|7
165.16.27.10|-|7
167.248.133.53|scanner-09.ch1.censys-scanner.com|7
134.209.34.154|-|7
107.158.225.94|-|7
114.129.28.238|-|7
103.143.248.87|-|7
43.156.1.71|-|7
186.200.158.42|-|7
51.89.153.112|ns3145504.ip-51-89-153.eu|7
150.109.196.110|-|7
85.221.48.114|-|7
167.94.138.36|scanner-06.ch1.censys-scanner.com|7
192.155.90.118|dublin.scan.bufferover.run|7
185.42.170.203|exit01.tor.anduin.net|7
150.136.43.235|-|7
167.248.133.36|scanner-08.ch1.censys-scanner.com|7
42.200.66.164|42-200-66-164.static.imsbiz.com|7
175.206.80.31|-|7
148.135.12.30|heapbuys.com|7
43.153.10.208|-|7
104.250.50.16|-|7
185.220.101.185|tor-exit-185.relayon.org|7
94.254.0.234|h-94-254-0-234.na.cust.bahnhof.se|7
185.100.87.174|torexit1.flokinet.net|7
198.96.155.3|exit.tor.uwaterloo.ca|7
60.247.225.32|-|7
150.109.252.192|-|7
43.163.229.234|-|7
181.48.60.50|-|7
186.10.245.152|z350.entelchile.net|7
43.156.232.111|-|7
121.142.87.218|-|7
121.142.146.167|-|7
167.94.145.60|-|7
43.134.25.106|-|7
187.190.112.180|fixed-187-190-112-180.totalplay.net|7
72.240.125.133|cm-72-240-125-133.buckeyecom.net|7
175.207.13.22|-|7
170.64.179.62|-|7
113.59.119.97|-|7
43.135.148.51|-|7
152.32.199.73|-|7
43.134.129.161|-|7
222.186.13.132|-|7
118.45.205.44|-|7
223.197.186.7|223-197-186-7.static.imsbiz.com|7
185.130.44.108|tor-exit-se1.privex.cc|7
199.45.155.17|scanner-202.hk2.censys-scanner.com|7
185.246.188.73|-|7
62.219.172.50|bzq-219-172-50.dsl.bezeqint.net|7
121.178.36.107|-|7
118.163.196.104|118-163-196-104.hinet-ip.hinet.net|7
43.155.183.246|-|7
205.210.31.201|-|7
43.159.40.34|-|7
159.65.91.105|-|7
36.134.203.34|-|7
34.101.240.144|144.240.101.34.bc.googleusercontent.com|7
134.122.17.178|-|7
96.78.175.36|96-78-175-36-static.hfc.comcastbusiness.net|7
96.78.175.38|96-78-175-38-static.hfc.comcastbusiness.net|7
195.144.21.56|red3.census.shodan.io|7
175.206.117.126|-|7
103.146.16.45|-|7
113.161.194.27|static.vnpt.vn|7
49.51.72.84|-|7
207.90.244.6|-|7
219.144.67.60|-|7
178.128.97.141|-|7
164.163.98.49|164-163-98-49.isp.infomaistelecom.com.br|7
167.94.138.33|scanner-06.ch1.censys-scanner.com|7
43.133.166.245|-|7
112.173.90.204|-|7
162.142.125.12|scanner-04.ch1.censys-scanner.com|7
170.106.74.178|-|7
223.167.121.235|-|7
120.48.124.172|-|7
167.94.146.53|-|7
167.94.146.56|-|7
167.94.146.58|-|7
159.192.143.249|-|7
71.6.134.232|-|7
71.6.134.234|-|7
185.220.103.8|mariellefranco.tor-exit.calyxinstitute.org|7
84.2.226.70|ktv5402e246.fixip.t-online.hu|7
118.123.105.93|-|7
77.37.168.42|broadband-77-37-168-42.ip.moscow.rt.ru|7
213.3.40.107|107.40.3.213.static.wline.lns.sme.cust.swisscom.ch|7
165.154.43.143|-|7
103.48.193.7|-|7
118.36.15.126|-|7
122.155.0.205|www.phatan.go.th|7
149.56.44.47|47.ip-149-56-44.net|7
121.164.71.235|-|7
171.25.193.234|tor-exit-read-me.dfri.se|7
129.226.147.252|-|7
162.142.125.13|scanner-04.ch1.censys-scanner.com|7
162.142.125.11|scanner-04.ch1.censys-scanner.com|7
107.189.2.157|-|7
192.155.90.220|bern.scan.bufferover.run|7
171.25.193.25|tor-exit-read-me.dfri.se|7
74.82.47.3|-|7
167.248.133.52|scanner-09.ch1.censys-scanner.com|7
80.91.183.93|80.91.183.93.ipv4.datagroup.ua|7
43.134.227.133|-|7
61.74.14.153|-|7
170.64.175.91|-|7
193.122.166.253|-|7
114.67.110.206|-|7
193.70.1.27|27.ip-193-70-1.eu|7
71.6.146.130|refrigerator.census.shodan.io|7
172.105.128.12|reykjavik.scan.bufferover.run|7
43.156.80.60|-|7
195.158.5.3|-|7
121.180.201.251|-|7
128.199.211.78|-|7
185.233.100.23|elenagb.nos-oignons.net|7
185.216.116.44|-|7
175.24.203.218|-|7
137.184.185.142|-|7
211.252.27.38|-|7
71.6.167.142|census9.shodan.io|7
192.155.88.231|192-155-88-231.ip.linodeusercontent.com|7
167.248.133.185|scanner-29.ch1.censys-scanner.com|7
167.248.133.184|scanner-29.ch1.censys-scanner.com|7
167.248.133.187|scanner-29.ch1.censys-scanner.com|7
167.248.133.186|scanner-29.ch1.censys-scanner.com|7
68.183.88.186|-|7
167.94.138.124|scanner-27.ch1.censys-scanner.com|7
167.94.138.127|scanner-27.ch1.censys-scanner.com|7
194.120.24.243|device-telecer.dockeriron.net|7
47.180.114.229|-|7
2.57.122.127|-|7
185.56.83.83|onion.xor.sc|7
213.89.216.193|c213-89-216-193.bredband.tele2.se|7
92.119.231.76|vm30136.realhost-free.net|7
185.67.82.114|tor-ou.effi.org|7
222.113.125.16|-|7
211.229.73.221|-|7
74.40.19.68|-|7
125.99.173.162|-|7
43.153.83.135|-|7
43.153.45.125|-|7
43.157.82.142|-|7
223.197.188.206|223-197-188-206.static.imsbiz.com|7
183.136.225.32|-|7
65.181.73.155|65-181-73-155.static.imsbiz.com|7
43.135.172.127|-|7
43.155.107.205|-|7
43.156.29.148|-|7
176.109.0.30|-|7
34.123.134.194|194.134.123.34.bc.googleusercontent.com|7
43.157.10.157|-|7
92.154.95.236|lstlambert-656-1-48-236.w92-154.abo.wanadoo.fr|7
51.222.13.180|vps-9de7d664.vps.ovh.ca|7
170.106.73.154|-|7
178.128.93.152|-|7
129.226.201.243|-|7
162.142.125.214|scanner-05.ch1.censys-scanner.com|7
162.142.125.215|scanner-05.ch1.censys-scanner.com|7
162.142.125.217|scanner-05.ch1.censys-scanner.com|7
162.142.125.213|scanner-05.ch1.censys-scanner.com|7
43.134.41.100|-|7
185.241.208.206|-|7
210.212.99.168|static.ill.210.212.99.168/24.bsnl.in|7
112.164.236.13|-|7
146.190.222.176|-|7
187.50.178.142|187-50-178-142.customer.tdatabrasil.net.br|7
66.240.236.109|ubuntu20236109.aspadmin.net|7
140.86.39.162|oc-140-86-39-162.compute.oraclecloud.com|7
50.187.52.51|50-187-52-51-static.hfc.comcastbusiness.net|7
122.160.25.225|abts-north-static-225.25.160.122.airtelbroadband.in|7
43.134.104.29|-|7
37.113.26.6|-|7
219.77.19.170|n219077019170.netvigator.com|7
80.82.77.202|rnd.group-ib.com|7
80.67.167.81|nosoignons.cust.milkywan.net|7
91.205.128.170|-|7
36.91.135.141|-|7
45.172.153.100|-|7
184.105.247.252|-|7
120.48.179.33|-|7
121.137.74.48|-|7
80.249.113.79|-|7
95.181.43.122|95-181-43-122.goodline.info|7
37.59.64.163|ip163.ip-37-59-64.eu|7
139.150.74.245|-|7
162.62.133.200|-|7
43.134.250.248|-|7
220.76.163.140|-|7
49.229.0.188|-|7
125.141.139.29|-|7
143.198.146.239|-|7
101.126.35.124|-|7
103.10.44.7|-|7
220.119.65.20|-|7
185.129.61.3|tor-project-exit3.dotsrc.org|7
71.6.165.200|census12.shodan.io|7
104.225.154.161|104.225.154.161.16clouds.com|7
43.134.75.206|-|7
67.205.190.61|-|7
52.183.128.237|-|7
185.235.146.29|-|7
183.107.151.167|-|7
191.100.25.45|45.191-100-25.etapanet.net|7
144.34.171.163|144.34.171.163.16clouds.com|7
43.157.96.119|-|7
185.165.190.34|red.census.shodan.io|7
109.167.197.20|109-167-197-20.westcall.net|7
14.116.189.74|-|7
167.248.133.34|scanner-08.ch1.censys-scanner.com|7
103.47.184.2|mail.ictdcd.gov.mm|7
190.145.81.37|-|7
61.76.169.138|-|7
14.46.116.243|-|7
130.61.35.0|-|7
43.153.15.117|-|7
182.93.50.90|n18293z50l90.static.ctmip.net|7
205.185.113.140|-|7
43.130.62.221|-|7
171.244.140.174|-|7
192.42.116.23|this-is-a-tor-exit-node-hviv123.hviv.nl|7
192.42.116.20|this-is-a-tor-exit-node-hviv120.hviv.nl|7
192.42.116.25|this-is-a-tor-exit-node-hviv125.hviv.nl|7
151.177.201.230|c151-177-201-230.bredband.tele2.se|7
167.248.133.127|scanner-26.ch1.censys-scanner.com|7
167.248.133.125|scanner-26.ch1.censys-scanner.com|7
167.248.133.123|scanner-26.ch1.censys-scanner.com|7
139.59.127.178|-|7
43.134.189.26|-|7
60.247.92.186|-|7
129.154.238.13|-|7
129.226.198.6|-|7
45.128.96.239|-|7
64.227.122.198|-|7
182.72.219.186|nsg-static-186.219.72.182.airtel.in|7
179.43.159.196|hostedby.privatelayer.com|7
185.220.101.162|tor-exit-162.relayon.org|7
85.209.11.254|-|7
43.130.16.190|-|7
178.128.80.65|-|7
165.154.138.151|-|7
43.134.103.17|-|7
185.142.236.34|hat.census.shodan.io|7
121.4.83.32|-|7
103.248.60.70|-|7
43.156.201.224|-|7
159.89.233.77|-|7
60.220.185.22|22.185.220.60.adsl-pool.sx.cn|7
43.130.49.137|-|7
66.249.155.244|-|7
175.206.47.218|-|7
194.209.191.243|-|7
175.203.118.149|-|7
200.105.183.118|static-200-105-183-118.acelerate.net|7
43.156.174.43|-|7
43.156.26.222|-|7
221.167.63.25|-|7
174.138.72.191|-|7
167.94.145.59|-|7
167.94.145.57|-|7
167.94.145.51|-|7
167.94.145.52|-|7
120.48.9.61|-|7
43.134.108.110|-|7
43.156.35.214|-|7
43.134.63.170|-|7
112.167.233.14|-|7
118.69.80.75|-|7
190.85.15.251|-|7
185.46.18.99|-|7
45.79.172.21|riga.scan.bufferover.run|7
103.246.194.229|ws229-194.246.103.rcil.gov.in|7
