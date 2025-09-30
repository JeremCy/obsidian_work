---
tags:
  - project
  - Testing
Owner: Jeremie Cyrille
Last edited time: 2025-09-29T15:13:00
id: "25"
---

sphere et databricks
formation PL300

priorité: formation datashpère et databricks

formation:
- [datasphere](https://www.sap.com/france/products/data-cloud/datasphere/trial.html)
Account:
- ON premeise sap 4/HANA
GCP-ovh
k2ETPoAmnmA6U7tDtD25
gcp-gmail
eM5gH0yB2OBihZDXzt2M
marketing
5ELIwyS9uw3psFDKMTa4
POC:
- configurer l'instance SAP ABAP 1909
- FIchier de configuration en cour,
- configuere l'instance avec 
- on le fait en on premise
code 60 day trial 
- CB8609EF0ABE599A
- aNe@MxqwnM@E7c2QCSEE
- tISFTXnaWA0NNtDWH5E8

````bash
sudo docker run -p 49013:49013 -p 49015:49015 -p 49041-49045:49041-49045 -p 1138-1139:1128-1129 -p 59023-59024:59013-59014 -p 49030-49033:49030-49033 -p 51000-51060:51000-51060 -p 53075:53075 -h hxehost -v /data/hxe:/hana/mounts --ulimit nofile=1048576:1048576 --sysctl kernel.shmmax=1073741824 --sysctl net.ipv4.ip_local_port_range='60000 65535' --sysctl kernel.shmmni=524288 --sysctl kernel.shmall=8388608 --name saptest --agree-to-sap-license --passwords-url /data/user.json --proxy-host proxy.wdf.sap.corp --proxy-port 8080 --no-proxy localhost,127.0.0.1,hxehost,hxehost.localdomain
````
`
```bash
sudo docker run -p 39013:39013 -p 39017:39017 -p 39041-39045:39041-39045 -p 1128-1129:1128-1129 -p 59013-59014:59013-59014 -v /data/<directory_name>:/hana/mounts \
--ulimit nofile=1048576:1048576 \
--sysctl kernel.shmmax=1073741824 \
--sysctl net.ipv4.ip_local_port_range='40000 60999' \
--sysctl kernel.shmmni=524288 \
--sysctl kernel.shmall=8388608 \
--name testsap \
store/saplabs/hanaexpress:<tag> \
--passwords-url file://data/user.json \
--agree-to-sap-license
```
`